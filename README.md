# HydroMesh

**HydroMesh** is an interactive, real-time **2D Slice and 3D Tank liquid simulation** built inside a single self-contained HTML file (`HydroMesh.html`). It combines particle-based fluid dynamics, real-time Surface Nets isosurface meshing, two-way rigid-body buoyancy, drivable boat controls with splashing and cockpit detail, and a translucent liquid-glass interface—all running directly in the browser with no build step or backend server. Made with assistance from **Gemini 4 Hydrogen at xhigh effort**.

---

## Optimisations

- **Single-File Architecture (`HydroMesh.html`):** The entire application—HTML layout, responsive CSS, Three.js scene setup, fluid solver, surface meshing, rigid-body physics, procedural textures, and UI logic—lives in a single `.html` file. You can open it directly or host it anywhere with zero bundler or dependency-management overhead.
- **~3,000-Line Self-Contained Codebase:** Roughly **~5.5K lines of code** packed into one file, balancing rich visual and physical features with readable, modular sections and a compact project footprint.
- **Zero-Allocation Typed Arrays (SoA):** Particle positions, previous positions, velocities, density constraints, neighbor lists, spatial hash buckets, and up to 16 rigid-body objects use pre-allocated typed arrays (`Float32Array`, `Int32Array`, `Uint8Array`) to avoid garbage-collection hitches during real-time simulation.
- **Dual Representation (Droplets to Fused Liquid):** Morph smoothly between discrete instanced spheres (`Liquid Fusion` at `0%`), transitional blending, and a continuous Surface Nets liquid volume (`Pure Liquid` at `100%`) rendered at `0.70` opacity.

---

## Core Features

### 1. 2D Slice & 3D Tank Modes
- **2D Slice Mode:** Flattens the simulation plane and adjusts the camera for cross-sectional wave, splash, and buoyancy experiments.
- **3D Tank Mode:** Full volumetric tank with orbit, pan/zoom, procedural PMREM studio reflections, and animated pool-tile floor caustics.

### 2. Fluid Controls & Scaling Detail
- **Liquid Fusion:** Blend continuously from individual droplets/balls to a fused liquid mesh.
- **Amount:** Adjust fluid volume fill inside the tank (`10%–90%`).
- **Waves:** Drive rhythmic wave tank motion (`tankX` / `tankVx` / `tankAx`) that sloshes water and moves floating objects.
- **Magnet Force:** Grab, lift, and stir fluid particles directly with pointer or touch input.
- **Detail Scaling (Up to 4,000 Particles):** Preserves the default detail level while extending particle counts up to **4,000** across **Very High** (`2,500–3,200`), **Ultra** (`3,200–3,900`), and **Max** (`3,900–4,000`).
- **Custom Water Color:** Tint the fluid, surface attenuation, and dynamic UI accents with a color picker.
- **Splash & Reset:** Trigger an instant water splash or reset the tank and objects cleanly.

### 3. Floating & Drivable Objects
- **Three Sculpted Shapes:** Place **Harbor Buoy**, **Small Boat**, and **Rubber Duck** objects (up to 16 total objects, with a single active boat), complete with ghost placement previews and **Tap to Place** or **Stir Water** interaction modes.
- **Buoyancy & Size:** Customize object scale (`50%–200%`), buoyancy presets (**Light Float**, **Balanced**, **Heavy Sinker**), and object colors.
- **Boat Driving, Seat View, Splashing & Cockpit Detail:**
  - Drive the boat using **W A S D** or **Arrow keys** (and a touch joystick in Boat Seat View).
  - Toggle **Boat Seat View** to ride from the helm with look controls.
  - Moving through water generates bow-wake spray, stern prop-wash churn, trailing foam, and fluid impulses.
  - Detailed close-up boat model featuring a lofted V-hull, teak cockpit sole, seats, windshield, outboard motor with spinning propeller, steering wheel, throttle lever, gauges, and decorative dashboard buttons/switches.

### 4. Liquid-Glass UI & Theme Support
- **Liquid-Glass Panels:** Translucent frosted glass sidebar/sheet and HUD pills with specular borders, spring-like hover scale-ups, and glowing hover states.
- **Dark & Light Themes:** Toggle between dark and light modes with synchronized lighting, grid, tank framing, and floor styling.
- **Mobile & Desktop Responsive:** Adapts between a collapsible right sidebar on desktop/tablet and a compact bottom sheet with quick actions and a touch scroll lane on mobile.

---

## Quick Start

1. Download or clone `HydroMesh.html`.
2. Open `HydroMesh.html` in a modern WebGL-capable browser (Chrome, Edge, Firefox, Safari).
3. Drag on the fluid to use the magnet, open the **Fluid** tab to adjust waves/fusion/detail, or switch to the **Objects** tab to drop buoys, ducks, or the boat.

---

## Controls Cheat Sheet

| Action | Desktop | Touch / Mobile |
| :--- | :--- | :--- |
| **Fluid Magnet / Stir** | Left-click & drag | 1-finger drag |
| **Orbit Camera** | Right/Middle drag (or drag outside fluid) | 2-finger drag / pinch |
| **Place Object** | Click in **Tap to Place** mode | Tap / drag in **Tap to Place** mode |
| **Drive Boat** | `W` `A` `S` `D` or Arrow keys | Virtual joystick (in Boat Seat View) |
| **Look (Boat Seat View)** | Drag on canvas | 1-finger drag on canvas |
