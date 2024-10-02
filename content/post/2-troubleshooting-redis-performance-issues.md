---
title: Troubleshooting Redis Performance Issues
name: 2-troubleshooting-redis-performance-issues
date: 2024-09-07
draft: false
tags:
  - Redis
share: "true"
---

# A comprehensive guide to troubleshooting Redis performance issues

## 1. Introduction

Redis is renowned for its high performance, capable of handling 100,000 operations per second. However, users may encounter unexpected latency issues in various scenarios:

- Same commands sometimes fast, sometimes slow
- Simple operations like SET and DEL taking unexpectedly long
- Temporary slowdowns that resolve themselves
- Sudden performance degradation after long periods of stability

This comprehensive guide (approximately 20,000 words) aims to provide a thorough troubleshooting approach for Redis performance issues.

## 2. Confirming Redis Slowdown

### a) Isolate the problem

- Implement distributed tracing in your application
- Record response times for external dependencies, including Redis
- Identify if the Redis operation is the bottleneck

### b) Eliminate network issues

- Check if all services on the same server experience similar delays
- If so, involve network operations team
- If not, focus on Redis-specific issues

### c) Establish baseline performance

Conduct benchmark tests on production servers using redis-cli commands directly on the Redis server:

1. Measure maximum latency:
   ```
   redis-cli -h 127.0.0.1 -p 6379 --intrinsic-latency 60
   ```
   Example output: max latency of 72 microseconds

2. Monitor latency history:
   ```
   redis-cli -h 127.0.0.1 -p 6379 --latency-history -i 1
   ```
   Example output: average latencies between 0.08 and 0.13 milliseconds

### d) Compare suspected slow instances

- Test a known good Redis instance for baseline
- Test the suspected slow instance
- If latency is 2x or more than baseline, consider it definitively slow

## 3. Investigating Slowdown Causes

### a) Using high complexity commands

#### Check Redis slow log

Set slowlog parameters:
```
CONFIG SET slowlog-log-slower-than 5000
CONFIG SET slowlog-max-len 500
```

View slow log:
```
SLOWLOG get 5
```

#### Look for:
- O(N) or higher complexity commands (e.g., SORT, SUNION, ZUNIONSTORE)
- O(N) commands with large N values
- Commands returning large amounts of data

#### Impact:
- High CPU usage for complex operations
- Network transfer time for large data sets
- Blocking of subsequent commands due to Redis' single-threaded nature

#### Solutions:
- Avoid high complexity commands, move aggregation to client side
- Limit the amount of data returned (N <= 300 recommended)
- Use SCAN instead of KEYS for iterating over large key sets
- Monitor CPU usage - high CPU with low OPS suggests complex commands

#### Additional tips:
- Use pipelining to reduce network round trips
- Consider using Lua scripts for complex operations

### b) Operating on big keys

#### Reasons for slowdown:
- Time-consuming memory allocation for large values
- Slow memory deallocation when deleting large keys

#### Detecting big keys:
```
redis-cli -h 127.0.0.1 -p 6379 --bigkeys -i 0.01
```
- Scans entire keyspace, reports largest keys by type
- Shows distribution of key sizes and types

#### Cautions when scanning:
- Can cause OPS spikes on production systems
- May block other operations on busy systems

#### Solutions:
- Avoid storing big keys in applications
- Use UNLINK instead of DEL for large keys (Redis 4.0+)
- Enable lazy-free mechanism for DEL (Redis 6.0+)
- Set lazyfree-lazy-eviction, lazyfree-lazy-expire, lazyfree-lazy-server-del to yes

#### Best practices:
- Split large values into smaller chunks
- Use Hash data structures for large objects instead of single String keys

### c) Keys expiring at the same time

#### Symptoms:
- Latency spikes at regular intervals

#### Redis expiration strategies:
- Passive: Check expiration on access
- Active: Periodic scan of expired keys

#### Problems:
- Active expiration runs in main thread, blocking other operations
- Many keys expiring simultaneously cause latency spikes

#### Detection:
- Monitor expired_keys metric in INFO stats
- Use Redis 4.0+ MEMORY STATS for more detailed expiration info

#### Solutions:
- Add random jitter to expiration times (e.g., expire_at = now + TTL + random(0, 300))
- Enable lazy-free for expired key deletion (Redis 4.0+)
- Adjust active expiry algorithms (hz and active-expire-effort parameters)

#### Additional considerations:
- Balance between memory usage and CPU usage when tuning expiration
- Consider using SCAN to manually expire keys in batches for extreme cases

### d) Memory fragmentation

#### Check fragmentation ratio:
```
INFO memory
```
Look for `mem_fragmentation_ratio`

#### Causes:
- Frequent creation/deletion of keys of varying sizes
- OS memory allocation strategies

#### Impact:
- High fragmentation ratio (>1.5) indicates inefficient memory use
- Very low ratio (<1) suggests Redis needs more memory

#### Solutions:
- Enable activedefrag (Redis 4.0+):
  ```
  CONFIG SET activedefrag yes
  ```
- Configure `active-defrag-*` parameters:
  ```
  CONFIG SET active-defrag-ignore-bytes 100mb
  CONFIG SET active-defrag-threshold-lower 10
  CONFIG SET active-defrag-threshold-upper 100
  CONFIG SET active-defrag-cycle-min 25
  CONFIG SET active-defrag-cycle-max 75
  ```
- Restart Redis instance to defragment memory (last resort)

#### Best practices:
- Use consistent key sizes when possible
- Monitor fragmentation ratio over time
- Consider using jemalloc memory allocator

### e) AOF persistence impacting performance

#### Problem:
- fsync() on every write blocks the main thread

#### Detection:
Check `INFO persistence` for aof_* metrics

#### Solutions:
- Consider relaxing durability guarantees 
- Use "everysec" fsync policy as a compromise
- Configure `no-appendfsync-on-rewrite` for better performance during rewrites

#### AOF policies:
- always: Most durable, worst performance
- everysec: Good durability, acceptable performance
- no: Best performance, risk of data loss

#### Additional considerations:
- Use AOF rewrite to keep AOF file size manageable
- Monitor AOF rewrite progress and impact

### f) Replication issues

#### Problems:
- Large replication buffers on master can cause OOM
- Slow replicas can cause master buffers to grow

#### Monitoring:
- Check `INFO replication` for master_repl_offset and slave_repl_offset
- Monitor repl_backlog_size

#### Solutions:
- Increase replication backlog size if needed
- Optimize network between master and replicas
- Consider using diskless replication for faster sync

#### Best practices:
- Use replication timeout (repl-timeout) to detect stuck replicas
- Configure appropriate client-output-buffer-limit for slave clients
- Use Redis Sentinel or Cluster for automatic failover

### g) CPU utilization

#### Monitoring:
- Use `INFO CPU` to check Redis CPU usage
- Monitor system CPU usage

#### Solutions:
- Distribute load across multiple Redis instances
- Use Redis Cluster for better CPU utilization
- Optimize client-side operations to reduce load on Redis

#### Additional tips:
- Profile Redis commands using --latency-debug flag
- Use DEBUG OBJECT to analyze key encoding and other properties

### h) Network issues

- Test latency from Redis server itself to isolate network problems
- Use `redis-cli --latency` to measure network latency
- Check for network congestion or hardware issues

#### Considerations:
- Network interface configuration
- TCP settings (e.g., tcp-backlog)
- Use of proxies or load balancers

### i) Transparent huge pages (THP)

#### Check if enabled:
```
cat /sys/kernel/mm/transparent_hugepage/enabled
```

#### Solution:
Disable THP for Redis servers:
```
echo never > /sys/kernel/mm/transparent_hugepage/enabled
```
Make change permanent in /etc/rc.local or systemd

#### Additional system settings to consider:
- vm.overcommit_memory
- vm.swappiness
- Disable NUMA interleaving

## 4. Additional Considerations

### Impact of data structure choice on performance
- Strings: Fastest, but limited functionality
- Hashes: Efficient for objects, supports partial updates
- Lists: Good for queue-like data structures
- Sets: Efficient for membership checks
- Sorted Sets: Useful for leaderboards and range queries

### Proper configuration of maxmemory and eviction policies
- noeviction, allkeys-lru, volatile-lru, allkeys-random, volatile-random, volatile-ttl

### Importance of connection pooling in clients

### Monitoring and alerting for early detection of issues
- Set up monitoring for key metrics (CPU, memory, network, ops/sec)
- Use INFO command regularly to gather stats
- Consider tools like Redis Exporter for Prometheus

### Regular performance testing and capacity planning

### Consideration of Redis Cluster for scaling and better resource utilization

### Use of Redis modules for specific use cases (e.g., RediSearch, RedisTimeSeries)

## 5. Debugging and Profiling Tools

- redis-cli --stat: Real-time stats
- redis-cli --latency: Network latency testing
- redis-cli --latency-history: Latency over time
- redis-cli --latency-dist: Latency distribution
- redis-cli --bigkeys: Find large keys
- redis-cli --memkeys: Analyze memory usage of keys
- redis-cli --hotkeys: Identify frequently accessed keys
- MONITOR command: Real-time log of Redis commands (use cautiously in production)

## 6. Best Practices

- Regular backups and disaster recovery planning
- Implement proper security measures (password, firewall, SSL/TLS)
- Keep Redis version up-to-date
- Use Redis benchmark tool for performance testing
- Implement proper error handling and retry mechanisms in clients
- Use Redis Pub/Sub with caution, as it can impact performance

## 7. Conclusion

- Redis performance issues can have various causes
- Systematic approach to troubleshooting is crucial
- Understanding Redis internals helps in diagnosing and resolving issues
- Regular monitoring and proactive optimization are key to maintaining high performance
- Emphasizes the importance of ongoing learning and staying updated with Redis features
- Encourage reading Redis documentation and following the official blog for updates
