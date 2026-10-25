# M3 Forest assets — implementation specification (draft)

## Baseline
Start from the accepted M2 release. Do not change open-terrain PNG bytes in M3.

## Renderer/resource inventory
The default FreeCol `resources.properties` provides 20 image resource mappings for each of:
- tropicalForest
- wetlandForest
- scrubForest
- broadleafForest
- borealForest
- coniferForest
- mixedForest
- rainForest

Forest artwork is not equivalent to five center-tile variations: named edge/direction variants and 4-bit connectivity combinations (e.g. `s0001` through `s1111`) must match the renderer's actual selection logic.

Ground textures underlying forest families reuse open terrain mappings (e.g. broadleaf → prairie; conifer → grassland; tropical → savannah). Preserve these relationships unless actual gameplay requires a change.

## First implementation: broadleaf forest
1. Inspect `TileViewer`, the relevant image selectors and existing broadleaf PNG dimensions/alpha.
2. Record exact meanings of the directional and connectivity suffixes; verify drawing order and how forest edges connect.
3. Generate a consistent broadleaf visual direction aligned with approved M2 artwork.
4. Create the *full required resource set*, not just a demonstration center image.
5. Package in the same mod folder / unchanged ID; test in FreeCol with roads, rivers, coastline, hills, units, and settlements.
6. Evaluate grid enabled/disabled and screen-scale readability.
7. Freeze only after a gameplay screenshot is accepted.

## Non-regression
- Compare every M2 image SHA-256 against `docs/milestones/M2_files_sha256.json`.
- Do not change existing approved files.
- No Java code changes.
- Keep forest artwork on `feature/forests` until approved.

## Initial acceptance criteria
- Contiguous woodland reads as connected trees rather than isolated repeated clusters.
- Edges/corners appear correct across different neighboring forest configurations.
- Units/colonies/resources remain legible.
- No missing-asset placeholders, dark alpha seams, or broken zoom scaling.
