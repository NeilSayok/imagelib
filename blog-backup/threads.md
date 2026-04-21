# Threads

*22 April 2026*

---

## Definition

A **Thread** is a mechanism which helps in parallel processing of a program. It is basically a mechanism which helps in utilization of the CPU cores to the maximum.

---

## What is a CPU Core?

A CPU core is the real hardware which runs the programs. At a time, a CPU core can run a **single program / piece of code**.

---

## So how does Threading achieve Parallelism?

In reality, Threads are basically **Queues**. In each Thread, the OS / the Program queues up code and now the CPU decides which part of code to run. If a thread gets blocked, it immediately **switches to the next thread** and executes until it is complete / blocked.

---

## Example

![How Threading works](https://neilsayok.github.io/imagelib/images/blog/threads/CPU-thread-image.png)


> When P1 needed user input and was pushed out, the CPU immediately switched to T2 and started executing P4 — no idle time wasted.

---

## Key Insight

> ℹ️ In reality, **actual parallelism** can only be achieved by **increasing Core count**.
>
> Threading is just a **smart way to handle the core** and thus saving execution time.