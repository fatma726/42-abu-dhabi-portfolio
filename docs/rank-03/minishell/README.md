# Rank 03 · Minishell

## Objective

Build a Bash-style shell in C with parsing, expansion, built-ins, pipelines, redirections, heredocs, signals, process control, and cleanup.

## What it teaches

Lexing and syntax validation, quote rules, environment ownership, `fork`/`execve`/`waitpid`, file descriptors, signal modes, and error/status propagation.

## Architecture and code flow

`readline → tokenize → validate syntax → expand variables/wildcards → prepare pipes/redirections → run built-in or execve → wait → restore signals → free`. The parser must finish before children are created so execution is predictable.

## Build and usage

On macOS, install Readline and adjust the Makefile paths if needed:

```bash
make
./minishell
make bonus
./minishell_bonus
```

The [verified source bundle](../../../42-abu-dhabi-source-rank03-minishell.zip) contains the Fatma-authored implementation snapshot and its Makefile. The separate [public minishell repository](https://github.com/fatma726/minishell-42) has the recruiter-facing architecture README.

## Tests and evaluation tips

Compare behavior with Bash for quotes, empty expansions, `$?`, pipes, `<`, `>`, `>>`, heredocs, wildcard rules, built-ins, invalid commands, Ctrl-C, Ctrl-D, and exit status. Run leak and file-descriptor checks after every failure path.

## Common mistakes and improvements

Leaking FDs, expanding inside single quotes, mishandling a built-in in a pipeline, and freeing child-owned memory twice are common. Improve with differential tests against Bash and a single cleanup-owner table.

## What I learned

A shell is both a compiler pipeline and a process supervisor.

See the [animated lesson](../../../lessons/index.html#minishell).
