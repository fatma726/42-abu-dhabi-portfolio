# Rank 04 · C++ Modules 00–04

## Objective

Move from C to C++98 through focused exercises in classes, ownership, inheritance, polymorphism, and abstract interfaces.

## What it teaches

Constructors/destructors, canonical form, deep copies, operator overloading, inheritance, virtual dispatch, abstract classes, and exception-safe ownership.

## Architecture and code flow

`model state → protect invariants → implement canonical copy/assignment → extend through inheritance → call behavior through a base interface`. Each module has a small executable so one design idea can be isolated and tested.

## Build and usage

```bash
make
./exercise
```

Run the command from each module/exercise directory and keep the required `-std=c++98` flags. Local snapshots carry another student's headers, so no source is claimed here.

## Tests and evaluation tips

Test copy construction, assignment, self-assignment, deletion through a base pointer, virtual dispatch, wrong-type substitution, and owned-memory cleanup. Check compiler warnings and standard-version compliance.

## Common mistakes and improvements

Shallow copies, missing virtual destructors, exposed mutable state, and accidental C++11 features are common. Improve with ownership diagrams, sanitizers, and small interface contracts.

## What I learned

Good object-oriented interfaces make ownership, extension, and substitution explicit.

See the [animated lesson](../../../lessons/index.html#cpp-modules).
