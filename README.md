# Starship Troopers Terran Command Terrain Tool (STTCTT)

A lightweight, browser-based utility for generating and editing terrain maps for *Starship Troopers: Terran Command* custom scenarios.

This tool allows you to:
- Convert heightmap images into playable terrain
- Load and modify existing `map.json` files
- Adjust terrain types, elevation levels, and edge styles
- Preview results in real-time
- Export ready-to-use `map.json` and `scenario.json` files

> This tool is not officially supported nor endorsed by The Artistocrats or Slitherine.

---

## Features

### Image to Terrain Conversion
- Import PNG, BMP, or JPEG heightmaps
- Automatically resamples to 128×128
- Adjustable:
  - Quantization levels (2–15)
  - Min/max elevation mapping
- Dark = low terrain, bright = high terrain

### Existing Map Editing
- Load `map.json`
- Automatically detects landscape type
- Preserves original terrain data (optional)
- Automatically updates `LandscapeId` when scenario file is loaded

### Landscape Support
Supports all in-game landscape types:
- Desert
- Underground
- Desert City
- Lava
- Lava Underground
- Space Station
- Metro
- Metro Underground

Controls the `LandscapeId` used in `scenario.json`.

### Terrain Control
Multiple modes:
- Default (single terrain)
- Low / High overrides
- Per-level assignment

Options:
- Restrict to valid terrain for selected landscape
- Preserve original terrain from imported maps

### Edge (Cliff) Remapping
- Convert entire map to a different edge style:
  - Desert (Cliffs_A)
  - Underground (Cliffs_Purple)
  - Lava (Cliffs_Lava)
  - Metro/Storm (Cliffs_Storm)
  - Space Station (Spacestation_A)
- Smart fallback for unsupported terrain blends

### Level Editing Tools
- Shift entire map up/down
- Clamp low/high elevations
- Shift specific level bands
- Undo / Redo (up to 10 steps)
- Reset to original state

### Live Preview
- Tile-based visual preview
- Histogram of level distribution
- Terrain colour preview (when map loaded)
- Stats:
  - Total tiles
  - Level range
  - Non-zero tiles

### Export
- Export `map.json`
- Optionally export updated `scenario.json`
- Preview JSON before export


---

## Usage

### 1. Load a Source
Choose one of:
- Drop/Load a heightmap image
- Drop/Load an existing `map.json`

Optional:
- Drop/Load a `scenario.json` to sync the `LandscapeId`

### 2. Adjust Terrain
- Select landscape type (or use auto-detected)
- Configure terrain behaviour:
  - Default terrain
  - Overrides
  - Per-level mapping

### 3. Modify Levels (Optional)
Use level tools to:
- Shift elevation
- Clamp extremes
- Adjust specific level ranges

### 4. Preview
- Inspect terrain visually
- Check histogram and stats

### 5. Export
- Export `map.json`
- Export `scenario.json` if loaded

Default scenario path:
`%USERPROFILE%\Documents\My Games\Starship Troopers\Scenarios`

---

## Exported Data Format

### map.json
```json
{
  "Width": 128,
  "Height": 128,
  "Tiles": [
    {
      "Index": 0,
      "Level": 0,
      "Type": 0,
      "TerrainTypeId": 2
    }
  ]
}
```
### map.json
```json
{
  "LandscapeId": 0
}
```

### Notes:
 - Internal level range is 0–14 (mapped to editor levels -1 to 13)
 - Image imports always generate Type = 0
 - Terrain edge styles are derived from TerrainTypeId
 - Some terrain blends may not have exact equivalents when remapping edges

### Limitations:
 - Fixed map resolution: 128×128 only
 - No in-engine validation: Load your map to clean it up
 - Browser-based: no file system integration beyond downloads
