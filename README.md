# 2024 Google Summer of Code (GSoC) Overview

Parallel programming has advanced many of today's scientific computing projects to a new level.
However, writing a program that utilizes parallel and heterogeneous computing resources
is not easy because you often need to deal with a lot of technical details,
such as load balancing, programming complexity, and concurrency control.
[Taskflow](https://taskflow.github.io/) streamlines this process and helps you quickly create 
high-performance computing (HPC) applications with programming productivity.

As the user community of Taskflow continues to grow,
we have identified an important project to enhance Taskflow's library infrastructure,
described below:

## Project: Enhancing Work-stealing Scheduler

The goal of this project is to enhance the performance of the work-stealing scheduler in Taskflow
by implementing a worker-specific notification module in [notifier](https://github.com/taskflow/taskflow/blob/master/taskflow/core/notifier.hpp).

### Rationale

The performance of Taskflow is backed up by its work-stealing scheduler, which consists of two major components:
  1. Task-level scheduler that decides how tasks are enqueued to maximize the capabilities of our programming model
  2. Worker-level scheduler that decides which worker gets notified to run and steal a task from a task queue

As Taskflow incorporates more and more functionalities, it becomes important to enable fine-grained control over workers.
For instance, to incroporate multitasking-styled method, we need to wake up a specific worker instead of any worker.
Unfortunately, this capability is not available in Taskflow's [notification module](https://github.com/taskflow/taskflow/blob/master/taskflow/core/notifier.hpp).

### Approach

1. Extend the [notification module](https://github.com/taskflow/taskflow/blob/master/taskflow/core/notifier.hpp) to have a method that wakes up a specific worker
2. Implement extensive unittests to verify the new functionalities
3. Evaluate the performance of the new notification method

### Expected Outcome

We will merge the solution to the main Taskflow library. 
Our handbook will contain comprehensive instructions for reproducing the results and benchmarking the performance with Intel TBB.
We will also encourage participants to publis these results in related parallel computing conferences
or arXiv journals and to present our findings in leading C++ communities (e.g., CppCon, CppNow).

### Skills Required/Preferred

Participants should have decent C++14/17/20 programming experience. 
Basic knowledge about parallelism is preferred.

### Mentors

The [Taskflow Team](https://taskflow.github.io/taskflow/team.html) will mentor this project throughout the course of summer code.
Participants should expect weekly project meeting to sync up the progress.

### Expected Size of Project

We expect a *large size* (350 hours) for this project because it spans multiple activities, such as implementing algorithms, benchmarking the solutions, and deploying solutions to real use cases.

### Difficulty Level

We rate this project an *medium* level of difficulty. This project primarily focuses on 
*using* Taskflow to implement parallel algorithms and applications, rather than developing
the Taskflow core functionalities. 
Participants in this project will gain much practical and hands-on experience 
of parallel programming and understand the pros and cons of mainstream parallel programming tools.

### Contact

Feel free to reach out the tsung-wei.huang at wisc.edu for any questions.
