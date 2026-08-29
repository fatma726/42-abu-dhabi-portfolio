# Rank 02 · Push_swap

## Objective

Sort integers in stack A using only the legal stack operations, with stack B as workspace and a small operation count.

## What it teaches

Linked structures, duplicate/overflow validation, rotations, index compression, small-set strategies, radix or chunk sorting, and cost measurement.

## Architecture and code flow

`argv → parse → validate → build A → choose legal move → update A/B → check sorted`. Primitive operations (`sa`, `pb`, `ra`, reverse rotations and combined moves) should be correct before optimization. A strategy then chooses the cheapest safe next move.

## Build and usage

```bash
make
./push_swap 4 2 1 3
./push_swap 4 2 1 3 | ./checker 4 2 1 3
```

The existing local snapshot contains other authors/collaborators and remains private; this is an attribution-safe lesson.

## Tests and evaluation tips

Test empty input, one/two values, duplicates, signs, overflow, already sorted data, and random sets of 100 and 500 values. Check that every printed operation is legal and that the checker ends with `OK`.

## Common mistakes and improvements

Broken linked-list links, accepting duplicates, false operations, and optimizing before correctness are common. Improve with operation counters, randomized regression tests, and a documented strategy comparison.

## What I learned

Algorithm quality needs two measurements: it must be correct and it should use resources efficiently.

See the [animated lesson](../../../lessons/index.html#push-swap).
