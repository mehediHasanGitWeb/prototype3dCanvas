# 3D Shape & Material Studio

A single-file, browser-based 3D playground (`3dShapeMaterialStudio.html`) for building small scenes out of shapes, materials, liquids and lights, with an Excalidraw-style drawing layer and a set of interactive, sci-fi "hologram" tools on top.

> **Why this exists:** this prototype was built as an experiment **to check what Claude can do**: how far an AI assistant can take a real, interactive project step by step, from a plain 3D material viewer to a multi-tool creative studio, working only from short requests, screenshots and hand-drawn sketches.

---

## How to run it

1. Open `3dShapeMaterialStudio.html` in a modern desktop browser (Chrome or Edge recommended).
2. That's it. There is no install, no build step and no server. Everything (the 3D engine, UI and effects) is written in plain HTML, CSS and JavaScript inside this one file, with **no external libraries**.

> Tip: keep only one tab of the studio open at a time. Each tab runs its own WebGL engine.

---

## Layout at a glance

| Area | What's there |
|---|---|
| **Top bar** | Reset Camera · Toggle Grid · Export SVG · Help · FPS counter |
| **Left panel** | Add Shape · Custom Shape Designer · 2D Shapes · Tools · Containers · Lighting · Scene Objects |
| **Viewport** | The 3D scene, plus the drawing layer and the placeable hologram tools |
| **Right panel** | Appears when an object is selected: Transform · Shape · Material · Liquid |

---

## 1. The 3D scene

### Camera
- **Left-drag** on empty space to orbit, **right-drag** to pan, **scroll** to zoom.
- **Reset Camera** returns to the default view; **Toggle Grid** shows or hides the floor grid.

### Shapes
- Built-in primitives: **Box, Sphere, Cylinder, Cone, Torus, Plane**.
- **Custom Shape Designer**: draw a profile and **revolve** it (vases, bottles) or draw an outline and **extrude** it, then generate a real 3D mesh.
- **Bevel** (rounded edges) for boxes, like a 3D `border-radius`.

### Transform
- **Move / Rotate / Scale** modes: drag directly on the selected object, or type exact values (X/Y/Z, RX/RY/RZ, SX/SY/SZ).
- **Duplicate** and **Delete**, plus a Scene Objects list for quick selection.

### Materials
- Presets: **Metal, Paper, Glass, Plastic**.
- Fine control over base color (with opacity), roughness, metalness and transmission.
- **Glass-morphism** controls: blur, saturation, tint and border glow.
- **Crack / magma** effect with its own color and scale.

### Liquids & containers
- **Box Tray** and **Glass Cup** containers, or turn any shape into a container.
- Pour **multiple liquid layers** (water, wine, juice, cola or custom colors), set the amount, viscosity and opacity, and **mix layers** together.
- A spring-based **slosh simulation**: tilt, rotate or **shake** a container and the liquid moves.
- **Sealed** vessels (snow-globe style), **neon glow** liquids with spread, hot core and flicker.

### Lights
- Add point lights, change their color and intensity, and move them around the scene.

### Export
- **Export SVG**: render an animated SVG of the scene (frame rate, duration, camera orbit, optional object spin, liquid simulation and auto-shake).

---

## 2. Excalidraw-style drawing layer

A 2D annotation layer on top of the 3D view, with a hand-drawn ("sketchy") look.

- **Tools:** Rectangle, Diamond, Ellipse, Arrow, Line, Free Draw, Text, Eraser.
- **Style panel:** stroke and background colors, hachure / cross-hatch / solid fills, stroke width, sloppiness (clean / artist / cartoon), font family and size, opacity.
- **Editing:** select, move, resize with corner handles (Shift keeps proportions), double-click text to edit, duplicate, delete, bring to front / send back.
- **More menu:** undo / redo, hide / show drawings, export drawings as PNG, clear all, keyboard shortcuts.

---

## 3. Tools panel

| Tool | Key | What it does |
|---|---|---|
| **Select** | V / 1 | Select drawings and 3D objects |
| **Hand** | H | Pan the camera with a left-drag |
| **Lock** | Q | Keep the current drawing tool active after each shape |
| **Toolbox** | B | Drop an animated 3D toolbox (see below) |
| **Control** | C | Place a control pad wired to a cube (see below) |
| **More** | – | Undo/redo, hide drawings, export PNG, clear, shortcuts |

The placeable tools (Toolbox, Control, Import) can be **dragged from the panel onto the floor**, or selected and then placed with a click on the floor. A glowing drop target shows where they will land.

### 3a. Toolbox (HoloLens-inspired)
- A real **3D toolbox object** drops in with a bounce. Its **lid swings open on a hinge**, two **trays slide out**, and hologram panels unfold above it.
- Panels: **Shapes**, **Containers & Lights** (warm / cool), and **Scene** actions (duplicate, delete, shake liquid, reset camera, toggle grid).
- Trays: **Materials** (metal, paper, glass, plastic) and **Liquids** (water, wine, juice, cola).
- Move it like any object, click it (when selected) to open or close the lid, and put it away with ✕.

### 3b. Control pad
- Places a sci-fi **control pad lying flat on the floor** (in true perspective) and a **3D cube** behind it.
- A **neon wire** with physics connects the pad to the cube. It sags, rests on the floor and **swings and shakes** when either end moves, and it glows in the chosen color.
- A **3×3 grid of contrasting colors**: click one and the cube takes that color, with a small bounce.
- A **Scratch-style code panel** (decorative), with blocks that light up as if running: *when color clicked*, *set cube color*, *repeat / turn / wait*, *say Hello!*.
- A **layer panel** (decorative): select, show/hide, lock, add and delete layers.
- Drag the pad by its header to slide it across the floor.

---

## 4. Import Portal (key 9)

Place as many portals as you like. Each one has:

- **A floor circle** with a **Cartesian coordinate frame**: the Y axis on the left and the X axis along the bottom, whole-number ticks from −5 to 5, a grid, axis markers and dashed guide lines.
- **A glowing draggable point** that can only move **inside the circle** and **snaps to whole numbers**. Its live **X** and **Y** values are shown in tags next to each axis. Double-click the point to recenter it.
- **A floating energy orb** above the circle's center: a blue core, purple glow, wireframe rings and lightning. It gets more energetic and shifts toward magenta as the point moves outward.
- **Ring strips around the orb:**
  - the **number of strips = the X value** (|X|, 0–5), stacked from top to bottom;
  - the **number of placeholder cells in each strip = the Y value** (|Y|, 0–5).
- **Pictures in placeholders:** click a placeholder cell to open the file picker. The chosen image appears **inside that exact cell**, clipped to its curved shape, and you can click again to swap it.
- Click the orb itself to import an image into the drawing layer.
- **Resize** the whole portal with the ⤡ knob (0.5× to 2.5×), **move** it by dragging the circle's rim, and remove it with ✕.
- The axes face the viewer when placed, so dragging right increases X and dragging forward increases Y.

---

## 5. Eraser

The eraser (E / 0) removes **anything**: drawings, Import portals, Control pads, the Toolbox and any 3D object. Click or drag over it; a small puff shows what was erased.

---

## 6. Robustness

- If the graphics driver resets or the GPU runs out of memory, the 3D view shows a clear **"lost graphics context"** message with a **Reload** button instead of a blank white box.
- Hologram overlays hide themselves when the camera gets too close, to avoid huge GPU layers.

---

## Keyboard shortcuts

| Key | Action |
|---|---|
| V / 1 | Select |
| H | Hand (pan) |
| R / 2 · D / 3 · O / 4 | Rectangle · Diamond · Ellipse |
| A / 5 · L / 6 · P / 7 | Arrow · Line · Free draw |
| T / 8 | Text |
| 9 | Import Portal |
| E / 0 | Eraser |
| B | Toolbox |
| C | Control pad |
| Q | Lock tool |
| Ctrl+Z / Ctrl+Y | Undo / Redo (drawings) |
| Ctrl+D | Duplicate drawing |
| Delete | Delete selected drawing |
| Arrow keys | Nudge selected drawing (Shift = 10px) |
| Esc | Deselect / back to Select |
| ? | Shortcut help |

---

## Known limitations

- Nothing is saved: reloading the page clears the scene, drawings and placed pictures.
- Hologram overlays (pads, portals, panels, wires) are drawn on top of the 3D view, so a 3D object moved in front of them won't hide them.
- The Scratch code blocks and the layer panel on the Control pad are for show.
- Each 3D object uses a single material, so the toolbox case is one color.

---

## Tech notes

- **Pure HTML/CSS/JavaScript, one file, no dependencies.**
- A hand-written **WebGL** renderer (matrix math, geometry generators, PBR-style shading, glass and liquid rendering, spring-based liquid simulation).
- Floor-mounted UI uses **CSS `matrix3d` homographies** so flat panels lie correctly on the 3D floor.
- The neon wire uses a **Verlet rope simulation**; the orb and its strips are drawn on a 2D canvas each frame.

---

*Built as a hands-on test of what Claude can do: every feature above was added iteratively from short requests, screenshots and hand-drawn sketches.*
