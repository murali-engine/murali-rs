# Murali

Murali is a **Rust-based animation engine** for deterministic, timeline-driven mathematical, AI,
and teaching visuals. Its engine, scene model, timeline, and renderer are written in Rust and render
through `wgpu` (Metal, Vulkan, DirectX). Experimental Python bindings are available for early
authoring and integration work.

| You want to | Install | Details |
| --- | --- | --- |
| Build with or extend the engine | Rust crate `murali = "0.3.0"` | [Rust engine guide](./RUST.md) |
| Explore the experimental Python API | `pip install murali-kit==0.3.0` (pulls `murali-engine==0.3.0`) | [Experimental Python support](./PYTHON.md) |

The Rust crate is the primary engine and runtime surface. Use it to embed Murali, extend rendering,
or build an authoring layer. The Python packages expose an experimental subset of the engine for
rapid scene authoring and integrations; expect their APIs to change.

Python support is experimental and its APIs are unstable until at least **0.5.0**. For the earlier
high-level Rust scene-authoring API, see [`murali` 0.2.4](https://crates.io/crates/murali/0.2.4)
and its [GitHub-native documentation](./documentation/README.md).

Documentation: [current Rust engine](./RUST.md) · [complete GitHub-native Rust docs](./documentation/README.md)
· [experimental Python support](./PYTHON.md). These Markdown files are the documentation source of
truth; this project does not maintain a separate documentation website.

## Rust engine

```toml
[dependencies]
murali = "0.3.0"
anyhow = "1"
glam = "0.33"
```

Use the crate when embedding Murali in a Rust program, extending the renderer, or building an
authoring or runtime integration.

More: crate layout, `murali.toml`, Cargo examples, experimental features — **[RUST.md](./RUST.md)**.

## Experimental Python support

```bash
python3 -m pip install murali-kit==0.3.0
```

```python
from murali_engine import Circle, Label, Scene
from murali_kit.colors import GREEN_D, WHITE
from murali_kit.themes import DarkTheme

scene = Scene()
scene.apply_theme(DarkTheme())
scene.add(Label("Hello Murali", height=0.38, color=WHITE), at=(0.0, 2.4, 0.0))
scene.add(Circle(radius=1.2, color=GREEN_D).with_stroke(0.04, WHITE))
scene.preview()
```

`murali-engine` provides experimental Python bindings for scenes, tattvas, timelines, cameras,
preview, and export. `murali-kit` adds themes, named colors, reusable teaching views, and examples.

More: wheels, frames, export, maturin, kit examples — **[PYTHON.md](./PYTHON.md)**.

## Development

Development of the optional Python bindings uses [uv](https://docs.astral.sh/uv/) for its
environment and lockfile. From a checkout:

```bash
uv sync
uv run pytest python/tests
```

After changing the Rust bindings, rebuild the editable extension with
`uv run maturin develop --features python`.

End-user wheels remain standard Python packages and do not require uv.

## Videos

[![Shapes](./resources/shapes.png)](https://youtu.be/rzQZHta2PQM)
[![Animation showcase](./resources/animation_showcase.png)](https://youtu.be/W8WQQbSo70Y)

## License

Murali is dual-licensed under either the MIT License or the Apache License, Version 2.0.
