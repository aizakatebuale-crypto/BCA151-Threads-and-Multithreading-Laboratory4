# Threads and Multithreading Laboratory

## Student Information
- **Name:** Buale, Aiza Kate D.
- **Section:** Block 186
- **Date:** November 21, 2026

## Laboratory Description
This laboratory demonstrates thread creation, multithreading, thread coordination, and shared-resource management using Python.

## Completed Tasks
1. Single Thread
2. Multiple Threads
3. Thread Synchronization using join()
4. Shared Resource Management using Lock()

## Learning Outcomes
- Create and execute threads.
- Demonstrate concurrent execution.
- Explain thread coordination.
- Apply locks to protect shared resources.

---

## Program Execution Screenshots

### Task 1: Single Thread
<img width="1100" height="246" alt="image" src="https://github.com/user-attachments/assets/a6f376f2-e620-47a4-bab1-383a0a70a2b6" />


### Task 2: Multiple Threads
<img width="1132" height="263" alt="image" src="https://github.com/user-attachments/assets/c0bf3c6c-d7d5-4dc4-b8e1-aca0286ffc28" />


### Task 3: Thread Synchronization using join()
<img width="1192" height="112" alt="image" src="https://github.com/user-attachments/assets/cf926910-14d5-49cb-9af7-d0a163dee913" />


### Task 4: Shared Resource Management using Lock()
<img width="1102" height="41" alt="image" src="https://github.com/user-attachments/assets/c1f58c6e-72f9-4a87-9479-62b6c989d191" />


---

## Guide Questions and Answers

### Task 1: Creating and Executing a Single Thread
1. **What is the purpose of `threading.Thread()`?**
   It creates a new thread object and tells it which function (`display_numbers`) to run.
2. **What happens when `start()` is executed?**
   It begins running the thread's target function separately from the main program.
3. **What is the purpose of `join()`?**
   It tells the main program to pause and wait until the thread completely finishes its task before moving on.
4. **What happens if `join()` is removed?**
   The main program does not wait. It prints `"Program completed."` immediately while the thread is still counting numbers in the background.

### Task 2: Implementing Multiple Threads
1. **How many threads are created in the program?**
   Two new worker threads (`t1` and `t2`) are created, running alongside the main thread (3 threads total).
2. **Do the two threads execute independently?**
   Yes, once started, both threads run on their own at the same time without waiting for each other.
3. **Why might the output order change when the program is executed again?**
   The operating system's scheduler decides which thread gets CPU time first. Tiny differences in system timing can cause one thread to print slightly ahead of the other.
4. **What is the difference between sequential and concurrent execution?**
   * **Sequential:** Tasks run strictly one after another (Task 2 waits for Task 1 to finish).
   * **Concurrent:** Multiple tasks run and make progress during the same overlapping time period.

### Task 3: Thread Synchronization Using `join()`
1. **Why does the main program wait when `join()` is used?**
   `t1.join()` pauses the `main()` function until the `download_file` thread finishes its 3-second task.
2. **What happens when `join()` is removed?**
   The main program prints `"Main program continues."` immediately—before the file download even finishes.
3. **In what situations is thread synchronization necessary?**
   Whenever the main program (or another thread) needs a background task to finish first before using its result—such as waiting for a file to finish downloading before opening it.

### Task 4: Managing Shared Resources Using Thread Locks
1. **What is a shared resource?**
   Any variable, file, or memory space that multiple threads can access and change at the same time (like the `counter` variable).
2. **What is a race condition?**
   A bug where two or more threads try to update the same shared data at the exact same time, causing the final result to become inaccurate depending on which thread finishes first.
3. **What is the purpose of `threading.Lock()`?**
   It acts like a key so only one thread can access the shared variable at a time, forcing other threads to wait their turn.
4. **What is a critical section?**
   The specific part of the code that modifies a shared resource (`counter += 1`) and must only be executed by one thread at a time.
5. **Why is synchronization important when multiple threads access shared data?**
   Without synchronization, threads can overwrite each other's updates ("lost updates"), leading to wrong totals or corrupted data.

---

## General Review Questions

1. **What is the difference between a process and a thread?**
   A **process** is a complete, independent program with its own separate memory. A **thread** is a smaller unit of execution inside a process, and multiple threads share the same memory.
2. **What are the advantages of using multithreading?**
   It uses less memory than running multiple processes, lets threads share data easily, and keeps programs fast when waiting on slow tasks like downloads or file reading.
3. **How does multithreading improve application responsiveness?**
   Slow tasks (like loading data or downloading files) can run in a background thread so the main screen doesn't freeze while the user clicks around.
4. **What is the difference between concurrency and parallelism?**
   * **Concurrency** means managing multiple tasks at once by rapidly switching between them.
   * **Parallelism** means literally running multiple tasks at the exact same instant using multiple CPU cores.
5. **Why is a lock necessary when multiple threads access shared data?**
   Updating a variable takes multiple steps (read, add, save). A lock stops two threads from reading the same old value at once and overwriting each other's work.
6. **What might happen if a thread is not properly synchronized?**
   It can cause race conditions, wrong calculations (lost updates), corrupted data, or program freezes (deadlocks).
7. **Can multiple threads execute simultaneously on a single-core processor? Explain.**
   Not at the exact same physical instant. A single-core CPU can only do one instruction at a time, so it switches back and forth between threads very quickly to make them *appear* simultaneous (concurrency).
8. **How does the operating system manage kernel-level threads?**
   The OS keeps track of each thread's status (ready, running, or waiting) and uses a scheduler to assign CPU time slices to each thread across available processor cores.
```[cite: 1]
