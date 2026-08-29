# Rank 00 · Libft

## Objective

Build a reusable C library from first principles: libc-style character, string, memory, conversion, and file-descriptor helpers, plus linked-list utilities.

## What it teaches

- Pointer arithmetic, arrays, null terminators, and const-correct APIs.
- Heap ownership, overflow-aware allocation, and cleanup on partial failure.
- Linked-list nodes and traversal.
- Headers, static archives, compiler warnings, and Makefiles.

## Architecture and code flow

`libft.h` defines the public contract. Each small `.c` file implements one function. The Makefile compiles source files to objects, then `ar` packages them into `libft.a`:

`caller → libft.h → function → libft.a → linked executable`

Important functions include `ft_strlen`, `ft_memcpy`, `ft_split`, `ft_itoa`, `ft_lstnew`, `ft_lstadd_back`, and the file-descriptor writers.

## Build and usage

```bash
make
make clean
make fclean
cc main.c -L. -lft -o demo
./demo
```

The [verified source bundle](../../../42-abu-dhabi-source-rank00-libft.zip) includes the Makefile and headers.

## Tests and evaluation tips

Compare behavior with libc for normal, empty, boundary, and invalid inputs. Test `INT_MIN`, empty splits, embedded zero bytes, NULL list pointers, and allocation failures. Use compiler warnings and a leak checker. Evaluation should check return values as well as visible output.

## Common mistakes and improvements

Reserve room for `\\0`, check multiplication before `malloc`, free every partially built array, and never return a pointer to freed memory. Possible improvements are a small unit-test runner, fuzz tests, and documented ownership annotations.

## What I learned

Precise contracts and explicit ownership make every later 42 project easier to reason about.

For the visual lesson, open the [interactive lab](../../../lessons/index.html#libft).
