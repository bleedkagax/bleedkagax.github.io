---
title: Golang Pprof
name: golang-pprof
date: 2024-09-07
draft: false
tags:
  - Golang
share: "true"
---

#  Overview of `pprof`

`pprof` is a tool that comes with Go's standard library and is used for collecting and viewing profiling data. It can collect different types of profiles including:

- **CPU Profile**: Measures where the program spends most of its time.
- **Memory Profile**: Measures the amount of memory allocated and retained.
- **Block Profile**: Measures where the program spends time waiting for synchronization primitives.
- **Mutex Profile**: Measures contention on mutexes.

# Setting Up `pprof`

To use `pprof`, you need to import the `net/http/pprof` package and set up HTTP server to serve the profiling data.

## Step 1: Import the `pprof` Package

```go
import (
    "net/http"
    _ "net/http/pprof" // This blank import enables the HTTP endpoints for `pprof`
)
```

## Step 2: Start the HTTP Server

```go
func main() {
    go func() {
        // The ListenAndServe function starts the HTTP server. It never returns.
        // We use `log.Fatal` here to ensure that the program will exit if the server fails to start.
        log.Fatal(http.ListenAndServe("localhost:6060", nil))
    }()
    
    // Your application logic here...
}
```

# Writing Code to Profile

 For demonstration, we'll use a CPU-intensive function.

```go
func expensiveFunction() {
    for i := 0; i < 1000000; i++ {
        // Simulating some CPU intensive computation
    }
}

func main() {
    go func() {
        log.Fatal(http.ListenAndServe("localhost:6060", nil))
    }()
    
    // Call the function multiple times to simulate CPU usage
    for i := 0; i < 10; i++ {
        expensiveFunction()
    }
}
```

# Profiling the Application

After running your program, you can access the `pprof` HTTP endpoints at `http://localhost:6060/debug/pprof/`.

## Profiling CPU Usage

1. **Generate a CPU profile** by visiting `http://localhost:6060/debug/pprof/profile` in your browser.
2. **Capture the profile** by setting the duration for which you want to collect the profile. For example, you can set it to 30 seconds.

## Profiling Memory Usage

1. **Generate a memory profile** by visiting `http://localhost:6060/debug/pprof/heap` in your browser.
2. **Capture the profile** and download the snapshot.

# Analyzing the Profile

Use the `go tool pprof` command to analyze the profile.

## Analyzing CPU Profile

```bash
go tool pprof http://localhost:6060/debug/pprof/profile
```

Use various commands to explore the data:

- `top`: Lists the top functions by self or total CPU time.
- `list <function_name>`: Shows the source code of a specific function.
- `web`: Opens an interactive web visualization of the call graph.

## Analyzing Memory Profile

```bash
go tool pprof http://localhost:6060/debug/pprof/heap
```

## Analyzing concurrency performance

### Step 1: Enable `pprof` HTTP Endpoints

```go
import (
    "net/http"
    _ "net/http/pprof" // This blank import enables the HTTP endpoints for `pprof`
    "log"
)

func startProfiler() {
    // Start the HTTP server on a different goroutine
    go func() {
        log.Println(http.ListenAndServe("localhost:6060", nil))
    }()
}
```

### Step 2: Write Concurrent Code

Create a Go program that uses concurrency features like goroutines and channels.

```go
func worker(id int, done chan bool) {
    for {
        // Do some work...
        log.Printf("Worker %d is processing\n", id)
        done <- true
    }
}

func main() {
    startProfiler()

    numWorkers := 5
    done := make(chan bool, numWorkers)

    for i := 0; i < numWorkers; i++ {
        go worker(i, done)
    }

    for i := 0; i < numWorkers; i++ {
        <-done
    }
}
```

### Step 3: Collect Concurrency Profiles

#### Mutex Profile

1. **Run the Mutex Profiler**: Access `http://localhost:6060/debug/pprof/mutex` to view the mutex profile, which shows contention points for mutexes.

    ```bash
    go tool pprof http://localhost:6060/debug/pprof/mutex
    ```

2. **Analyze Contention**: Look for high `contention` values, which indicate that goroutines are frequently blocked waiting for a mutex.

#### Goroutine Profile

1. **Run the Goroutine Profiler**: Access `http://localhost:6060/debug/pprof/goroutine` to get a report of all current goroutines.

    ```bash
    go tool pprof http://localhost:6060/debug/pprof/goroutine
    ```

2. **Analyze Goroutine Counts**: Check for an unusually high number of goroutines, which might indicate a leak.
   
### Step 4: Use `pprof` to Analyze Data

Use the `top` `list` `web` command

### Step 5: Optimize Concurrency

1. **Reduce Lock Contention**: Redesign your code to reduce the need for locking or use finer-grained locks.
2. **Optimize Channel Usage**: Ensure that channel operations are efficient and that goroutines are not blocked waiting for channel operations unnecessarily.
3. **Limit Goroutine Creation**: Use a pool of worker goroutines or limit the creation of new goroutines.
4. **Avoid Blocking Operations**: Ensure that blocking operations are handled correctly and do not unnecessarily block other goroutines.

# Conclusion

`pprof` is a powerful tool for understanding and optimizing the performance of your Go applications.

# Additional Resources

- [Go `pprof` documentation](https://pkg.go.dev/net/http/pprof)
- [Go `pprof` GitHub repository](https://github.com/golang/go/tree/master/src/net/http/pprof)
