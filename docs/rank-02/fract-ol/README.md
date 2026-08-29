# Rank 02 · fract-ol

## Objective

Render interactive Mandelbrot and Julia fractals with zoom, keyboard/mouse controls, and a MiniLibX window.

## What it teaches

Complex numbers, iterative escape tests, screen-to-world mapping, color palettes, event hooks, image buffers, and redraw lifecycle.

## Architecture and code flow

`pixel → complex coordinate → iterate formula → escape count → color → image buffer → window`. Keep world coordinates separate from screen coordinates; input changes the view and triggers a redraw.

## Build and usage

```bash
make
./fractol mandelbrot
./fractol julia -0.8 0.156
```

Local copies carry other developers' headers, so no source is claimed here. Install the platform MiniLibX dependency separately.

## Tests and evaluation tips

Test unknown fractal names, bad parameters, zoom at corners, max iterations, close-window events, and redraw after every input. Check that image buffers and windows are freed.

## Common mistakes and improvements

Mixing coordinate systems, dividing by zero, redrawing stale buffers, and leaking images are common. Improve with a palette abstraction, zoom-centered-on-cursor math, and frame-time measurement.

## What I learned

A clean mathematical model becomes an interactive program when rendering and events share one coordinate system.

See the [animated lesson](../../../lessons/index.html#fract-ol).
