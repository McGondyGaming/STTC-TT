# STTCTT Roadmap

A living document for tracking ideas, improvements, and future direction for the terrain tool.

---

## Current Focus

---

## Ideas

### Exports
- [ ] Export greyscale heightmap
- [ ] Add "export directly to game folder" option
- [ ] Allow selecting export directory
- [ ] Add confirmation or diff view before export if overwiting

### Preview
- [ ] Manual toggle between height and terrain views
- [ ] Show tile coordinates on hover
- [ ] Zoom / inspect specific tiles
- [ ] Colourblind accessibility options
- [ ] Level -1 render as water in preview (with terrain underlay) - toggleable?
- [ ] Terrain traversability overlay
- [ ] Terrain traversability (including blocking decors) overlay
    
### Generation
- [ ] Noise (Perlin/Simplex) generator for quick prototyping
- [ ] Map orientaion controls (flip, invert, rotate)

### Scenario integration 
- [ ] Map-wide decor orientation controls (flip, rotate)

---

## Technical Improvements

Under-the-hood changes

- [ ] Improve undo/redo efficiency (diff-based instead of full copy)
- [ ] Add basic automated tests for core functions

---

## Done

Completed items

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
