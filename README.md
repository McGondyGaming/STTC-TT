# Starship Troopers Terran Command Terrain Tool (STTC-TT)

## A lightweight, browser-based utility for generating and editing terrain maps for *Starship Troopers: Terran Command* custom scenarios.

This tool allows you to:
- Convert heightmap images into playable terrain
- Load, modify and export existing `map.json`, `scenario.json` files
- Load, modify and export entire scenario folders
- Generate a starter landscape using Perlin or Simplex deterministic algorithms
- Adjust terrain orientation, types, elevation levels, and edge styles
- Preview results in real-time with histograms and tile-based visuals

> This tool is not officially supported nor endorsed by The Artistocrats or Slitherine.

> Use this tool at your own risk. There is no guarantee it won't eat your map/scenario file. Definitely back your scenario up before using the tool on it.

## Special Thanks
- Thank-you to the dedicated STTC community for providing feedback, especially `Finding Pudge` and `Lionstein` 

## Features

### Image to Terrain Conversion
- Import PNG, BMP, or JPEG heightmaps
- Automatic resampling to 128x128
- Configurable quantization (2-15 levels) and elevation mapping
- Dark values represent low terrain; bright values represent high terrain

### Map and Scenario Editing
- Load `map.json` to modify existing landscapes
- Load entire scenario folders to modify lanscapes, DLC dependencies, and biomes/landscapes
- Automatic `LandscapeId` syncing when `scenario.json` is loaded
- Support for all in-game biomes including Desert, Lava, Space Station, and Metro (plus Underground variants)

### Generator
- Modify the seed to dramatically change the layout
- Move sliders to finesse

### Terrain and Level Control
- **Modes:** Default single terrain, Low/High overrides, or per-level assignment
- **Edge Remapping:** Batch-convert map edges to specific styles (e.g., Cliffs_Lava, Cliffs_Purple)
- **Modifications:** Shift entire maps up/down, clamp extremes, or adjust specific level bands
- **History:** 50-step Undo/Redo and state reset

### Analysis and Export
- Visualise tile, height, navigability and heatmap previews
- Elevation distribution histogram
- Real-time stats for total tiles and level ranges
- Export new or updated `map.json`, update existing `scenario.json` or `header.json` files or even entire scenario folders
- Export optional backup `*.bak` files 
- Export an optional `STTC-TT.json` file containing debugging information

---

## Usage

### 0. Download or Access
- If downloading, choose the source code in your preferred format
- Open `index.html` in your favourite browser (currently only tested in Chrome)
 - Alternatively, navigate to https://mcgondygaming.github.io/STTC-TT/ 

### 1. Select a Source
- Drop or load a heightmap image *or* an existing `map.json` *or* scenario folder *or* generate a new layout
- If loading a `map.json`, optionally load a:
 - `scenario.json` to sync the `LandscapeId` ("biome").
 - `header.json` to sync the DLC requirements
 - `text_<language>.csv` to display scenario title - slected language based on browser settings, fallback to english -> any available -> null

### 2. Adjust Terrain and Edges
- Select the landscape type and configure terrain and edges (Default, Overrides, or Per-Level mapping).

### 3. Modify Orientation
- Rotate or Flip the entire terrain
  - Does not include Units, Decor or Triggers (yet)

### 4. Use Level Tools
- Use level tools to shift elevation, clamp extremes, or refine specific bands.

### 5. Settings
- Adjust UI and Preview colour schemes

### 6. History
- Navigable history list
  - Click on the point you would like to return to
  - Taking an action wipes the previous history

### 7. Export
- Export the current heightmap as `heightmap.png`
- Preview the JSON and export your files to the scenario folder.
  - Optionally export backup `*.bak` files
  - Optionally export all as `*.zip` file
  - Optionally export `STTC-TT.json` debug file
  - Multiple downloads will likely prompt to "Allow download of multiple files"

**Default scenario path:**
`%USERPROFILE%\Documents\My Games\Starship Troopers\Scenarios`

---

## Exported Data Format

### Option: Export `STTC-TT.json` for diagnositc purposes. The following data is captured:
 - STTC-TT version
 - Source
 - Generation data (if used)
 - Tile and Edge selections and number
 - Level ranges
 - Undo depth and history
 - Map orientation state and changes

### Option: Export `*.bak` files 
 - Snapshot of previous `*.json` files 

### Heightmap
- Current preview exported as `heightmap.png`
- Greyscale
- 128 x 128 pixels

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
...}
```

### scenario.json
```json
{...
  "LandscapeId": 0
...}
```

### header.json
```json
{...
  "DLCs": [
    1 //Base game
    2 //Raising Hell
    4 //Urban Onslaught
  ]
}
```

---

### Notes:
 - Internal level range is 0-14 (mapped to editor levels -1 to 13)
 - Terrain edge styles are derived from TerrainTypeId
 - Some terrain blends may not have exact equivalents when remapping edges

### Limitations:
 - Fixed map resolution: 128x128 only
 - No in-engine validation - Load your map in the scenario editor to verify/clean up
 - Browser-based: no file system integration beyond uploads/downloads
 - Tested in Chrome, future builds will be tested in multiple browsers (e.g. Firefox, Edge)

## Known Issues:
- Outside corner edges may not be generated
- All image imported maps default to desert biome 
   - Suggested work around: Create scenario in offical editor -> Save and close scenario -> Load `map.json` for tweaks

## Change Notes:
 - Drag handle interacts with max preview size 
 - Drag handle between controls and preview panes - persists, reset on double clicks
 - Preview modes added + UI fixes
 - Show section pills only at appropriate data load
 - Increase max section pill width
 - Fixed undo/redo not correctly restoring orientation
 - Fixed CW/CCW rotating in wrong directions
 - Fixed loading a new image preserving rotation from previous session
 - Fixed image sliders (quantization, min/max level) wiping undo history
 - Numerous bugfixes (Edge rotations, preview caches, edge variations, export available/unsaved changes, undo depth)
 - Heatmap performance improvements
 - Customised keyboard binding for preview keyboard navigation - defaults to WASD
 - Keyboard navigation of preview (arrows move selector, shift+arrow move 5x, space/enter selects current tile)
 - Close tile inspector using `X` at section
 - Preview pane is scrollable
 - Greyscale heightmap export added
 - Fixed `scenario.json` showing outlined export (unsaved changes) immediately after loading a map
 - Loading a map now appears in the undo history, so you can undo all the way back to the original loaded state
 - Exporting a single file no longer disables the export button if you cancel the save dialog
 - Decors are now preserved when exporting `map.json`
 - Improved exported `*.json` formatting
 - Keyboard navigation and focus highlights added
 - Aria screenreader support added 
 - Heatmap and navigation colour schemes available 
 - Heightmap and UI colour schemes available, custom schemes are saved to the device
 - Rotating a map will now rotate slopes
 - Import entire scenario folders (`map.json`, `scenario.json`, `header.json`, `text_<language>.csv` - language based on browser settings, fallback to english -> any available -> null)
 - Export multiple files as zip 
 - Generator level limiter added
 - Preview mode selector now separate buttons
 - Slopes now calculate heat in the correct direction, and with greater penalties uphill
 - Heatmap scale slider
 - Slopes now differentiated from cliffs, painted separately in preview
 - Heatmap calculated using Dail's algorithm to support multiple weights in future changes (cliffs vs slopes)
 - `Tile selector` available in preview
 - `Navigability` preview introduced (red = blocked, green = open)
 - BFS transform based `Heatmap`(red = narrow, green = open, blue = wide open)
 - All sections except `Source` are collpased on load
 - `History` list implemented with meaningful entries
 - `Preview` switch simplified text, and defaults to Height
 - `Generator` actions register in undo buffer, and move slider to previous position
 - Perlin and OpenSimplex generator added
 - Terrain orientation controls (Units, Decors and Triggers are unmoved)
 - Undo buffer increased from 10 to 30 steps
 - Edge selection no longer modifies preview
 - Imported image, preview and generated map have same orientation
 - Edges applied to elevations
 - Switch between terrain colours and heightmap preview 
 - Icon created
 - Option to include debug STTC-TT information embedded in map.json
 - Improve preview performance
 - Decouple edges from terrain selection
 - Default TerrainTypeId set to --no change--
