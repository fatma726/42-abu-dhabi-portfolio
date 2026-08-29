# Rank 01 · ft_printf

## Objective

Implement a printf-like formatter that reads a format string, dispatches conversions, writes output, and returns the exact character count.

## What it teaches

Variadic arguments, parser state, integer bases, pointer formatting, signed values, and API-compatible return values.

## Architecture and code flow

`format string → scan ordinary character → see % → choose typed printer → write bytes → add to count`. A dispatcher owns the conversion table while small printers handle characters, strings, decimals, unsigned values, hexadecimal values, and pointers.

## Build and usage

```bash
make
cc demo.c -L. -lftprintf -o demo
./demo
```

No attributable Fatma source snapshot was found; this page is a learning lesson rather than a source claim.

## Tests and evaluation tips

Compare with libc for zero, negative, `INT_MIN`, `UINT_MAX`, NULL strings, pointers, `%%`, mixed formats, and long output. Verify the return count for every case. Check that each `va_arg` type matches its conversion.

## Common mistakes and improvements

Wrong variadic types, missing sign handling, pointer `0x` formatting, and off-by-one counts are common. Improve with table-driven conversion tests and a fuzzed format-string harness.

## What I learned

A small public function can hide a disciplined parser with independent, testable stages.

See the [animated lesson](../../../lessons/index.html#ft_printf).
