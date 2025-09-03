# Task A1: Parallel CSV Aggregator (Multithreading)

## Problem

You’re given a CSV of transactions and must compute **per-user sum and average** of `amount`.
**Schema:** `userId,amount,category,timestamp`
The file may contain a few **bad lines** (non-numeric/missing amounts) and an occasional **duplicate header**.

**Sample (5K rows):** Attached in the repo

---

## Objective

Write a **Java 17** CLI program that:

* Reads the file **in batches** (e.g., 5k–20k lines) and processes batches **in parallel** using `ExecutorService`.
* Parses the header to find `userId` and `amount` (don’t hardcode column positions).
* For each batch, computes local `(sum, count)` per `userId`, then **merges** results safely.
* Skips malformed rows without stopping.
* Shuts down the thread pool cleanly.

**Run:**

```bash
java ParallelCsvAggregator <csvPath>
```

---

## Results required

* **Output to stdout** as CSV, **sorted by `userId`**:

  ```
  userId,sum,avg
  u1,40.000000,10.000000
  u2,21.000000,5.250000
  ...
  ```
* Must use an **ExecutorService** with >1 worker.
* Handle bad lines gracefully (e.g., count or log how many were skipped).

> Focus is on **multithreading logic**: sensible batching, correct merging, and clean shutdown.
