# M2 acceptance — Open Terrain

**Accepted:** 2026-10-25

**Deliverable:** five terrain families; five variants per family; native and 4× PNG resources, plus FreeCol mod metadata.

Accepted versions:
- Grassland V3 — richer green
- Prairie V3 — golden-green
- Savannah V3 — less visually dominant vegetation
- Plains — warm muted baseline
- Desert V3 — light sand with sparse scrub

User acceptance occurred after actual FreeCol gameplay tests in an existing save. The mod persisted using internal identifier `better_terrain_graphics_grassland_m1`. Older saves may store an empty mods list; savegame modification was required once for the test save.

**Preservation:** do not change accepted image bytes during GitHub import. Track asset checksums in `docs/milestones/M2_SHA256_manifest.json` when importing binaries.

**Migration:** This text can be committed separately from the binary artwork. Do not label the repository's contents a complete installable mod until assets are uploaded and checksums verified.

**Outstanding:** visual contrast of some resource icons, particularly tobacco; separate future milestone.
