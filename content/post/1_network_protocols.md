---
title: Network Protocols
name: 1_network_protocols
date: 2024-10-04
draft: false
tags:
  - Network
share: "true"
---

![](/img/1_network_protocols.png) 

## Transmission Control Protocol (TCP)

### TCP Principles and Mechanisms

Key features:
1. **Connection Establishment**: Three-way handshake (SYN, SYN-ACK, ACK)
2. **Reliable Delivery**: Acknowledgment and retransmission
3. **Flow Control**: Sliding window mechanism
4. **Congestion Control**: Slow start, congestion avoidance, fast retransmit, and fast recovery
5. **Ordered Data Transfer**: Sequence numbers
6. **Error Detection**: Checksum

Example of TCP header:

```
 0                   1                   2                   3
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|          Source Port          |       Destination Port        |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                        Sequence Number                        |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    Acknowledgment Number                      |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|  Data |           |U|A|P|R|S|F|                               |
| Offset| Reserved  |R|C|S|S|Y|I|            Window             |
|       |           |G|K|H|T|N|N|                               |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|           Checksum            |         Urgent Pointer        |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    Options                    |    Padding    |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                             data                              |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

### TCP Performance Characteristics

1. **Throughput**: 
   - Affected by Round-Trip Time (RTT) and packet loss
   - Theoretical max: Window Size / RTT

2. **Latency**:
   - Connection setup time: 1.5 RTT (three-way handshake)
   - Data transfer: At least 1 RTT per request-response cycle

3. **Reliability**:
   - Guaranteed delivery through acknowledgments and retransmissions
   - Ordered delivery ensures data integrity

4. **Scalability**:
   - Limited by connection state maintenance on servers
   - C10K problem: difficulty in handling 10,000+ concurrent connections

### TCP Use Cases and Limitations

Use Cases:
- Web browsing (HTTP)
- Email (SMTP, IMAP, POP3)
- File transfers (FTP, SFTP)
- Remote administration (SSH)

Limitations:
- Head-of-line blocking in multiplexed scenarios
- Performance degradation in high-latency networks
- Overhead for small, frequent transmissions

## User Datagram Protocol (UDP)

### UDP Core Concepts

Key features:
1. **Connectionless**: No handshake required
2. **Unreliable**: No guarantee of delivery, ordering, or duplicate protection
3. **Lightweight**: Minimal protocol overhead
4. **Stateless**: No connection state tracking

UDP header structure:

```
 0      7 8     15 16    23 24    31
+--------+--------+--------+--------+
|     Source      |   Destination   |
|      Port       |      Port       |
+--------+--------+--------+--------+
|                 |                 |
|     Length      |    Checksum     |
+--------+--------+--------+--------+
|
|          data octets ...
+---------------- ...
```

### UDP Performance Analysis

1. **Throughput**:
   - Higher potential throughput than TCP due to less overhead
   - Not limited by congestion control mechanisms

2. **Latency**:
   - Lower latency than TCP for initial data transfer (no handshake)
   - Consistent latency due to lack of retransmission delays

3. **Packet Loss**:
   - No built-in recovery from packet loss
   - Application must implement its own reliability if needed

4. **Scalability**:
   - Excellent for broadcast and multicast scenarios
   - Efficient for large numbers of small transactions

### UDP Applications and Constraints

Applications:
- Real-time gaming
- Voice over IP (VoIP)
- Streaming media
- DNS lookups

Constraints:
- Lack of built-in reliability mechanisms
- No congestion control (potential for network flooding)
- Limited message size (65,507 bytes maximum)

## Hypertext Transfer Protocol (HTTP)

[http1_http2_http3](computer_science/06_system_design/http1_http2_http3.md)

## WebSocket Protocol

### WebSocket Full-Duplex Communication

WebSocket provides a persistent, full-duplex communication channel over a single TCP connection.

Key features:
1. **Bi-directional**: Both client and server can send messages
2. **Low-latency**: Reduced overhead after initial handshake
3. **Real-time**: Immediate message delivery

### WebSocket Performance Metrics

1. **Connection Overhead**:
   - Initial handshake: Similar to HTTP
   - Subsequent messages: Minimal frame overhead (2-14 bytes)

2. **Latency**:
   - Low latency for real-time updates
   - No need for polling or long-polling

3. **Scalability**:
   - Efficient for large numbers of concurrent connections
   - Challenges with very high connection counts (C10K problem)

4. **Bandwidth Usage**:
   - Reduced compared to polling techniques
   - Efficient for small, frequent updates

### WebSocket Use Cases and Limitations

Use Cases:
- Real-time collaborative applications
- Live sports updates
- Financial trading platforms
- Multiplayer games

Limitations:
- Not supported in older browsers
- Potential for abuse (e.g., bypassing same-origin policy)
- Challenges with load balancing and scaling

## Comparative Analysis

| Feature           | TCP                   | UDP              | HTTP                   | WebSocket            |
|-------------------|----------------------|------------------|------------------------|----------------------|
| Connection        | Connection-oriented   | Connectionless   | Connection-oriented    | Persistent connection|
| Reliability       | Guaranteed delivery   | Best-effort      | Reliable (over TCP)    | Reliable (over TCP)  |
| Ordering          | Ordered delivery      | No ordering      | Ordered (HTTP/2 streams) | Ordered              |
| Speed             | Moderate              | Fast             | Varies (1.1 vs 2 vs 3) | Fast after handshake |
| Overhead          | Moderate              | Low              | High (headers)         | Low after handshake  |
| Use Case          | Most internet apps    | Real-time, UDP   | Web, API               | Real-time, push      |
