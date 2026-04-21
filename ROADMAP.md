# STTC-TT Roadmap

A living document for tracking ideas, improvements, and future direction for the terrain tool.

---

## Current Focus

- [ ] Selections in preview
- [ ] Rotate preview to match game (45° CW)

---

## Ideas

### Exports

- [ ] Export greyscale heightmap
- [ ] Allow selecting export directory
- [ ] Add confirmation or diff view before export if overwiting

### Preview

- [ ] Terrain traversability preview (including blocking decors) overlay
- [ ] Level -1 render as water preview overlay
    
### Generation

### Scenario integration 

- [ ] Map-wide decor orientation controls (flip, rotate)
- [ ] Map-wide unit orientation controls (flip, rotate)
- [ ] Map-wide trigger orientation controls (flip, rotate)

---

## Technical Improvements

- [ ] Option to load terrain/edge data from gamefiles *or* use embedded values
- [ ] Host multiple versions
- [ ] Improve undo/redo efficiency (diff-based instead of full copy)
- [ ] Add basic automated tests for core functions

---

## Done

Completed items

- [x] Colourblind accessibility options
- [x] Selectable colours (high, medium, low + interpolated levels)
- [x] Show tile coordinates on hover
- [x] Zoom / inspect specific tiles
- [x] Terrain traversability preview overlay
- [x] Undo/redo action list/History
- [x] Noise (Perlin/Simplex) generator for quick prototyping
- [x] Map orientaion controls (flip, invert, rotate)
- [x] Manual toggle between height and terrain views
- [x] Image → heightmap conversion
- [x] map.json import
- [x] Terrain assignment modes
- [x] Edge remapping system
- [x] Undo / redo system
- [x] Live preview + histogram
- [x] Improve testing workflow (test packs + repeatable process)
- [x] Validate edge remapping behaviour across all landscapes
- [x] Fix any inconsistencies in terrain assignment logic
- [x] Map vertical flip (in tool and game)
---

## Notes

- Keep scope aligned with actual usage (map creation + tweaking)
- Avoid overbuilding features that don't translate to in-game value
- Prioritise anything that reduces iteration time
