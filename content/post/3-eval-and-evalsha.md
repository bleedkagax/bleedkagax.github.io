---
title: Eval and Evalsha
name: 3-eval-and-evalsha
date: 2024-10-02
draft: false
tags:
  - Redis
share: "true"
---
# Overview

`EVAL` and `EVALSHA` are Redis commands used to execute Lua scripts within the Redis server.  They differ primarily in how they handle script loading and execution:

* **`EVAL`:** This command takes the Lua script as an argument.  Redis parses and hashes the script every time `EVAL` is called.  This adds overhead, especially for frequently executed scripts.

* **`EVALSHA`:** This command takes the SHA1 hash of the Lua script as an argument.  Redis retrieves the script from its internal cache using this hash.  If the script is found, it's executed directly, bypassing the parsing and hashing steps.  This results in significantly faster execution times for frequently used scripts.

# Key Differences Summarized

| Feature          | `EVAL`                               | `EVALSHA`                             |
|-----------------|---------------------------------------|----------------------------------------|
| Script Input     | Lua script as a string                | SHA1 hash of the Lua script           |
| Script Parsing   | Parses and hashes the script each time | Retrieves from cache; no parsing      |
| Performance      | Slower, especially for frequent use   | Faster for frequently used scripts     |
| Script Cache     | No reliance on script cache           | Relies on script cache; error if miss |
| Error Handling   | No specific error for cache miss       | Returns error if script not in cache   |

# When to Use Which

* **`EVAL`:** Use for testing, debugging, or scripts that are executed infrequently.  It's simpler to use since you don't need to manage script hashes.

* **`EVALSHA`:** Use for frequently executed scripts to optimize performance.  This requires a prior step to load the script using `SCRIPT LOAD` to obtain its SHA1 hash.

# Example

Let's say you have a Lua script to increment a counter:

```lua
redis.call('INCR', KEYS[1])
```

1. **Using `EVAL`:**

```redis-cli
EVAL "redis.call('INCR', KEYS[1])" 1 mykey
```

2. **Using `EVALSHA`:**

a. **Load the script and get the SHA1 hash:**

```redis-cli
SCRIPT LOAD "redis.call('INCR', KEYS[1])"
```

Redis computes the script's SHA1 hash and stores both the script and its hash in an internal cache.

This returns the SHA1 hash (e.g., `a1b2c3d4e5f6...`).

b. **Execute using the hash:**

```redis-cli
EVALSHA a1b2c3d4e5f6... 1 mykey
```

Remember to replace `a1b2c3d4e5f6...` with the actual SHA1 hash.  `EVALSHA` will be significantly faster if this script is executed repeatedly.  However, if the script is not in the cache, `EVALSHA` will fail.  Therefore, robust error handling is crucial in production environments.  A common strategy is to use `EVALSHA` first and fall back to `EVAL` if it fails.
