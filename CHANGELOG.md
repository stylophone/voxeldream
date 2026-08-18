# Changelog

This file records public VoxelDream releases. Releases are listed in reverse
chronological order.

## v0.1.1-beta.1 — Unreleased

- Added Voxel Shapes in World Mode, beginning with resizable Box and Sphere
  primitives. Shapes can be adjusted before entering Voxel Mode for detailed
  editing, and the Shapes menu is designed to support more primitives in future
  updates.
- Improved World Mode workspace bounds visualization so it remains stable when
  objects are selected, respects normal scene depth, and avoids flickering
  where workspace boundaries overlap voxel meshes.
- Fixed the Stairs tool so the requested steps divide the full selected height,
  instead of always making the lowest step only one voxel high.

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
