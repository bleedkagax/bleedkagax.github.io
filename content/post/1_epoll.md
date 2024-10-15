---
title: Epoll
name: 1_epoll
date: 2024-10-03
draft: false
tags:
  - OperatingSystem
share: "true"
---

# `epoll` (Linux): An Efficient I/O Multiplexing Mechanism

`epoll` operates on an event-driven model, meaning it only notifies the application when an event occurs on a specific file descriptor, unlike `select` and `poll` which poll all descriptors regardless of activity. This drastically reduces overhead, especially when managing numerous connections.

## Key Features and Functionality

The core functionality revolves around three system calls:

1. **`epoll_create(size)`:** Creates an `epoll` instance and returns an `epoll` file descriptor.  While `size` was initially used to hint at the number of file descriptors, modern kernels largely ignore it.

2. **`epoll_ctl(epfd, op, fd, event)`:**  Manages the set of file descriptors monitored by the `epoll` instance (`epfd`).  `op` specifies the operation (ADD, MODIFY, or DELETE), `fd` is the file descriptor to manage, and `event` defines the events of interest (read, write, error, etc.).

3. **`epoll_wait(epfd, events, maxevents, timeout)`:** Waits for events on the registered file descriptors.  It blocks until at least one event occurs or a timeout expires.  `events` is a pre-allocated array where `epoll_wait` populates information about the triggered events. `maxevents` specifies the maximum number of events to return.

## Scalability and Efficiency

`epoll`'s efficiency stems from its use of a kernel-level data structure (often a red-black tree) to manage monitored file descriptors. This allows it to handle a massive number of descriptors with minimal performance degradation, a significant advantage over `select` and `poll`, which suffer from performance bottlenecks as the number of descriptors grows.

## Edge-Triggered vs. Level-Triggered

`epoll` offers two triggering modes:

* **Level-triggered:** `epoll_wait` returns an event as long as the condition (e.g., data available for reading) persists.  If the application doesn't process the event immediately, `epoll_wait` will continue to return it.

* **Edge-triggered:** `epoll_wait` only returns an event when the condition *transitions* from false to true.  This is more efficient but requires careful handling to ensure no events are missed.  The application must process all available data in a single `epoll_wait` cycle.

## Use Cases

`epoll` is extensively used in high-performance network servers and applications requiring efficient management of numerous concurrent connections or I/O operations.  Its scalability and event-driven nature make it a crucial component in many modern network architectures.

