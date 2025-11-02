# VibTraf Project Overview

The web application will be an interactive traffic simulation game inspired by SimCity, featuring an isometric view of a central field with highways entering from all four directions (north, south, east, west) converging at a simple crossroads. Users can enter a building mode to redesign the intersection (e.g., add lanes, traffic lights, roundabouts, or other elements) to optimize traffic flow. In simulation mode, vehicles of random types (e.g., cars, trucks, buses) and sizes spawn from the highways with random destinations, increasing in density over time until the system jams. The goal is to iteratively rebuild and test designs to handle higher traffic volumes before jams occur. The app must be responsive for desktops, tablets, and mobiles, using web technologies for accessibility without installations.

## Requirements
### Functional Requirements
* Map and View:
    * (MV-11) Render an isometric grid-based field (e.g., 20x20 tiles) with highways extending from the four edges to a central simple crossing (e.g., basic four-way intersection).
    * (MV-12) Support panning/zooming for detailed inspection, with touch gestures on mobile.
* Building Mode:
    * (BM-11) Tools to modify the crossroads: Place/remove road tiles, add traffic signals, signs, lanes, merges, or advanced structures like overpasses (keep initial scope simple).
    * (BM-12) Grid snapping for placements; validate builds (e.g., ensure connectivity to highways).
    * (BM-13) UI palette for selecting build elements (e.g., drag-and-drop or click-to-place).
* Simulation Mode:
    * (SS-11) Start/restart button to toggle simulation.
    * (SS-12) Vehicle spawning: Random types/sizes from each direction at increasing rates (e.g., start low, ramp up every minute).
    * (SS-13) Vehicle behavior: Random destination (e.g., straight, left, right turn); follow paths, obey signals, queue, avoid collisions.
    * (SS-14) Jam detection: When no space for new vehicles (e.g., queues block spawns), end simulation and show score (e.g., max density handled).
    * (SS-15) Real-time animation: Smooth vehicle movement in isometric perspective.
* Game Mechanics:
    * (GM-11) Scoring: Based on time/density before jam;
    * (GM-12)Reset: Clear builds to default and restart.
* Persistence:
    * (LL-11) Save designs locally (localStorage) for resuming.

### Non-Functional Requirements
* Compatibility: Responsive UI for all devices; support modern browsers.
* Performance: Handle 100+ vehicles without lag; use efficient rendering and simulation loops.
* Accessibility: Keyboard controls for building/simulation
* Security: Client-side only; no user data storage.
* Scalability: Modular for adding features like multiplayer or more complex AI.
Technology Stack
* Frontend Framework: React.js for UI components and state management; PixiJS or Phaser for isometric rendering and game loop (efficient for sprites/animations).
* Graphics and Simulation: Canvas with PixiJS for isometric tiles/vehicles (sprites for cars, path animations); or Three.js if needing pseudo-3D effects.
* Physics/AI: Custom JS for simple traffic rules (e.g., A* pathfinding for routes, basic collision detection); libraries like Matter.js for physics if collisions get complex.
* State Management: Redux for tracking map state, vehicle positions, and simulation params.
* Styling: CSS with Tailwind for responsive grids/UI.
* Build Tools: Vite 
* Testing: Jest for units
* Deployment: Github Pages

### Architecture
* High-Level Design:
    * Client-Side Only: All logic in browser for offline play.
    * Modules:
        * MapGenerator: Create initial field with highways and crossing; handle user edits (2D grid array for tiles: road=1, signal=2, etc.).
        * Renderer: Isometric projection (math for 2D-to-iso coords); draw tiles, vehicles as sprites.
        * Simulator: Game loop (requestAnimationFrame) for spawning, moving vehicles, checking jams.
        * VehicleAI: Classes for vehicles (position, speed, path, intent); random generation.
        * UIController: Modes toggle (build vs. sim), tool palettes, buttons.
    * Data Flow: Central state store for grid and entities; events trigger renders/updates.
    * Isometric Handling: Use tile-based system; sort draw order for depth (e.g., back-to-front).
    * Simulation Logic: Time-based spawning (interval increases density); pathfinding ensures vehicles navigate user-built paths.

## prompts 
```
Develop vibcol app accoding to the specification in README.md: 

bTraf Project Overview

The web application will be an interactive traffic simulation game inspired by SimCity, featuring an isometric view of a central field with highways entering from all four directions (north, south, east, west) converging at a simple crossroads. Users can enter a building mode to redesign the intersection (e.g., add lanes, traffic lights, roundabouts, or other elements) to optimize traffic flow. In simulation mode, vehicles of random types (e.g., cars, trucks, buses) and sizes spawn from the highways with random destinations, increasing in density over time until the system jams. The goal is to iteratively rebuild and test designs to handle higher traffic volumes before jams occur. The app must be responsive for desktops, tablets, and mobiles, using web technologies for accessibility without installations.

## Requirements
### Functional Requirements
* Map and View:
    * (MV-11) Render an isometric grid-based field (e.g., 20x20 tiles) with highways extending from the four edges to a central simple crossing (e.g., basic four-way intersection).
    * (MV-12) Support panning/zooming for detailed inspection, with touch gestures on mobile.
* Building Mode:
    * (BM-11) Tools to modify the crossroads: Place/remove road tiles, add traffic signals, signs, lanes, merges, or advanced structures like overpasses (keep initial scope simple).
    * (BM-12) Grid snapping for placements; validate builds (e.g., ensure connectivity to highways).
    * (BM-13) UI palette for selecting build elements (e.g., drag-and-drop or click-to-place).
* Simulation Mode:
    * (SS-11) Start/restart button to toggle simulation.
    * (SS-12) Vehicle spawning: Random types/sizes from each direction at increasing rates (e.g., start low, ramp up every minute).
    * (SS-13) Vehicle behavior: Random destination (e.g., straight, left, right turn); follow paths, obey signals, queue, avoid collisions.
    * (SS-14) Jam detection: When no space for new vehicles (e.g., queues block spawns), end simulation and show score (e.g., max density handled).
    * (SS-15) Real-time animation: Smooth vehicle movement in isometric perspective.
* Game Mechanics:
    * (GM-11) Scoring: Based on time/density before jam;
    * (GM-12)Reset: Clear builds to default and restart.
* Persistence:
    * (LL-11) Save designs locally (localStorage) for resuming.

### Non-Functional Requirements
* Compatibility: Responsive UI for all devices; support modern browsers.
* Performance: Handle 100+ vehicles without lag; use efficient rendering and simulation loops.
* Accessibility: Keyboard controls for building/simulation
* Security: Client-side only; no user data storage.
* Scalability: Modular for adding features like multiplayer or more complex AI.
Technology Stack
* Frontend Framework: React.js for UI components and state management; PixiJS or Phaser for isometric rendering and game loop (efficient for sprites/animations).
* Graphics and Simulation: Canvas with PixiJS for isometric tiles/vehicles (sprites for cars, path animations); or Three.js if needing pseudo-3D effects.
* Physics/AI: Custom JS for simple traffic rules (e.g., A* pathfinding for routes, basic collision detection); libraries like Matter.js for physics if collisions get complex.
* State Management: Redux for tracking map state, vehicle positions, and simulation params.
* Styling: CSS with Tailwind for responsive grids/UI.
* Build Tools: Vite 
* Testing: Jest for units
* Deployment: Github Pages

### Architecture
* High-Level Design:
    * Client-Side Only: All logic in browser for offline play.
    * Modules:
        * MapGenerator: Create initial field with highways and crossing; handle user edits (2D grid array for tiles: road=1, signal=2, etc.).
        * Renderer: Isometric projection (math for 2D-to-iso coords); draw tiles, vehicles as sprites.
        * Simulator: Game loop (requestAnimationFrame) for spawning, moving vehicles, checking jams.
        * VehicleAI: Classes for vehicles (position, speed, path, intent); random generation.
        * UIController: Modes toggle (build vs. sim), tool palettes, buttons.
    * Data Flow: Central state store for grid and entities; events trigger renders/updates.
    * Isometric Handling: Use tile-based system; sort draw order for depth (e.g., back-to-front).
    * Simulation Logic: Time-based spawning (interval increases density); pathfinding ensures vehicles navigate user-built paths.
```