# Experimental Python support

Murali is a Rust-based animation engine. `murali-engine` exposes experimental Python bindings for
scene authoring and integrations, while `murali-kit` adds higher-level helpers. These packages are
an early-access interface to the Rust engine, not its primary implementation language.

| Package | Import | Role |
| --- | --- | --- |
| `murali-engine==0.3.0` | `murali_engine` | Experimental bindings: scene, primitives, timeline, camera, preview, export |
| `murali-kit==0.3.0` | `murali_kit` | Themes, named colors, teaching views, examples |

Python support is experimental. APIs are unstable until at least **0.5.0**.

## Install

```bash
python3 -m pip install murali-kit==0.3.0
```

That pulls a compatible engine wheel on macOS arm64/x86_64, Linux x86_64/aarch64, and Windows
x86_64. No local Rust toolchain on those platforms.

Engine only:

```bash
python3 -m pip install murali-engine==0.3.0
```

Use `murali-engine` directly when experimenting with your own Python integration or toolkit and you
do not want kit opinions. Use the Rust crate for the primary engine surface ([RUST.md](./RUST.md)).

## A first scene

```python
from murali_engine import Circle, Label, Scene, Timeline
from murali_kit.colors import GREEN_D, WHITE
from murali_kit.themes import DarkTheme, apply_theme

scene = apply_theme(Scene(), DarkTheme())
title = scene.add(Label("Hello Murali", height=0.38, color=WHITE), at=(0.0, 2.4, 0.0))
circle = scene.add(Circle(radius=1.2, color=GREEN_D).with_stroke(0.04, WHITE))

timeline = Timeline()
timeline.animate(title).at(0.0).for_duration(1.0).typewrite_text().spawn()
scene.play(timeline)
scene.preview()
```

`preview()`, `save_png(...)`, and `export_video(...)` consume the scene — call one of them.

```python
Scene()
Scene(frame="portrait")
Scene(frame="square")
scene.save_png("frame.png", width=1920)
scene.export_video("scene.mp4", width=1920, fps=60)
```

This file is the canonical guide for the experimental Python interface.

## Examples

Python examples live in the kit repo, not in `murali/examples/`:

[murali-kit/examples](https://github.com/murali-engine/murali-kit/tree/main/examples)

```bash
uv run python examples/hello_shapes.py
uv run python preview_all.py --auto
```

## Develop bindings from this repo

Install [uv](https://docs.astral.sh/uv/getting-started/installation/), then run:

```bash
uv sync
uv run pytest python/tests
```

`uv sync` creates `.venv` when needed and installs the development dependencies locked in
`uv.lock`. It also builds the local extension through maturin. After changing Rust binding code,
rebuild it with `uv run maturin develop --features python`. The published `murali-engine` and
`murali-kit` wheels do not depend on uv.

Kit against an adjacent engine checkout: see
[murali-kit](https://github.com/murali-engine/murali-kit).
