# Starship Troopers Terran Command Terrain Tool (STTC-TT)

## A lightweight, browser-based utility for generating and editing terrain maps for *Starship Troopers: Terran Command* custom scenarios.

This tool allows you to:
- Convert heightmap images into playable terrain
- Load and modify existing `map.json` and `scenario.json` files
- Adjust terrain types, elevation levels, and edge styles
- Preview results in real-time with histograms and tile-based visuals
- Export ready-to-use `map.json` and updated `scenario.json` files

> This tool is not officially supported nor endorsed by The Artistocrats or Slitherine.

> Use this tool at your own risk. There is no guarantee it won't eat your map/scenario file. Definitely back your scenario up before using the tool on it.

## Features

### Image to Terrain Conversion
- Import PNG, BMP, or JPEG heightmaps
- Automatic resampling to 128x128
- Configurable quantization (2-15 levels) and elevation mapping
- Dark values represent low terrain; bright values represent high terrain

### Map and Scenario Editing
- Load `map.json` to modify existing landscapes
- Automatic `LandscapeId` syncing when `scenario.json` is loaded
- Support for all in-game biomes including Desert, Lava, Space Station, and Metro (plus Underground variants)

### Terrain and Level Control
- **Modes:** Default single terrain, Low/High overrides, or per-level assignment
- **Edge Remapping:** Batch-convert map edges to specific styles (e.g., Cliffs_Lava, Cliffs_Purple)
- **Modifications:** Shift entire maps up/down, clamp extremes, or adjust specific level bands
- **History:** 10-step Undo/Redo and state reset

### Export and Analysis
- Visual tile preview and elevation distribution histogram
- Real-time stats for total tiles and level ranges
- Export validated `map.json` and updated `scenario.json`

---

## Usage

### 0. Download
- Download the source code in your preferred format
- Open `STTCTT.html` in your favourite browser (tested in Chrome)

### 1. Load a Source
- Drop or load a heightmap image or an existing `map.json`.
- Optionally load a `scenario.json` to sync the `LandscapeId`.

### 2. Adjust Terrain
- Select the landscape type and configure terrain behavior (Default, Overrides, or Per-Level mapping).

### 3. Modify Levels
- Use level tools to shift elevation, clamp extremes, or refine specific bands.

### 4. Export
- Preview the JSON and export your files to the scenario folder.

**Default scenario path:**
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
### scenario.json
```json
{
  "LandscapeId": 0
}
```

### Notes:
 - Internal level range is 0-14 (mapped to editor levels -1 to 13)
 - Terrain edge styles are derived from TerrainTypeId
 - Some terrain blends may not have exact equivalents when remapping edges

### Limitations:
 - Fixed map resolution: 128x128 only
 - No in-engine validation: Load your map to clean it up
 - Browser-based: no file system integration beyond downloads
 - Tested in Chrome, stavle builds will be tested in a few browsers (e.g. Firefox, Edge)

## Known Issues:
- Outside corner edges may not be generated
- Edges are presented as linked to terrains, this not the case
- All image imported maps default to desert biome

## Change Notes:
 - Edge selection no longer modifies preview
 - Imported image, preview and generated map have same orientation
 - Edges applied to elevations
 - Switch between terrain colours and heightmap preview 
 - Icon created
 - Option to include debug STTC-TT information embedded in map.json
 - Improve preview performance
 - Decouple edges from terrain selection
 - Default TerrainTypeId set to --no change--
