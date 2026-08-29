# Rank 04 · Cub3D

## Objective

Turn a validated `.cub` map into a small ray-casting game with textures, movement, collision, and optional bitmap output.

## What it teaches

Configuration parsing, flood validation, DDA ray casting, fish-eye correction, texture sampling, MiniLibX hooks, collision, and teardown order.

## Architecture and code flow

`read .cub → validate directives/map/player → cast one DDA ray per screen column → compute perpendicular wall distance → draw textured column → handle input/collision → redraw`. Parser and renderer stay separate so invalid maps fail before a window opens.

## Build and usage

MiniLibX is a third-party dependency and is intentionally excluded from the bundle. Install the platform-appropriate version, then:

```bash
make
./cub3D maps/test.cub
```

The [verified source bundle](../../../42-abu-dhabi-source-rank04-cub3d.zip) contains Fatma-authored project code, maps, and Makefile but not MiniLibX binaries/sources.

## Tests and evaluation tips

Test missing/duplicate textures, invalid colors, open edges, diagonal gaps, duplicate players, collision corners, window close, and BMP output. Use a leak checker and verify all textures are freed before the display.

## Common mistakes and improvements

Mixing degrees and radians, using raw ray distance (fish-eye), accepting open maps, and freeing MiniLibX objects in the wrong order are common. Improve with parser fixtures, a collision epsilon, and a renderer debug overlay.

## What I learned

A precise parser and coordinate model are the foundation of a convincing real-time display.

See the [animated lesson](../../../lessons/index.html#cub3d).
