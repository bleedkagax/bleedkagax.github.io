---
title: Subnet and Subnet
name: 2_subnet
date: 2024-10-04
draft: false
tags:
  - Network
share: "true"
---

## What is a Subnet?

A **subnet** is a way to divide a large network into smaller, more manageable pieces. Think of it like dividing a big city into neighborhoods. Each subnet (neighborhood) has its own group of devices (houses), but all are still part of the same overall network (city).

## What is a Subnet Mask?

A **subnet mask** is a number used to help identify which part of an IP address belongs to the **network** (city) and which part identifies the **device** (house). It’s like a divider that separates the network part from the device part in an IP address.

### Simple Example: IP Address and Subnet Mask

Let’s say you have the following IP address and subnet mask:

- **IP Address**: `192.168.1.10`
- **Subnet Mask**: `255.255.255.0`

This IP address and subnet mask help identify:

- What **network** this device is in (like which city it belongs to).
- What **device** it is within that network (like which house in the city).

### Visual Breakdown of IP Address and Subnet Mask

Let’s break down the IP address and subnet mask using a visual approach:

#### Step 1: Convert IP Address to Binary

An IP address is made up of **four numbers** (each between 0 and 255). In binary, the IP address `192.168.1.10` becomes:

```
192      . 168      . 1        . 10
11000000 . 10101000 . 00000001 . 00001010
```

#### Step 2: Convert Subnet Mask to Binary

The subnet mask `255.255.255.0` also has four numbers. In binary, it looks like this:

```
255      . 255      . 255      . 0
11111111 . 11111111 . 11111111 . 00000000
```

#### Step 3: Identify Network and Host Parts

A subnet mask is used to divide the IP address into two parts:

- **Network part**: The part of the IP address that identifies the network (like identifying which city).
- **Host part**: The part that identifies the specific device within that network (like identifying the specific house).

In the subnet mask `255.255.255.0`, the **1s** represent the network part, and the **0s** represent the host part. So, for the IP address `192.168.1.10`:

- **Network Part**: `192.168.1` (because the first three sections are covered by the `1s` in the subnet mask).
- **Host Part**: `10` (the last section is covered by the `0s` in the subnet mask).

### Diagram: How Subnet Mask Divides IP Address

Here’s a simple visual showing how the subnet mask divides the IP address:

```
IP Address:    192.168.1.10
Subnet Mask:   255.255.255.0

Binary IP:     11000000.10101000.00000001.00001010
Binary Mask:   11111111.11111111.11111111.00000000

Network Part:  11000000.10101000.00000001 (192.168.1)
Host Part:                         00001010 (10)
```

- The **first 24 bits** (the `1s` in the subnet mask) represent the **network**.
- The **last 8 bits** (the `0s`) represent the **host**.

### Visualizing a Network with Subnets

Let’s say you have a large network (`192.168.1.0/24`), which consists of all the IP addresses from `192.168.1.0` to `192.168.1.255`. You can divide this large network into smaller subnets.

The notation /24 is part of something called CIDR notation, which stands for Classless Inter-Domain Routing. CIDR notation is a shorthand way to represent the subnet mask.

The number after the / (in this case, 24) tells us how many bits are used for the network portion of the IP address. 

For example, if you use a subnet mask like `255.255.255.192`, it will break the network into smaller subnets, each with fewer devices.

#### Example: Dividing the Network

```
Main Network: 192.168.1.0/24

Subnet 1: 192.168.1.0/26
Subnet 2: 192.168.1.64/26
Subnet 3: 192.168.1.128/26
Subnet 4: 192.168.1.192/26
```

Each subnet has its own range of IP addresses and can have its own devices. This way, you can better manage the network traffic and security.

## Key Points

- **Subnet**: Think of it as a smaller group within a large network.
- **Subnet Mask**: A tool that divides the IP address into a **network part** and a **host part**.
- **Network Part**: The part of the IP address that identifies which network the device belongs to.
- **Host Part**: The part of the IP address that identifies the specific device in the network.
