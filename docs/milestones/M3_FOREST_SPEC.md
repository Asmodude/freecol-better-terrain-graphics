# M3 Forest graphics — renderer-verified implementation specification

## Accepted baseline
- The released M2 open-terrain graphics (`v0.2.0`) are frozen. Keep their bytes unchanged.
- Develop only on `feature/forests`; the internal FreeCol mod ID stays `better_terrain_graphics_grassland_m1`.
- No changes to FreeCol's Java renderer or gameplay rules.

## Source-verified image selection

Based on current upstream `src/net/sf/freecol/client/gui/ImageLibrary.java` and `src/net/sf/freecol/client/gui/mapviewer/TileViewer.java`:

1. **Basic forest image:** `image.tileforest.model.tile.<forestType>` is rendered on forest tiles without a river style.
2. **River masks:** When a forest tile has a river style, the renderer tries `image.tileforest.model.tile.<forestType>.s<4-bit-river-mask>`. If missing, it **falls back** to the basic forest image. A `0000` river mask is substituted with `0100` (map-editor visibility).
3. **Forest corners:** On some nonforested tiles, at high graphics quality, four optional `.n`, `.s`, `.e`, `.w` corner images are used where adjacent neighbouring tiles have the same forest type. These create smoother forest edges.
4. The forest image is bottom-aligned at `tileHeight - forestImage.height`; source artwork must respect this anchor and transparent canvas geometry.
5. The forest is drawn above overlays and lower-z-index tile items but below remaining higher-z-index items, so units, rivers, improvements and surrounding items require gameplay testing.

**Correction to initial planning:** the 16 `s####` variants are **river-style variants, not 16 forest-to-forest neighbour connectivity variants**. Forest-neighbour continuity is handled in part by the directional corner images.

## Resource inventory

Eight families are mapped upstream, each with **20 image keys**: one basic forest image, four directional corner images, and fifteen `s####` river-mask images (the `0000` form is not a separate mapped image).

- tropicalForest — tropical
- wetlandForest — wetland
- scrubForest — scrub
- broadleafForest — broadleaf
- borealForest — boreal
- coniferForest — conifer
- mixedForest — mixed
- rainForest — rain

Ground textures for forests are mapped separately: broadleaf→prairie, conifer→grassland, mixed→plains, tropical→savannah, boreal→tundra, rain→swamp, wetland→marsh, scrub→desert.

## First playable prototype — broadleaf

**Stage A: Geometry and resource inspection**
1. Inspect original broadleaf image(s) for pixel dimensions and transparency against FreeCol's tile canvas/anchor.
2. Establish art direction: temperate broadleaf foliage, coherent scale and season-neutral colours matching M2.
3. Create one new `broadleaf.png` basic forest image with no river handling changes.
4. Override only its single resource key in the feature mod, using current original river-mask and corner images as fallbacks.
5. Test in FreeCol on a mixed map: forest tiles without rivers, river-crossed forest tiles, and edges in high-quality mode.

**Stage B: Connected forest package**
6. Replace four edge/corner images, measuring whether adjacent woods read as connected.
7. Design the 15 river-mask forest variants preserving river visibility and correct tree clearance, testing every mask.
8. Check grid on/off, zoom, fog-of-war, unit/resource visibility and performance.
9. Accept broadleaf only from in-game evidence. Then generalize to remaining forest families.

## Non-regression
- Verify all accepted M2 image hashes match `docs/milestones/M2_files_sha256.json`.
- Avoid changing other approved artwork.
- Test real FreeCol savegames rather than treating artificial tile sheets as acceptance.

## Upstream sources
- https://github.com/FreeCol/freecol/blob/master/src/net/sf/freecol/client/gui/ImageLibrary.java
- https://github.com/FreeCol/freecol/blob/master/src/net/sf/freecol/client/gui/mapviewer/TileViewer.java
- https://github.com/FreeCol/freecol/blob/master/data/default/resources.properties
