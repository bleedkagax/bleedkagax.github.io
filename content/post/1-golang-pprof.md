---
title: Golang Pprof
name: 1-golang-pprof
date: 2024-09-07
draft: false
tags:
  - Golang
share: "true"
---

#  Overview of Pprof

`pprof` is a tool that comes with Go's standard library and is used for collecting and viewing profiling data. It can collect different types of profiles including:

- **CPU Profile**: Measures where the program spends most of its time.
- **Memory Profile**: Measures the amount of memory allocated and retained.
- **Block Profile**: Measures where the program spends time waiting for synchronization primitives.
- **Mutex Profile**: Measures contention on mutexes.

# Setting Up pprof

To use `pprof`, you need to import the `net/http/pprof` package and set up HTTP server to serve the profiling data.

## Step 1: Import the pprof Package

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

### Step 1: Enable pprof HTTP Endpoints

```go
import (
    "net/http"
    _ "net/http/pprof" // This blank import enables the HTTP endpoints for `pprof`
    "log"
    "time"
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
		// Simulating work by sleeping for a bit.
		time.Sleep(time.Millisecond * 10)

		// Log the work being processed.
		log.Printf("Worker %d is processing\n", id)

		// Signal that the work is done.
		done <- true
	}
}

func main() {
    startProfiler()

    numWorkers := 10000
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
   
### Step 4: Use pprof to Analyze Data

Use the `top` `list` `web` command

```bash
(pprof) top
Showing nodes accounting for 77021, 96.14% of 80112 total
top - 15:25:56 up  1:15,  0 users,  load average: 2.18, 2.84, 2.41
Tasks:  17 total,   1 running,  15 sleeping,   0 stopped,   1 zombie
%Cpu(s): 50.1 us, 11.5 sy,  0.0 ni, 37.4 id,  0.0 wa,  0.0 hi,  1.0 si,  0.0 st
MiB Mem :   7950.9 total,   4956.1 free,   2293.5 used,    701.4 buff/cache
MiB Swap:      0.0 total,      0.0 free,      0.0 used.   5196.8 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                              
    135 user      20   0 1717788 847608  10480 S   4.3  10.4   2:34.51 node                                                                                 
      6 user      20   0  954168  88244   9608 S   3.0   1.1   1:21.68 node                                                                                                             
    295 user      20   0  899088  16332   1264 S   0.0   0.2   0:00.99 nodemon                                                                              
    324 user      20   0  503980  12852      0 S   0.0   0.2   0:00.49 nixd                                                                                 
    439 user      20   0  684016  73544      0 S   0.0   0.9   0:00.87 nixd-attrset-ev        
   3949 user      20   0  223960   2840   1952 S   0.0   0.0   0:00.06 bash                                                                                 
   7542 user      20   0 1524220  75852      0 S   0.0   0.9   0:10.57 gopls                                                                                
   9074 user      20   0  223960   2560   1668 S   0.0   0.0   0:00.09 bash     
```
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
