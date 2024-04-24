-   **Program**: A program is a set of instructions that a computer can execute to perform a specific task. It is a static sequence of instructions written in a programming language. When a program is loaded into memory and becomes a process, it can be executed.

-   **Process**: A process is an instance of a program that is being executed. It contains the program code and its current activity. Each process has a separate memory address space, which means that a process runs independently and is isolated from other processes. It cannot directly access shared data in other processes. Switching from one process to another requires some time for saving and loading registers, memory maps, and other administrative information Has own code segment, data segment, heap, stack, registers.

-   **Thread**: A thread is the smallest unit of execution within a process. A process can have multiple threads. Each thread within the process shares the same data space with the entire process, so they can communicate with each other more easily than if they were separate processes. Threads are sometimes called lightweight processes and they do not require much overhead to create and manage. Has own stack, registers. Code segment, data segment, heap are used from the process.

### Concurrency

Concurrency means executing multiple tasks at the same time but not necessarily simultaneously. There are two tasks executing concurrently, but those are run in a 1-core CPU, so the CPU will decide to run a task first and then the other task or run half a task and half another task, etc. Two tasks can start, run, and complete in overlapping time periods i.e Task-2 can start even before Task-1 gets completed. It all depends on the system architecture.

The switching among tasks happens so fast that a user can't notice in blank eye therefore it seems the computer is making progress on more than one task concurrently. In reality, it is just context switching.

### Parallel Execution

Parallel execution refers to the concept of executing multiple tasks or processes simultaneously. This is made possible by systems with multiple processors or cpu cores.

### Concurrent Parallel Execution

Combination of Concurrency and Parallel Execution. For example, Among 4 tasks, task 1 and 2 are running concurrently in cpu 1, task 3 and 4 are running concurrently in cpu 2.

### Parallelism

Parallelism means that an application splits its tasks up into smaller subtasks which can be processed in parallel. Parallelism requires hardware with multiple processing units, essentially. In single-core CPU, you may get concurrency but NOT parallelism. Parallelism is a specific kind of concurrency where tasks are really executed simultaneously.

### Concurrency vs. Parallelism

A system is said to be concurrent if it can support two or more actions in progress at the same time. A system is said to be parallel if it can support two or more actions executing simultaneously.

The key concept and difference between these definitions is the phrase “in progress.”

This definition says that, in concurrent systems, multiple actions can be in progress (may not be executed) at the same time. Meanwhile, multiple actions are simultaneously executed in parallel systems. In fact, concurrency and parallelism are conceptually overlapped to some degree, but “in progress” clearly makes them different.

Concurrency is about dealing with lots of things at once. Parallelism is about doing lots of things at once.


### Thread Safety
### Deadlock
### Race Condition