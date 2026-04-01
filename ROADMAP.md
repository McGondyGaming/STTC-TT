# STTCTT Roadmap

A living document for tracking ideas, improvements, and future direction for the terrain tool.

---

## Current Focus

### Testing

- [ ] Improve testing workflow (test packs + repeatable process)

### Bugfixes

- [ ] Validate edge remapping behaviour across all landscapes
- [ ] Fix any inconsistencies in terrain assignment logic
- [ ] Map vertical flip (in tool and game)

---

## Ideas

### Exports
- [ ] Export greyscale heightmap
- [ ] Add “export directly to game folder” option
- [ ] Allow selecting export directory
- [ ] Add confirmation or diff view before export if overwiting

### Preview
- [ ] Manual toggle between height and terrain views
- [ ] Show tile coordinates on hover
- [ ] Zoom / inspect specific tiles
    
### Generation
- [ ] Noise (Perlin/Simplex) generator for quick prototyping
- [ ] Map orientaion controls (Flip, invert, rotate)

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

---

## Notes

- Keep scope aligned with actual usage (map creation + tweaking)
- Avoid overbuilding features that don’t translate to in-game value
- Prioritise anything that reduces iteration time
