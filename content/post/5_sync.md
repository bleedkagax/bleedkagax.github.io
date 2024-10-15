---
title: Go's Sync
name: 5_sync
date: 2024-09-07
draft: false
tags:
  - Golang
share: "true"
---


## `sync.Mutex`

```go
// Mutex provides mutual exclusion for shared resources.
type Mutex struct {
    state int32   // State of the mutex (locked/unlocked)
    sema  uint32  // Semaphore for blocking goroutines
}

// Lock acquires the mutex, blocking if necessary.
func (m *Mutex) Lock() {
    // Check if already locked; if so, block until unlocked.
}

// Unlock releases the mutex.
func (m *Mutex) Unlock() {
    // Update state and unblock waiting goroutines if any.
}
```

**Mechanism**: Uses atomic operations to manage state and semaphore to block goroutines.

## `sync.RWMutex`

```go
// RWMutex allows multiple readers or one writer.
type RWMutex struct {
    w       Mutex   // Mutex for exclusive access by writers
    readers int32   // Count of active readers
    readerSem uint32 // Semaphore for managing reader access
    writerSem uint32 // Semaphore for managing writer access
}

// RLock acquires a read lock, allowing multiple concurrent readers.
func (rw *RWMutex) RLock() {
    // Increment reader count; block if a writer is active.
}

// RUnlock releases a read lock.
func (rw *RWMutex) RUnlock() {
    // Decrement reader count and unblock if necessary.
}

// Lock acquires an exclusive write lock.
func (rw *RWMutex) Lock() {
    // Block all readers and wait for exclusive access.
}

// Unlock releases the write lock.
func (rw *RWMutex) Unlock() {
    // Release exclusive access and notify waiting readers/writers.
}
```

**Mechanism**: Combines a mutex with counters and semaphores to manage read/write access efficiently.

##  `sync.WaitGroup`

```go
// WaitGroup waits for a collection of goroutines to finish executing.
type WaitGroup struct {
    noCopy noCopy     // Prevent copying of WaitGroup
    state1 [1]uint32  // Atomic state tracking active goroutines
    done   uint32     // Count of completed goroutines
    sema   uint32     // Semaphore for blocking
}

// Add increments the WaitGroup counter by n.
func (wg *WaitGroup) Add(n int) {
    // Increment counter; block if necessary based on done count.
}

// Done decrements the WaitGroup counter by one.
func (wg *WaitGroup) Done() {
    // Increment done count; signal if all goroutines are done.
}

// Wait blocks until the WaitGroup counter is zero.
func (wg *WaitGroup) Wait() {
    // Block until all added goroutines call Done().
}
```

**Mechanism**: Utilizes atomic operations and a semaphore to manage synchronization among multiple goroutines.

##  `sync.Once`

```go
// Once ensures that a function is executed only once.
type Once struct {
    m    Mutex   // Mutex for synchronization
    done uint32  // Flag indicating if function has been called
}

// Do executes the function f only once.
func (o *Once) Do(f func()) {
    o.m.Lock()          // Lock to ensure exclusive access
    if o.done == 0 {   // Check if function has been executed
        f()            // Call the function
        o.done = 1    // Mark as executed
    }
    o.m.Unlock()       // Unlock after execution
}
```

**Mechanism**: Uses a mutex to ensure that the wrapped function is executed only once, regardless of how many times `Do()` is called.

## `sync.Cond`

```go
// Cond provides a way for goroutines to wait for conditions to be met.
type Cond struct {
    noCopy noCopy      // Prevent copying of Cond
    L      *Mutex      // Locker that must be held when calling Wait or Signal
    notify notifyList  // List of waiting goroutines
}

// Wait atomically releases the mutex and waits for notification.
func (c *Cond) Wait() {
    c.L.Unlock()       // Unlock before waiting to avoid deadlock
    // Block until notified by Signal or Broadcast.
}

// Signal wakes one waiting goroutine, if any.
func (c *Cond) Signal() {
    // Notify one waiting goroutine to wake up.
}

// Broadcast wakes all waiting goroutines, if any.
func (c *Cond) Broadcast() {
    // Notify all waiting goroutines to wake up.
}
```

**Mechanism**: Uses an associated mutex to manage access and a notification system to wake up blocked goroutines based on conditions.

## `sync.Map`

### Structure

```go
type Map struct {
   mu     Mutex
   read   atomic.Value // readOnly
   dirty  map[interface{}]*entry
   misses int
}

type readOnly struct {
   m       map[interface{}]*entry
   amended bool
}

type entry struct {
   p unsafe.Pointer // *interface{}
}
```

- **`mu`**: A mutex used to protect access to **`read`** and **`dirty`**.
- **`read`**: A read-only data structure supporting concurrent reads using atomic operations. It stores a **`readOnly`** structure, which is a native map. The **`amended`** attribute marks whether the **`read`** and **`dirty`** data are consistent.
- **`dirty`**: A native map for reading and writing data, requiring locking to ensure data security.
- **`misses`**: A counter tracking how many times the read operation fails.
- **`entry`**: It contains a pointer **`p`** that points to the value stored for the element (key).

### Load

1. Check `read` map first (lock-free)
2. If not found and `amended` is true, lock and check `dirty` map
3. Increment `misses` counter if needed

### Store

1. Try to update existing entry in `read` map (lock-free)
2. If not possible, lock and update `dirty` map
3. If `amended` is false, copy `read` to `dirty` before updating

### Delete

1. Try to mark entry as deleted in `read` map (lock-free)
2. If not possible, lock and delete from `dirty` map

### LoadOrStore

Combines `Load` and `Store` operations efficiently

