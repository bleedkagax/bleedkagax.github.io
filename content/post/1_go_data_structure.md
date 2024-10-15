---
title: Go's Common Data Structures
name: 1_go_data_structure
date: 2024-10-11
draft: false
tags:
  - Golang
share: "true"
---

## 1. Strings

Strings in Go are immutable sequences of bytes, typically used to represent UTF-8 encoded text.

### Structure
```go
type stringStruct struct {
    str unsafe.Pointer
    len int
}
```

### Memory Layout
```
stringStruct
+----------------+
| str (uintptr)  | ---> [byte array]
| len (int)      |
+----------------+
```

### Detailed Implementation

#### Creation
1. When a string literal is used, the compiler allocates the bytes in read-only memory.
2. Runtime string creation (e.g., string concatenation) allocates new memory and copies bytes.

#### Operations
- **Substring**: Creates a new `stringStruct` pointing to the same byte array, with adjusted `str` and `len`.
- **Concatenation**: Allocates a new byte array and copies contents from both strings.
- **Comparison**: Compares bytes lexicographically.

### Runtime Behavior
- **Immutability**: String contents cannot be changed after creation. This allows for safe concurrent access and efficient substring operations.
- **UTF-8**: Go source code is UTF-8, and string literals are interpreted as UTF-8. However, a string can contain arbitrary bytes.
- **Conversion**: Converting between strings and byte slices involves copying data.

## 2. Slices

Slices provide a flexible, dynamic array-like interface.

### Structure
```go
type slice struct {
    array unsafe.Pointer
    len   int
    cap   int
}
```

### Memory Layout
```
slice
+-------------------+
| array (uintptr)   | ---> [underlying array]
| len   (int)       |
| cap   (int)       |
+-------------------+
```

### Detailed Implementation

#### Creation
1. **make**: Allocates a new array and sets up the slice structure.
2. **Literal**: Compiler creates an array and sets up the slice structure.
3. **Slicing existing array/slice**: Creates a new slice header pointing to the same array.

#### Growth Algorithm
When appending to a slice that exceeds its capacity:
1. If capacity < 1024, double the capacity.
2. If capacity ≥ 1024, grow by 25%.
3. Round up to the next size class (for better memory allocation).

#### Append Operation
1. Check if there's enough capacity.
2. If not, grow the slice (allocate new array, copy data).
3. Copy new elements to the end of the slice.
4. Update len (and possibly cap and array pointer).

### Runtime Behavior
- **Bounds Checking**: Go performs runtime bounds checking for all slice accesses.
- **Copy**: Uses optimized memory copy functions (potentially using SIMD instructions).
- **GC Interaction**: The garbage collector considers the entire capacity of a slice, not just its length.

## 3. Maps

Maps in Go are implemented as hash tables with separate chaining for collision resolution.

### Structure
```go
type hmap struct {
    count     int
    flags     uint8
    B         uint8
    noverflow uint16
    hash0     uint32
    buckets   unsafe.Pointer
    oldbuckets unsafe.Pointer
    nevacuate  uintptr
    extra *mapextra
}

type bmap struct {
    tophash [8]uint8
    // followed by keys
    // followed by values
    // followed by an overflow pointer
}
```

### Memory Layout
```
hmap
+-------------------+
| count             |
| flags             |
| B                 |
| noverflow         |
| hash0             |
| buckets    -------|---> [array of 2^B pointers to bmap]
| oldbuckets        |
| nevacuate         |
| extra             |
+-------------------+

bmap (bucket)
+------------------+
| tophash [8]uint8 |
+------------------+
| keys   [8]KeyType|
+------------------+
| values [8]ValType|
+------------------+
| overflow *bmap   |
+------------------+
```

### Detailed Implementation

#### Hashing
1. Each key type has a specific hash function.
2. The hash is seeded with `hash0` to prevent collision attacks.
3. Lower `B` bits of the hash are used to select the bucket.
4. Upper 8 bits are stored in `tophash` for quick comparisons.

#### Lookup
1. Compute the hash of the key.
2. Use lower bits to find the bucket.
3. Search the bucket (and overflow buckets) for matching `tophash` and key.

#### Insertion
1. Find the appropriate bucket.
2. If the bucket is full, allocate an overflow bucket.
3. Insert the key-value pair and update `count`.

#### Deletion
1. Find the key-value pair.
2. Zero out the `tophash`, key, and value.
3. Update `count` during the next map growth.

#### Growth
1. Triggered when load factor > 6.5 or too many overflow buckets.
2. Allocate a new bucket array with 2^(B+1) buckets.
3. Gradually move items from old buckets to new ones during subsequent operations.

### Runtime Behavior
- **Concurrency**: Maps are not safe for concurrent read/write access.
- **Iteration**: Map iteration order is randomized.
- **Load Factor**: Maintained around 6.5 items per bucket for performance.

## 4. Channels

Channels provide a way for goroutines to communicate and synchronize.

### Structure
```go
type hchan struct {
    qcount   uint
    dataqsiz uint
    buf      unsafe.Pointer
    elemsize uint16
    closed   uint32
    elemtype *_type
    sendx    uint
    recvx    uint
    recvq    waitq
    sendq    waitq
    lock     mutex
}
```

### Memory Layout
```
hchan
+-------------------+
| qcount            |
| dataqsiz          |
| buf         ------|---> [circular buffer]
| elemsize          |
| closed            |
| elemtype          |
| sendx             |
| recvx             |
| recvq       ------|---> [waiting receivers]
| sendq       ------|---> [waiting senders]
| lock              |
+-------------------+
```

### Detailed Implementation

#### Creation
1. Allocate `hchan` struct.
2. For buffered channels, allocate buffer.

#### Send Operation
1. Lock the channel.
2. If channel is closed, panic.
3. If receiver is waiting, transfer data directly.
4. Else if buffer not full, copy data to buffer.
5. Else park the goroutine in `sendq`.
6. Unlock the channel.

#### Receive Operation
1. Lock the channel.
2. If channel is empty and closed, return zero value.
3. If sender is waiting, receive directly or from buffer.
4. Else if data in buffer, receive from buffer.
5. Else park the goroutine in `recvq`.
6. Unlock the channel.

#### Close Operation
1. Lock the channel.
2. Set `closed` to 1.
3. Release all waiting goroutines.
4. Unlock the channel.

### Runtime Behavior
- **Blocking**: Channel operations may cause goroutine scheduling.
- **Fairness**: Generally FIFO, but not guaranteed.
- **Select**: Uses special cases for efficiency (e.g., 2-case select).

## 5. Interfaces

Interfaces in Go provide a way to specify behavior of types.

### Structure
```go
type iface struct {
    tab  *itab
    data unsafe.Pointer
}

type itab struct {
    inter *interfacetype
    _type *_type
    hash  uint32
    _     [4]byte
    fun   [1]uintptr
}
```

### Memory Layout
```
iface
+----------------+
| tab  *itab     | ---> itab
| data unsafe.Ptr| ---> concrete data
+----------------+

itab
+------------------+
| inter            |
| _type            |
| hash             |
| _                |
| fun [1]uintptr   | ---> [method table]
+------------------+
```

### Detailed Implementation

#### Interface Assignment
1. Check if type implements interface.
2. Create or retrieve `itab`.
3. Set up `iface` with `itab` and pointer to data.

#### Method Call
1. Access function pointer from `itab.fun`.
2. Call function with `data` as receiver.

#### Type Assertions
1. Check `_type` in `itab`.
2. If match, return `data`; else panic or return false.

### Runtime Behavior
- **Dynamic Dispatch**: Method calls use indirect function calls.
- **Type Switch**: Optimized for common cases.
- **Empty Interface**: Special fast-path for `interface{}`.
