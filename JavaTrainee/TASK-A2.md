# Task A2: Simple Task Scheduler

## Problem

Build a tiny scheduler that stores tasks with **future Unix timestamps** and executes any tasks that are **due** (prints their descriptions).

---

## Objective

Write a **Java 17** CLI program exposing two methods:

```java
scheduleTask(String id, long epochSeconds, String description)
executeDueTasks() // execute & remove all tasks with time <= now
```

---

## Requirements (keep it simple)

* Use a **min-heap / priority queue** ordered by execution time.
* **Past times:** if a task is scheduled in the past, it should run on the next `executeDueTasks()` call.
* **Same timestamp:** if multiple tasks share the same time, execute them in a **stable** order (e.g., FIFO).
* Print each execution as:

  ```
  Executing task: <description>
  ```
* **Optional (nice-to-have):** basic thread safety if scheduling and executing could happen from different threads.

---

## Run example (transcript)

```bash
javac TaskScheduler.java
java TaskScheduler
```

Inside `main`, demonstrate:

```java
long now = java.time.Instant.now().getEpochSecond();
scheduler.scheduleTask("t1", now + 2, "Backup database");
scheduler.scheduleTask("t2", now + 2, "Send report email");
scheduler.scheduleTask("late", now - 5, "Run missed task");

// simple loop
for (int i = 0; i < 6; i++) {
  scheduler.executeDueTasks();
  Thread.sleep(1000);
}
```

**Expected output (order for equal timestamps can be FIFO):**

```
Executing task: Run missed task
... (after ~2s)
Executing task: Backup database
Executing task: Send report email
```

---

## What to submit

* `TaskScheduler.java` (and a tiny `main` showing the demo above).
* Short **README** (2–4 lines) describing the data structure and how to run.

---

## Acceptance checklist

* [ ] Uses a priority queue (min-heap).
* [ ] Executes all tasks with `time <= now` on each call to `executeDueTasks()`.
* [ ] Handles past timestamps and equal timestamps clearly.
* [ ] Prints exactly one line per executed task.
* [ ] Simple, readable code and clean exit.
