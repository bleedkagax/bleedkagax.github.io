---
title: Network Interview
name: 0_network_interview
date: 2024-10-04
draft: false
tags:
  - Network
share: "true"
---

## What is the OSI model?

![](/img/0_network_interview.png)

1. Physical Layer
2. Data Link Layer
3. Network Layer 
4. Transport Layer 
5. Session Layer
6. Presentation Layer
7. Application Layer

## Explain the difference between TCP and UDP.

- TCP (Transmission Control Protocol):
  - Connection-oriented
  - Reliable, ensures all data is received
  - Flow control and congestion control
  - Slower than UDP
  - Used for applications requiring high reliability (e.g., file transfer, email)

- UDP (User Datagram Protocol):
  - Connectionless
  - Unreliable, doesn't guarantee data delivery
  - No flow control or congestion control
  - Faster than TCP
  - Used for applications that prioritize speed (e.g., video streaming, online gaming)

## What is DNS and how does it work?

DNS (Domain Name System) is a hierarchical and decentralized naming system for computers, services, or other resources connected to the Internet or a private network. It translates human-readable domain names (e.g., www.example.com) into IP addresses.

Process:
1. User enters a URL in the browser
2. Browser checks its cache for DNS record
3. If not found, it queries the OS
4. If still not found, it contacts a DNS resolver
5. The resolver queries root servers, then TLD servers, then authoritative name servers
6. The IP address is returned to the browser

![](/img/0_network_interview-1.png)

## What is a subnet and subnet mask?

A subnet is a logical subdivision of an IP network. A subnet mask is a 32-bit number that masks an IP address, and divides the IP address into network address and host address.

Subnetting allows for more efficient use of IP addresses and improved network performance.

![](/img/0_network_interview-2.png)

## Explain the concept of ARP (Address Resolution Protocol).

ARP is a protocol used to map an IP address to a physical machine address (MAC address) in a local network. 

Process:
1. Device wants to send a packet to an IP address
2. It checks its ARP cache for the corresponding MAC address
3. If not found, it broadcasts an ARP request
4. The device with the matching IP address responds with its MAC address
5. The sender updates its ARP cache and sends the packet

##  What is the difference between a hub, switch, and router?

- Hub: Layer 1 device, broadcasts data to all ports
- Switch: Layer 2 device, forwards data to specific port based on MAC address
- Router: Layer 3 device, forwards data between different networks based on IP address

## Explain the three-way handshake in TCP.

The three-way handshake is used to establish a TCP connection:

1. SYN: Client sends a SYN packet to the server
2. SYN-ACK: Server responds with a SYN-ACK packet
3. ACK: Client sends an ACK packet to the server

![](/img/0_network_interview-3.png)

## What is DHCP and what is it used for?

DHCP (Dynamic Host Configuration Protocol) is a network management protocol used to dynamically assign an IP address to any device, or node, on a network so it can communicate using IP.

DHCP automates and centrally manages these configurations rather than requiring network administrators to manually assign IP addresses to all network devices.

![](/img/0_network_interview-4.png)

1. **DHCP Discover:** The client broadcasts a request for an IP address.
2. **DHCP Offer:** The DHCP server responds with an IP address offer.
3. **DHCP Request:** The client requests the offered IP address.
4. **DHCP Acknowledge:** The server confirms the IP address assignment.

## Explain the difference between IPv4 and IPv6.

| Feature        | IPv4                          | IPv6                                      |
| -------------- | ----------------------------- | ----------------------------------------- |
| Address Length | 32-bit                        | 128-bit                                   |
| Address Space  | ~4.3 billion unique addresses | 340 undecillion (3.4 × 10^38) addresses   |
| Notation       | Dot-decimal                   | Hexadecimal with colons                   |
| Example        | `192.168.1.1`                 | `2001:0db8:85a3:0000:0000:8a2e:0370:7334` |

## What is NAT and why is it used?

NAT (Network Address Translation) is a method of remapping one IP address space into another by modifying network address information in the IP header of packets while they are in transit across a traffic routing device.

NAT is primarily used to:
- Conserve IPv4 addresses
- Improve security by hiding internal network addresses

## Can multiple UDP sockets bind to the same IP and port?

- **Yes**, with conditions:
  - Most operating systems allow multiple UDP sockets to bind to the same IP and port.
  - This is often referred to as "socket reuse" or "address reuse".
  - Requires setting the `SO_REUSEADDR` socket option before binding.

## Can multiple TCP sockets bind to the same IP and port?

- **Generally No**, with exceptions:
  - Typically, only one TCP socket can bind to a specific IP and port combination.
  - Exceptions:
    - Different IP addresses on the same port.
    - Same IP, different ports.
    - Using `SO_REUSEADDR` for sequential (not simultaneous) bindings.

## Can TCP and UDP bind to the same port?

- **Yes**:
  - TCP and UDP use separate protocol stacks.
  - A TCP socket and a UDP socket can bind to the same port number simultaneously.
  - The operating system distinguishes between them based on the protocol.

## How TCP Ensures Reliable Transmission

1. **Sequence Numbers and Acknowledgments**
   - Each byte of data is assigned a sequence number
   - Receiver acknowledges receipt of data by sending ACKs

2. **Retransmission**
   - Sender retransmits data if ACK is not received within a timeout period
   - Implements various retransmission strategies (e.g., fast retransmit)

3. **Checksums**
   - Used to detect corrupted data
   - Receiver discards corrupt segments and doesn't acknowledge them

4. **Flow Control**
   - Sliding window protocol
   - Prevents sender from overwhelming receiver

5. **Congestion Control**
   - Slow start
   - Congestion avoidance
   - Fast recovery

6. **Connection Management**
   - Three-way handshake for connection establishment
   - Four-way handshake for connection termination

7. **Ordered Data Transfer**
   - Segments are reassembled in correct order at the receiver

8. **Duplicate Data Detection**
   - Receiver identifies and discards duplicate segments

## What is the TCP four-way handshake for connection termination?

1. FIN from initiator: Either the client or server can initiate the termination by sending a FIN (finish) packet.
2. ACK from receiver: The receiving end acknowledges the FIN with an ACK packet.
3. FIN from receiver: The receiving end then sends its own FIN packet to indicate it's ready to close.
4. ACK from initiator: The initiating end acknowledges this FIN with a final ACK.

## TCP TIME-WAIT

After a connection is closed, the closing party enters a TIME-WAIT state. This state typically lasts for 2 * Maximum Segment Lifetime (MSL), usually around 2-4 minutes. The TIME-WAIT state serves two main purposes:

- Ensures that any delayed packets from the closed connection are handled properly and don't interfere with new connections.
- Allows for proper closure of both sides of the connection, preventing potential issues with subsequent connections.

##  How to implement a basic TCP-like protocol using UDP？

1. Connection Establishment
Implement a three-way handshake similar to TCP

2. Sequence Numbers
Assign sequence numbers to each packet
Use these to detect packet loss and ensure correct ordering

3. Acknowledgments
Receiver sends acknowledgments for received packets
Sender retransmits packets that aren't acknowledged within a timeout period

4. Flow Control
Implement a simple sliding window protocol
Receiver advertises available buffer space

5. Error Detection
Use checksums or CRC to detect corrupted packets
Discard or request retransmission of corrupted packets

6. Connection Termination
Implement a four-way handshake for connection termination

## Http Keep-Alive

In this example, the idle timeout is set to ten seconds and it can accept up to 100 HTTP requests before the HTTP Connection is forcibly closed.

_Response_
```
HTTP/1.1 200 OK
Connection: keep-alive
Content-Type: text/html; chartset=utf-8
Keep-Alive: timeout=10, max=100
```

## Session ID and Session Key

| Aspect             | **Session ID**                               | **Session Key**                               |
|--------------------|----------------------------------------------|----------------------------------------------|
| **Purpose**         | Uniquely identifies a session between client and server. | Secures communication or encrypts session data. |
| **Type**            | A random string or token.                    | A cryptographic key.                         |
| **Use Case**        | Used to look up session data on the server.  | Used to encrypt/decrypt data during a session. |
| **Storage**         | Stored in cookies (client) and server memory. | Stored in memory (for encryption) or negotiated during SSL/TLS. |
| **Sensitive Info**  | Does not contain sensitive info (just an ID). | Contains sensitive info (used for encryption). |
| **Security Role**   | Identifies the user's session, but doesn't secure data directly. | Ensures data confidentiality and integrity. |

## Tp99 Tp95 Tp90

 It represents the value below which 95% of the observations in a dataset fall. 

1. **Sort the Data**: Arrange all data points in ascending order.

2. **Calculate the Index**: Use the formula: `index = (n * 0.95) + 0.5`, where `n` is the number of data points.
   - If the result is not a whole number, round up to the nearest integer.

3. **Find the Value**: The TP95 is the value at the calculated index position in the sorted dataset.

## Tcp Alive 
fuck byte
短视频去重
bloom过滤器 原理 ，redis 中怎么支持
rocksDB 如何保证快速读写
简历一致性哈希