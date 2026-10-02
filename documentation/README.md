# Murali Rust Edition documentation

This is the complete, GitHub-native documentation for the last first-party Rust scene-authoring
release, `murali` `0.2.4`. It covers the features that were available on the hosted documentation
website, converted to ordinary Markdown that works directly on GitHub and in offline clones.

This documentation intentionally excludes the Python API. The repository's `main` branch has
continued to evolve, so use the `0.2.4` crate when following these pages:

```toml
[dependencies]
murali = "0.2.4"
```

## Learn Murali

1. [Introduction](intro.md)
2. [Installation](installation.md)
3. [Visual foundations](visual-foundations.md)
4. [Your first scene](first-scene.md)
5. [Mental model](mental-model.md)
6. [Coordinate system](coordinate-system.md)
7. [Video formats](video-formats.md)
8. [Common first mistakes](common-first-mistakes.md)
9. [Which API should I use?](which-api-should-i-use.md)

## Scene authoring

- [Scene and App](scene-and-app.md)
- [Timelines and clips](timelines.md)
- [Animations](animations.md)
- [Updaters](updaters.md)
- [Camera](camera.md)
- [Scene views](scene-views.md)
- [Export and capture](export-and-capture.md)
- [Useful features](useful-features.md)
- [3D prop assets](3d-prop-assets.md)

## Tattva reference

- [Tattva overview](tattvas/index.md)
- [Properties](tattvas/properties.md)
- [Primitives and paths](tattvas/primitives.md)
- [Text, LaTeX, Typst, and code](tattvas/text.md)
- [Tables](tattvas/tables.md)
- [Composite tattvas](tattvas/composite.md)
- [Opening](tattvas/opening.md)
- [Graphs and fields](tattvas/graphs.md)
- [Math](tattvas/math.md)
- [Layout](tattvas/layout.md)
- [Storytelling](tattvas/storytelling.md)
- [AI visualization](tattvas/ai.md)
- [Utility tattvas](tattvas/utility.md)

## Examples

- [Example catalog](examples/index.md)
- [Basics](examples/basics.md)
- [Animation](examples/animation.md)
- [Text and math](examples/text_and_math.md)
- [Graphs and fields](examples/graphs_and_fields.md)
- [Dynamics](examples/dynamics.md)
- [3D](examples/three_d.md)
- [Branding and export](examples/branding_and_export.md)
- [Showcase videos](examples/showcase.md)
- [Reference example videos](examples/reference-videos.md)
- [Version `0.2.4` repository example catalog](https://github.com/murali-engine/murali/blob/v0.2.4/examples/README.md)

## Engine architecture

- [Architecture map](architecture/architecture.md)
- [Overview](architecture/overview.md)
- [Scene and timeline](architecture/scene-timeline.md)
- [Tattva internals](architecture/tattva.md)
- [Dirty flags](architecture/dirty-flags.md)
- [Projection](architecture/projection.md)
- [ECS](architecture/ecs.md)
- [Renderer](architecture/renderer.md)
- [Text and LaTeX pipeline](architecture/text-and-latex.md)
- [End-to-end frame flow](architecture/end-to-end-flow.md)

## Advanced and experimental features

- [Experimental feature flags](beta/experimental-features.md)
- [Beta feature index](beta/index.md)
- [Chat input box](beta/chat-input-box.md)
- [Feature internals](feature-internals/overview.md)
- [Stepwise internals](feature-internals/stepwise.md)
- [Neural-network internals](feature-internals/neural-network.md)
- [AI visualization roadmap](ai-visualization/index.md)
- [Project roadmap](roadmap.md)

## Documentation policy

- Documentation in this directory is Markdown-only and must render on GitHub.
- Internal documentation links are relative so the pages work in forks and offline clones.
- Do not add Docusaurus frontmatter, components, generated routes, or hosted-site dependencies.
- Rust `0.2.4` behavior is the compatibility target for authoring examples in this directory.
