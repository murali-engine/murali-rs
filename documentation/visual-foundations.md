# Visual Foundations

Before jumping into your first scene, it’s important to understand how Murali thinks about **space, positioning, and visuals**.

Murali uses a deterministic, world-coordinate system — not pixels — which makes animations predictable and reproducible.

This page builds the mental model you need.

---

## Key Idea

Murali is **not pixel-based**.

Everything is defined in a **world coordinate system**, which makes:

- layouts predictable  
- animations resolution-independent  
- outputs reproducible  

---

## Colors

Murali defines constants for colors so that it is easy to use them while creating scenes.

| Category | Constants | Hex values |
| --- | --- | --- |
| Achromatic | `WHITE`, `BLACK` | `#FFFFFF`, `#000000` |
| Gray | `GRAY_A` → `GRAY_E` | `#DCDCDC`, `#BBBBBB`, `#888888`, `#555555`, `#222222` |
| Blue | `BLUE_A` → `BLUE_E` | `#C7E9F1`, `#9CDCEB`, `#58C4DD`, `#29ABCA`, `#1C758A` |
| Teal | `TEAL_A` → `TEAL_E` | `#ACEAD7`, `#76DDC0`, `#5CD0B3`, `#55C1A7`, `#49A88F` |
| Green | `GREEN_A` → `GREEN_E` | `#C9E2AE`, `#A6CF8C`, `#83C167`, `#77B05D`, `#699C52` |
| Yellow | `YELLOW_A` → `YELLOW_E` | `#FFF1B6`, `#FFEA94`, `#FFFF00`, `#F4D345`, `#E8C11C` |
| Gold | `GOLD_A` → `GOLD_E` | `#F7C797`, `#F9B775`, `#F0AC5F`, `#E1A158`, `#C78D46` |
| Orange | `ORANGE_A` → `ORANGE_E` | `#F7C59F`, `#FCAF80`, `#FF862F`, `#F26522`, `#D14C0A` |
| Red | `RED_A` → `RED_E` | `#F7A1A3`, `#FF8080`, `#FC6255`, `#E65A4C`, `#CF5044` |
| Maroon | `MAROON_A` → `MAROON_E` | `#ECABC1`, `#EC92AB`, `#C55F73`, `#A24D61`, `#94424F` |
| Purple | `PURPLE_A` → `PURPLE_E` | `#CAA3E8`, `#B189C6`, `#9A72AC`, `#715582`, `#644172` |
| Pink | `PINK_A` → `PINK_E` | `#F4A2C0`, `#F5829B`, `#D147A3`, `#C2185B`, `#AD1457` |
| Pure | `PURE_RED`, `PURE_GREEN`, `PURE_BLUE` | `#FF0000`, `#00FF00`, `#0000FF` |


### How to think about colors

- Use **palette constants** (e.g. `BLUE_C`, `GREEN_E`) for semantic meaning  
- Use **raw colors (`Vec4`)** for fine-tuned visuals (backgrounds, subtle tones)  
- Prefer consistency over variety  

```rust
use murali::colors::*;

let circle_id = scene.add_tattva(
    Circle::new(1.5, 48, GREEN_E),
    ORIGIN,
);
```

---

## Positions

In Murali, the center of the screen is `(0, 0, 0)`.

You define positions using:

```rust
Vec3::new(x, y, z)
```

* `+x` → right
* `-x` → left
* `+y` → up
* `-y` → down
* `z` → depth (used for layering; higher values come closer to the camera)

> In Murali, positions are **absolute and deterministic** — the same coordinates always produce the same visual result.

You can either use raw vectors:

```rust
Vec3::new(2.0, 1.0, 0.0)
```

Or use predefined constants from `murali::positions`.

```rust
use glam::Vec3;

pub const ORIGIN: Vec3 = Vec3::ZERO;
pub const CAMERA_DEFAULT_POS: Vec3 = Vec3::new(0.0, 0.0, 10.0);

pub const UP: Vec3 = Vec3::Y;
pub const DOWN: Vec3 = Vec3::NEG_Y;
pub const LEFT: Vec3 = Vec3::NEG_X;
pub const RIGHT: Vec3 = Vec3::X;
```

### Common Position Constants

| Name | Vector | Meaning | Visual |
| --- | --- | --- | --- |
| `UP` | `(0, 1, 0)` | Move upward | ⬆️ |
| `DOWN` | `(0, -1, 0)` | Move downward | ⬇️ |
| `LEFT` | `(-1, 0, 0)` | Move left | ⬅️ |
| `RIGHT` | `(1, 0, 0)` | Move right | ➡️ |
| `ORIGIN` | `(0, 0, 0)` | Center of screen | 🎯 |
| `CAMERA_DEFAULT_POS` | `(0, 0, 10)` | Default camera position | 📷 |

---

## Themes

Murali provides two built-in themes:

* `dark` (default)
* `light`

Themes define:

* background color
* surface colors
* text colors
* accent colors

Once you're comfortable, you should create your own theme to define a consistent visual identity.

### Creating a custom theme

1. Create a `themes/` folder next to your `Cargo.toml`
2. Add a file (e.g. `sesh.toml`)
3. Define the required fields
4. Activate it from `murali.toml`

Example:

```toml
name = "murali-dark"
background = "#0A121C"
surface    = "#1C2E45"
surface_alt = "#2B405C"
text_primary = "#F2F7FC"
text_muted   = "#BCCEE2"
accent      = "#56C1F4"
accent_alt  = "#AA8EF9"
positive    = "#4FD193"
warning     = "#F9B742"
```

Then point Murali at the theme from your project config:

```toml
theme = "sesh"
```

Murali will look for `themes/sesh.toml` next to your project `Cargo.toml`.

---

## Palettes

For advanced use cases, Murali supports **custom palettes**.

Palettes allow you to define your own color systems beyond the built-in constants.

### How to create a palette

1. Create a `palettes/` folder next to your `Cargo.toml`
2. Add a file (e.g. `my_palette.toml`)
3. Define your colors inside
4. Load the palette by name in your scene code

Example palette file:

```toml
name = "my-palette"
primary = "#56C1F4"
secondary = "#AA8EF9"
highlight = "#F9B742"
```

Example usage:

```rust
use murali::Palette;

let palette = Palette::load("my_palette");
let primary = palette.require("primary");
```

> This feature is evolving — examples will be added soon.

---

You now have the core mental model for how Murali represents visuals.

→ Continue to [First Scene](./first-scene.md)
