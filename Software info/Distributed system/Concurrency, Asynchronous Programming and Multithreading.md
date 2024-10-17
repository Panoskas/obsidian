Concurrent and parallel are effectively the same principle as you correctly surmise, both are related to tasks being executed simultaneously although I would say that parallel tasks should be truly multitasking, executed "at the same time" whereas concurrent could mean that the tasks are sharing the execution thread while still appearing to be executing in parallel.

Asynchronous methods aren't directly related to the previous two concepts, asynchrony is used to present the impression of concurrent or parallel tasking but effectively an asynchronous method call is normally used for a process that needs to do work away from the current application and we don't want to wait and block our application awaiting the response.

For example, getting data from a database could take time but we don't want to block our UI waiting for the data. The async call takes a call-back reference and returns execution back to your code as soon as the request has been placed with the remote system. Your UI can continue to respond to the user while the remote system does whatever processing is required, once it returns the data to your call-back method then that method can update the UI (or handoff that update) as appropriate.

From the User perspective, it appears like multitasking but it may not be.

---

EDIT

It's probably worth adding that in many implementations an asynchronous method call will cause a thread to be spun up but it's not essential, it really depends on the operation being executed and how the response can be notified back to the system.

# 1. Concurrency

- Concurrency is a concept where several tasks appear to run simultaneously, but not necessarily in parallel.
- It’s about dealing with multiple tasks at once, which can be achieved in various ways, including parallelism (using multiple processors), interleaved processing (time-slicing on a single processor), or even distributed processing across multiple machines.
- It’s about **managing access to shared resources, ensuring that data remains consistent, and tasks are executed in an orderly manner**.

# 2. Asynchronous Programming

![](https://miro.medium.com/v2/resize:fit:700/0*aeasNTuz4j6Hya4I.png)

- Asynchronous programming **is a form of concurrency where tasks start and then move on without waiting for the previous task to finish. This can be achieved using callbacks, promises, futures, events, etc.**
- It’s **especially popular in I/O-bound operations (like reading files, making network requests)** where tasks don’t need to wait for the operation to complete and can proceed with other operations, improving responsiveness.
- Asynchronicity doesn’t necessarily imply parallel execution. **The tasks may still be executed in a single thread (like in JavaScript’s Node.js)**, but the system can handle other tasks while waiting for some tasks to complete.

# 3. Multithreading

![](https://miro.medium.com/v2/resize:fit:700/0*2lmBNlyb6Cn_LRAP.png)

- Multithreading is a form of concurrency where multiple threads (smallest unit of CPU execution) run in parallel on multi-core processors.
- It allows true parallel execution of tasks.
- Managing multithreaded applications can be **complex** due to issues like **race conditions, deadlocks, and the need for synchronisation mechanisms.**
- Unlike asynchronous programming, which may or may not use threads, multithreading always involves multiple threads.

# _How they relate to each other ?_

**Concurrency vs. Asynchronous Programming** : _Concurrency is the broader concept, and asynchrony is one way to achieve it. Asynchronous operations might be carried out concurrently (in parallel) or might simply free up the main thread to do other tasks while the asynchronous task is waiting for some resource._

**Concurrency vs. Multithreading:** _Again, concurrency is the overarching concept. Multithreading is one method to achieve concurrency by running multiple threads in parallel. However, concurrency doesn’t always mean tasks run in parallel; it means they’re being managed in a way that they appear to be running at the same time._

**Asynchronous Programming vs. Multithreading**: _Asynchronous programming can be achieved without multithreading (e.g., event-driven systems like Node.js). Conversely, multithreaded systems can be synchronous, where each thread waits for its operations to complete before moving on. However, in many modern systems, asynchrony and multithreading often go hand in hand, with asynchronous operations being offloaded to different threads to achieve parallelism._

In summary, while these terms are related and sometimes used interchangeably, they each have distinct meanings and implications. Understanding the nuances can help in designing efficient and effective systems.

> _Concurrency can be achieved through various mechanisms, not just asynchronous programming and multithreading. I will be covering those concepts in my next post_

[  
](https://medium.com/tag/programming?source=post_page-----724340dec4df---------------programming-----------------)


### Go vs .NET
Let's clarify both of these points regarding Go and .NET:

### **Go:**

- **Go Routines and Threads**:
  - When you use the `go` keyword in Go to start a Go routine, a new thread is **not** necessarily created. Instead, Go routines are lightweight and managed by the Go runtime, which uses a **scheduler** to efficiently multiplex these Go routines onto a limited number of OS threads.
  - **Key Point**: Go routines are not 1:1 mapped to OS threads. Thousands of Go routines can run concurrently on a relatively small number of threads. The Go runtime creates and manages threads as needed, but it optimizes for efficiency and scalability by reusing threads and scheduling Go routines onto them as needed.
  - The Go scheduler handles the execution of Go routines across threads, so starting a Go routine does not directly correspond to creating a new OS thread.

### **.NET (C#):**

- **`async/await` and Threads**:
  - In .NET, using `async/await` does not necessarily create a new thread. Instead, `async/await` allows asynchronous operations to run in a non-blocking manner on the existing thread. While an `async` method is waiting (for example, on I/O), the thread is free to perform other work or be returned to the thread pool.
  - **Key Point**: When you use `async/await`, the code after the `await` runs on the same thread that started the method, assuming the `SynchronizationContext` has not changed (this is particularly relevant in UI applications). However, if you are in an environment like a web application (ASP.NET), the continuation after `await` might run on a different thread from the thread pool, but no new thread is created unless specifically required (e.g., for CPU-bound tasks).
  - The .NET runtime uses a **thread pool** to manage threads efficiently. When a task is awaited, the thread is released back to the pool, and the continuation can run on any available thread when the awaited task completes.

### **Summary**:

- **In Go**: Using `go` does **not** create a new thread for each Go routine. Instead, Go routines are scheduled onto existing threads by the Go runtime, allowing for very efficient concurrency with many Go routines running on a limited number of threads.
  
- **In .NET**: Using `async/await` does **not** create new threads. The code runs asynchronously on the current thread, and if the method awaits something like an I/O operation, the thread can be returned to the thread pool. The continuation after `await` might run on the same or a different thread, but a new thread is not created unless necessary.

In both Go and .NET, the idea is to efficiently manage concurrency without the overhead of creating and destroying threads for each concurrent operation.