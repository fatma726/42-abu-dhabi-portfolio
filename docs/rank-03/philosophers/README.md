# Rank 03 · Philosophers

## Objective

Simulate philosophers sharing forks while avoiding races, deadlocks, starvation, inaccurate timing, and output after shutdown.

## What it teaches

POSIX threads, mutex ownership, lock ordering, monitor design, timestamps, fairness, and coordinated termination.

## Architecture and code flow

`parse arguments → create fork mutexes and philosopher threads → eat/ sleep/ think loop → monitor last-meal timestamps → stop on death or required meals → join and destroy`. A consistent fork-lock strategy prevents circular waits.

## Build and usage

```bash
make
./philo 5 800 200 200
```

Add the meal-count argument for the finite-run variant. The local tree is a Theo Guérin reference tree with limited Fatma edits, so its source is not republished.

## Tests and evaluation tips

Try one philosopher, odd/even counts, tiny `time_to_die`, long runs, and finite meals. Check timestamps, one-fork behavior, no duplicate death messages, and clean mutex destruction.

## Common mistakes and improvements

Locking forks in the same order, reading timestamps without protection, sleeping too coarsely, and printing after the stop flag are common. Improve with monotonic time and a deterministic event log for tests.

## What I learned

Concurrency correctness is about ownership and timing as much as code structure.

See the [animated lesson](../../../lessons/index.html#philosophers).
