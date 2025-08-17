# RPG Game Board

Canvas-based, zero-dependency tabletop map editor for quick RPG encounters. Paint terrain, place/drag entities, use battleship-style coordinates, and save/load maps as JSON.

## Features
- **Interactive grid** with zoom, pan, and fit-to-screen.
- **Terrain painting**: `wall` (blocks placement/movement), `trap` (marker), `hole` (z–), `platform` (z+).
- **Z-levels** per cell (shows as `z#`), adjustable increment rate.
- **Entities**: add from icon set, random placement to valid cells, drag to move (can’t enter walls).
- **Undo** stack (compact history).
- **Save/Load** board state to/from JSON.
- **Coordinates**: column A… / row 1… labels; top-left is **A1**.
- **Info page** at `/info/` with a full user guide.
- **Responsive** sidebar; extra bottom spacer for easier scroll.

## Quick Start
1. Serve the folder (any static server works). Examples:
   - Python: `python -m http.server 8000`
   - Node: `npx serve`
2. Open `http://localhost:8000/` and start building.
3. Use the sidebar to pick **Terrain** or an **Entity**, then click the board.

> Tip: If you open `index.html` directly via `file://`, some browsers restrict paths; a tiny local server avoids issues.

## Usage
- **Add Entity**: picks the currently selected entity type and places it on a random valid cell.
- **Drag** entities to reposition; movement into `wall` cells is blocked.
- **Terrain painting**: click cells with a selected terrain type.
- **Cell Editor**: press **`E`**, then click a cell to edit Entity type/ID and Terrain/Z; use **Apply**.
- **Controls (top-right)**:
  - ⎌ Undo
  - `+` / `−` Zoom
  - `=` Fit to screen
  - 💾 Save (downloads JSON)
  - 📂 Load (imports JSON)
  - Arrow buttons Pan the view

## Save File Format (JSON)
```json
{
  "gridWidth": 8,
  "gridHeight": 8,
  "entities": [
    { "type": "wizard", "x": 3, "y": 4, "id": 1723598765123, "outline": "#FF00AA" }
  ],
  "terrain": [
    { "x": 1, "y": 2, "type": "wall", "z": 0 },
    { "x": 4, "y": 5, "type": "platform", "z": 2 }
  ]
}

