# Changelog

This file records public VoxelDream releases. Releases are listed in reverse
chronological order.

## v0.1.3-beta.1 — 2026-08-27

- Improved the World Mode terrain, maze and dungeon, and building generators so
  generated assets can restore their settings and be updated or rebuilt in place.
- Added `Add Face` and `Fill Depth` options to the Face tool in Create mode.
  `Add Face` adds one voxel layer across the connected clicked surface, while
  `Fill Depth` extends that same face footprint along its normal until each
  column reaches an existing voxel or the finite Voxel Space boundary.
- Added continuous Face tool strokes in Select, Paint, and Erase modes. Holding
  and dragging across multiple faces previews the combined operation and commits
  it as a single undoable edit when the pointer is released. Create mode remains
  click-based to prevent accidental repeated extrusion.
- Added binary STL export through **File → Export → STL**. Multiple selected
  scene objects can be combined into one STL, with an adjustable physical voxel
  edge length in millimetres and a live preview of export dimensions and triangle
  count.
- Significantly improved the first save of large VOXPROJ projects by removing
  redundant hashing and processing voxel assets in parallel. A 1.15 GiB test
  project now saves in about 4.5 seconds instead of 22 seconds, without changing
  the project format or compression results.
- Significantly improved opening large VOXPROJ projects through parallel package
  validation, reuse of verified asset fingerprints and duplicate meshes, and a
  compact VVOX-to-greedy-mesh path that avoids redundant full-voxel conversions
  and material scans. The same test project now opens in about 4.9 seconds instead
  of 19.7 seconds while retaining complete validation before the current scene is
  cleared.
- Introduced VVOX v5 with compact workspace-local coordinates and adaptive
  X-span/palette records, substantially reducing large regular voxel assets while
  retaining linear-time read and write behavior. Existing VVOX v3/v4 files remain
  readable; exporting them or resaving a VOXPROJ project upgrades the stored voxel
  assets to v5.

Release: <https://github.com/stylophone/voxeldream/releases/tag/v0.1.3-beta.1>

## v0.1.2-beta.1 — 2026-08-23

- Added Photoshop-style `Shift` ordering to Voxel Mode shape tools. Holding
  `Shift` after a Box, Sphere, Cylinder, Pyramid, Prism, or Stairs drag begins
  constrains the starting-plane axes to equal spans, while holding it before
  the drag continues to add to the current selection.
- Improved the color palette so it remembers the last paint color used and
  restores it across window reopenings and application restarts. New users, or
  users with no saved color preference, still start with the default pink.
- Fixed the center Scale handle in Voxel Mode so it resizes selections
  proportionally on all three axes instead of applying unrelated per-axis
  changes based on the camera angle.
- Fixed World Mode workspace bounds visualization so voxel workspaces moved in
  Voxel Mode are displayed at their saved offset instead of at the original
  zero-origin position.
- Fixed Rect tool edits after moving the Voxel Mode workspace a long distance.
  Chunk-cache hash collisions could previously write voxels outside the
  workspace bounds and cause the saved voxel source data to be rejected when
  entering Voxel Mode again.
- Fixed Detach after moving the Voxel Mode workspace. Detached voxel content
  and its new workspace bounds could previously appear far apart because the
  source workspace origin was not normalized into the detached asset.
- Improved performance when creating and rebuilding large voxel assets by
  optimizing VVOX serialization and World Mode greedy meshing.

Release: <https://github.com/stylophone/voxeldream/releases/tag/v0.1.2-beta.1>

## v0.1.1-beta.1 — 2026-08-22

- Added optional Smooth Refine when detaching a Voxel Mode selection at 2× or
  higher detail. It smooths the subdivided voxel silhouette while approximately
  preserving volume; exact block subdivision remains the default for hard-edged
  models and thin details.
- Added Region Selection in Voxel Mode for selecting spatial areas independently
  of their current contents. Selected regions can be filled with the active voxel,
  recolored or assigned a different material, or cleared while remaining selected.
- Added a Ruler outline mode in Voxel Mode. It keeps individual voxel edges
  visible while emphasizing major lines at the configurable voxel grid cell
  interval, helping users measure proportions and align larger models.
- Added Voxel Shapes in World Mode, beginning with resizable Box and Sphere
  primitives. Shapes can be adjusted before entering Voxel Mode for detailed
  editing, and the Shapes menu is designed to support more primitives in future
  updates.
- Improved World Mode workspace bounds visualization so it remains stable when
  objects are selected, respects normal scene depth, and avoids flickering
  where workspace boundaries overlap voxel meshes.
- Fixed the Stairs tool so the requested steps divide the full selected height,
  instead of always making the lowest step only one voxel high.

Release: <https://github.com/stylophone/voxeldream/releases/tag/v0.1.1-beta.1>

## v0.1.0-beta.2 — Unreleased

- Improved Minecraft Bedrock Add-On export so solid-color custom blocks and
  stair structures stay aligned with the corresponding China Edition export.
- Added English and Simplified Chinese footer tooltips for the main editor
  controls. Hover guidance appears temporarily in the footer without being
  added to the Console log.
- Added complete English and Simplified Chinese user guides.

## v0.1.0-beta.1 — 2026-08-12

The first public release of VoxelDream, published as a Very Early Beta.

- Introduced the first publicly downloadable macOS builds for Apple Silicon and
  Intel Macs.
- This early release may contain bugs, unfinished features, and changes to
  project files. Back up important work before using it.
- The macOS applications are currently ad-hoc signed and are not notarized by
  Apple. macOS may require users to allow the application manually from
  **System Settings → Privacy & Security** after the first launch attempt.

Release: <https://github.com/stylophone/voxeldream/releases/tag/v0.1.0-beta.1>
