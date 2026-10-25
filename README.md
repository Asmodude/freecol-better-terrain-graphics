# Better Terrain Graphics for FreeCol

An independently developed graphics-only mod for [FreeCol](https://www.freecol.org/), improving terrain readability and visual quality without changes to the Java renderer or gameplay rules.

## Status

**M2 — Open Terrain: accepted in game (25 variants across five terrain families).** Assets are being migrated into this repository from the approved milestone archive. Until the PNG files appear under `mod/`, **this repository alone is not yet an installable mod**.

| Terrain | Status |
| --- | --- |
| Grassland V3 | Accepted |
| Prairie V3 | Accepted |
| Savannah V3 | Accepted |
| Plains (warm revision) | Accepted |
| Desert V3 | Accepted |
| Forests | M3 — planned |

## Installable mod layout

The distributable FreeCol mod folder is `better_terrain_graphics_grassland_m1` inside `mod/`. Copy that entire folder into your FreeCol user mods directory. Enable the mod in FreeCol.

**Compatibility:** The internal mod ID `better_terrain_graphics_grassland_m1` is intentionally retained from initial tests so existing savegames referring to that ID continue to load the textures. The internal name is historical; the mod covers more than grassland.

Older FreeCol saves can restore their own list of active mods when loaded. Back up saves before modifying them. New saves made with the mod active may retain it automatically.

## Development and releases

- `main`: tested, accepted baseline.
- `feature/forests`: M3 development; no accepted-asset changes without specific justification.
- First intended milestone version: `v0.2.0` (after the accepted binaries are committed and verified).

Read [art direction](docs/ART_DIRECTION.md), [roadmap](docs/DEVELOPMENT_ROADMAP.md), and [M2 acceptance](docs/milestones/M2_OPEN_TERRAIN.md).

## License and provenance

**License review pending.** Some artwork was generated or transformed during development, and the package's compatibility with FreeCol includes resource naming and layout conventions. Redistribution terms and any attribution obligations must be confirmed before attaching an open-source license. Do not assume this repository is licensed for unrestricted reuse.

This project is not affiliated with the FreeCol development team.
