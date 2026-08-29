# Rank 01 · Get Next Line

## Objective

Return exactly one line per call from a file descriptor, including the final line when it has no trailing newline.

## What it teaches

`read`, file descriptors, static storage, partial reads, buffer-size choices, EOF, and ownership across calls.

## Architecture and code flow

`saved remainder → read a chunk → append → find first newline → return line → preserve remainder`. Multi-FD variants keep state indexed by descriptor. The key helpers search for a newline, join chunks, split the returned line, and dispose state on errors.

## Build and usage

```bash
cc -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c demo.c -o gnl_demo
./gnl_demo sample.txt
```

The utility is also used in the verified Cub3D source bundle. No separate attributable Fatma repository was found.

## Tests and evaluation tips

Use empty files, one-byte files, long lines, many short lines, tiny and large buffers, multiple descriptors, read errors, and a final line without `\\n`. Confirm no byte is duplicated or lost and run a leak checker after every EOF path.

## Common mistakes and improvements

Do not share one remainder between descriptors, leak state on `read` failure, or drop the final line. Improve with a small per-FD state object and property tests that compare concatenated output to the original file.

## What I learned

Stateful I/O is an ownership problem: every byte must be either returned, saved, or freed.

See the [animated lesson](../../../lessons/index.html#get-next-line).
