# Rank 02 · Minitalk

## Objective

Send a message between independent processes using only `SIGUSR1` and `SIGUSR2`.

## What it teaches

PIDs, bitwise encoding, signal handlers, byte reconstruction, acknowledgement protocols, validation, and async-signal-safe behavior.

## Architecture and code flow

`client character → eight bits → SIGUSR1/2 → server shifts bit into byte → print after eight bits → acknowledge`. The bonus path confirms progress so a fast client cannot overrun the receiver.

## Build and usage

```bash
make
./server
./client <server-pid> "hello 42"
make bonus
./server_bonus
./client_bonus <server-pid> "long message"
```

The [verified source bundle](../../../42-abu-dhabi-source-rank02-minitalk.zip) contains the Fatma-authored client, server, headers, and Makefile.

## Tests and evaluation tips

Try empty, long, repeated, and non-ASCII byte sequences plus invalid, zero, and stale PIDs. Confirm the final NUL reaches the server and that the client waits for acknowledgements.

## Common mistakes and improvements

Unsafe handler calls, timing races, lost final bytes, and missing NUL termination are classic failures. Improve with a tiny protocol diagram, timeout handling, and one deterministic integration test.

## What I learned

Even a two-signal channel needs a clear protocol, synchronization, and failure behavior.

See the [animated lesson](../../../lessons/index.html#minitalk).
