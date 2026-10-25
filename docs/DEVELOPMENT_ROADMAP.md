# Development roadmap

## M2 — Open terrain (accepted)

Grassland V3, Prairie V3, Savannah V3, Plains warm revision and Desert V3. Twenty-five variants, two resolutions each. Tested and approved visually in a running FreeCol game. Keep the accepted archive and SHA-256 manifest for comparison.

## M3 — Forests (next)

1. Document the forest resource families and the connected-mask render logic.
2. Choose a representative family (broadleaf) and create a full working visual set.
3. Compare adjoining forest tiles, edges, roads, rivers, and unit/settlement visibility in FreeCol.
4. Extend approved styling to remaining forest types.
5. Package and verify without overwriting the M2 approved open terrain.

The upstream default resource mapping names eight forest families: broadleaf, conifer, mixed, tropical, boreal, rain, wetland, scrub. There are 20 mapping keys per family. Verify actual renderer usage and images before generating replacements.

## Later milestones

- M4: hills and mountains
- M5: water, coastlines and terrain improvements
- M6: full integration, gameplay test matrix, release candidate
- Resource icon readability is a tracked separate improvement.

## Release controls

- Each milestone gets a manifest and an immutable archive.
- Only tested, accepted work goes onto `main`.
- Feature work stays in branches.
- Follow the same internal mod ID so existing FreeCol savegame references remain valid.
