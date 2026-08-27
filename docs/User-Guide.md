# VoxelDream User Guide

[简体中文](User-Guide.zh-CN.md)

> This guide reflects the menus, interface, and behavior of the current VoxelDream build. It is written for first-time users. Experimental features are identified explicitly.

## 1. What is VoxelDream?

VoxelDream is a discrete-space 3D modeling system built around editable voxel source data. You can place, remove, and modify blocks to create characters, props, buildings, decorations, and game assets.

Its finite, integer-aligned workspaces support purpose-built algorithms for connected regions, modeling tools, selection transforms, generators, compact storage, and mesh reconstruction. You do not need to understand those implementation details to use the editor, but they make voxel editing more than a visual style.

It is designed to help you:

- create voxel models from scratch;
- import voxel files or images and continue editing them;
- adjust a model's color, shape, proportions, and placement;
- save projects that remain fully editable;
- export finished objects as FBX meshes or Minecraft Add-Ons.

You do not need to understand topology, UVs, normals, or rigging before you begin. A typical workflow is:

```text
Create or import → Edit voxels → Shape, paint, and erase → Return to World mode → Save → Export
```

## 2. World mode and Voxel mode

VoxelDream has two main editing modes.

### World mode

World mode manages complete objects in a scene. Use it to:

- create and arrange multiple voxel objects;
- select, move, rotate, and scale objects;
- organize objects in the Hierarchy;
- duplicate or delete complete objects;
- import VVOX files or images;
- save and open projects;
- export FBX meshes or Minecraft Add-Ons.

Think of World mode as the place where you arrange and manage complete models.

### Voxel mode

Voxel mode edits the individual blocks inside one voxel object. Use it to:

- add and select voxels;
- change voxel colors or materials;
- erase voxels;
- use line, box, sphere, cylinder, and other modeling tools;
- move, rotate, and scale a selected group of voxels;
- adjust the voxel workspace size.

Think of Voxel mode as entering a model to edit its details. A scene can contain many voxel objects, but only one object is edited at voxel level at a time. Other objects remain visible as references.

### Interface icon reference

| Icon | Meaning | Icon | Meaning |
| --- | --- | --- | --- |
| ![Voxel editing](images/icons/voxel_edit.svg) | Switch World / Voxel mode | ![Focus](images/icons/focus.svg) | Focus the current content |
| ![Select](images/icons/select.svg) | Select mode | ![Create](images/icons/create%201.svg) | Create mode |
| ![Paint](images/icons/color.svg) | Paint mode | ![Erase](images/icons/erase.svg) | Erase mode |
| ![Hand](images/icons/hand.svg) | Hand / view | ![Move](images/icons/move.svg) | Move |
| ![Rotate](images/icons/rotate.svg) | Rotate | ![Scale](images/icons/scale.svg) | Scale |
| ![Undo](images/icons/undo.svg) | Undo | ![Redo](images/icons/redo.svg) | Redo |

## 3. Create your first model

### Step 1: Create a project

Choose `File > New`.

If the current project contains unsaved changes, VoxelDream asks whether to save them. Projects use the `.voxproj` extension.

### Step 2: Create a voxel object

In World mode, choose `Object > Create Voxel Object`. The new object appears in the scene and Hierarchy and becomes selected.

### Step 3: Enter Voxel mode

With the voxel object selected, press `Enter` or click the mode button in the top bar.

The editing grid remains level, regular, and axis-aligned. If the object was rotated or scaled in World mode, the voxel grid itself does not become tilted or distorted.

### Step 4: Add voxels

Choose Create mode in the left toolbar, select the Pen tool, then click or drag in the scene to place voxels. Begin with a rough outline and use tools such as Box or Sphere to add larger forms quickly.

### Step 5: Paint and refine

- Use Paint mode to change the color or material of existing voxels.
- Use Erase mode to remove voxels.
- Use Eyedropper to sample an existing voxel's color or material.
- Use Select mode to select part of the model, then move, rotate, or scale it.

### Step 6: Return to World mode

Press `Esc` or click the mode button in the top bar. If a cancellable voxel selection exists, the first press of `Esc` cancels it; press `Esc` again to leave Voxel mode.

When you exit, VoxelDream commits the voxel content to the object and updates the mesh used for display and export. Large models may take a moment.

### Step 7: Save

Choose `File > Save`, or press:

- macOS: `Command + S`
- Windows: `Ctrl + S`

An unnamed project opens the Save As flow.

## 4. The four voxel operation modes

The tool determines the shape of an operation; the mode determines what that operation does.

### Select

Select existing voxels for moving, rotating, scaling, copying, deleting, recoloring, or detaching. A selection can become a floating selection; commit its transform before beginning another operation or leaving Voxel mode.

### Create

Add voxels to empty cells using the current color or material.

### Paint

Change the color or material of existing voxels without changing the model's shape.

### Erase

Remove voxels covered by the active tool. For large shape operations, check the preview before releasing the mouse button.

Use the number keys in Voxel mode:

- `1`: Select
- `2`: Create
- `3`: Paint
- `4`: Erase

## 5. Voxel tools

The left toolbar shows the tools available for the current operation mode. Some buttons can be held or expanded to choose another shape in the same group.

With Box, Sphere, Cylinder, Pyramid, Prism, or Stairs, begin dragging first and then hold `Shift` to keep the two directions on the starting surface at equal spans. This makes it easy to draw squares, circles, and proportional cross-sections; release `Shift` to return to free proportions. In Select mode, holding `Shift` before pressing the mouse button still adds to the selection. If you begin an additive selection with `Shift`, release it and press it again during the drag to enable the proportional constraint.

### Pen

The basic point-by-point tool. Use it for details, repairs, painting, and local erasing. Click and drag for a continuous stroke.

### Line

Drag from a start point to an end point to create a continuous line. It is useful for edges, rods, and beams.

### Rect

Drag a rectangular region on screen or on the work plane. In Select mode it selects voxels; in other modes the current operation is applied to the region.

### Box

Drag a cuboid region. Create mode supports solid or shell forms and rounded or chamfered corners. Select, Paint, and Erase apply their operation to occupied voxels in the same region.

### Face

Operate on a connected surface starting from the clicked face. It is useful for selecting, painting, or cleaning a continuous surface.

In Create mode, choose one of the Face options in the top bar:

- **Add Face** adds one voxel layer across the connected clicked surface.
- **Fill Depth** starts with the same connected face footprint, then fills each
  cell along the face normal until that column reaches an existing voxel or the
  finite Voxel Space boundary. Open space is filled to the boundary; it is not
  treated as an infinite exterior.

These options affect only Create mode, which remains click-based. In Select,
Paint, and Erase modes, click a face for a single connected-surface operation,
or hold the mouse button and drag across multiple faces to combine them into one
operation. The combined operation is committed as one undoable edit when the
mouse button is released.

### Sphere

Create a sphere or ellipsoid inside the dragged bounds, either solid or as a shell.

### Cylinder

Create a cylinder within a chosen extent and direction. It is useful for columns, wheels, and pipes.

### Pyramid and Prism

Build slopes, roofs, pointed forms, and regular prisms quickly.

### Stairs

Generate a staircase from the drag direction and bounds.

### Magic Wand

Select or erase voxels according to color similarity. Connected mode follows only matching adjacent voxels; All Matching searches the complete workspace. Tolerance controls how similar colors must be.

### Paint Bucket

Fill a matching region quickly. It is useful for large color changes.

### Eyedropper

Click an existing voxel to sample its color or material, then continue with Pen or another tool.

### Tool icon reference

| Icon | Tool | Main use |
| --- | --- | --- |
| ![Pen](images/icons/modeling/pen.svg) | Pen | Point or continuous stroke editing |
| ![Line](images/icons/modeling/line.svg) | Line | Build a continuous segment between two points |
| ![Rect](images/icons/modeling/rect.svg) | Rect | Drag a rectangular operation region |
| ![Face](images/icons/modeling/face%20%282%29.svg) | Face | Add one surface layer or fill its depth in Create mode; process a connected surface in other modes |
| ![Magic Wand](images/icons/magic_wand.svg) | Magic Wand | Match voxels by color and connectivity |
| ![Paint Bucket](images/icons/paint_bucket%20%281%29.svg) | Paint Bucket | Fill a region quickly |
| ![Eyedropper](images/icons/eyedropper%202.svg) | Eyedropper | Sample an existing voxel's appearance |

Shape tools have outline and volume variants:

| Shape | Outline icon | Volume icon |
| --- | --- | --- |
| Box | ![Box outline](images/icons/shapes/cube_outline.svg) | ![Box volume](images/icons/shapes/cube_solid.svg) |
| Sphere | ![Sphere outline](images/icons/shapes/sphere_outline.svg) | ![Sphere volume](images/icons/shapes/sphere_solid.svg) |
| Cylinder | ![Cylinder outline](images/icons/shapes/cylinder_outline.svg) | ![Cylinder volume](images/icons/shapes/cylinder_solid.svg) |
| Pyramid | ![Pyramid outline](images/icons/shapes/pyramid_outline.svg) | ![Pyramid volume](images/icons/shapes/pyramid_solid.svg) |
| Prism | ![Prism outline](images/icons/shapes/prism_outline.svg) | ![Prism volume](images/icons/shapes/prism_solid.svg) |
| Stairs | ![Stairs outline](images/icons/shapes/stairs_outline.svg) | ![Stairs volume](images/icons/shapes/stairs_solid.svg) |

## 6. Selection and transforms

In Select mode, use:

- `Q`: Hand / View
- `W`: Move
- `E`: Rotate
- `R`: Scale

Transform handles affect only the selected voxels inside the current object. They do not move the complete object as they would in World mode.

Common selection commands:

- `Command/Ctrl + A`: Select all voxels
- `Command/Ctrl + C`: Copy selection
- `Command/Ctrl + X`: Cut selection
- `Command/Ctrl + V`: Paste
- `Command/Ctrl + D`: Duplicate selection
- `Delete`: Delete selection
- `Esc`: Cancel the current selection

To turn the selection into an independent object, choose `Voxel Edit > Detach and Subdivide`. Its shortcut is `Command/Ctrl + Shift + D`, and its dialog can also set subdivision for the detached result.

## 7. Colors and materials

Colors and materials are related but distinct:

- regular voxels usually use solid colors and work well for general modeling and FBX export;
- Minecraft materials identify specific blocks and include their textures and Minecraft block identity.

Open the material window with `View > Materials`. The active material is used by Create and Paint operations. Palettes can group materials, including default and Minecraft materials.

Eyedropper is usually the fastest way to copy an existing voxel's appearance.

To adjust colors in bulk, select voxels and choose `Voxel Edit > Adjust Color`, or press `Command/Ctrl + Shift + C`. When no selection exists, the command may affect the currently available voxel range; review the preview before applying it.

## 8. Camera and view controls

### Focus

Press `F` to focus the current content:

- in World mode, focus the selected object;
- with no selection, frame all visible objects;
- in Voxel mode, focus the current voxel content.

### Orbit

In Voxel mode:

- right-drag over visible model geometry to orbit around the pointed location;
- on macOS, `Option + left-drag` uses the editor's default orbit behavior around the current Scene pivot;
- right-drag over empty space preserves the editor's default camera behavior.

### Pan, zoom, and free movement

- Use the mouse wheel to zoom.
- Use the Hand tool to view and pan.
- Hold the right mouse button and use movement keys for free movement.
- Hold `Shift` to move faster.

Modeling tools do not draw while the mouse is being used for orbiting, panning, or another camera operation.

## 9. Grid, workspace, and Pivot

### Coordinates and front direction

VoxelDream uses this asset-local convention:

```text
+X = right
+Y = up
+Z = forward
```

A character's face, a vehicle's front, or a building's main entrance should point toward `+Z` and lie on the maximum-Z side of the model. A front-view camera normally sits on the `+Z` side and looks toward `-Z`.

Bottom center is often a useful Pivot for grounded assets. A model may use both positive and negative X/Z coordinates around its Pivot. Export adapters handle formats with different coordinate systems.

### Grid settings

Open grid settings through `Options > Settings`, or press `Command/Ctrl + ,`. Check the current view, work plane, and grid settings before a large operation if placement does not behave as expected.

### Voxel workspace size

Choose `Voxel Edit > Adjust Voxel Workspace Size`, or press `Command/Ctrl + Shift + G`.

Workspace size determines the editable voxel range. Enlarging it allows a larger model; when reducing it, check whether existing voxels lie outside the new bounds.

In Voxel mode, press `V` to start a temporary workspace at the current cursor position. Press it again to restore the complete workspace.

### Pivot

![Edit Pivot](images/icons/edit_pivot.svg)

The Pivot is the point around which an object is placed, rotated, scaled, and exported in World mode.

While editing the Pivot, choose from the model center, bottom center, top center, side centers, and corners:

- `Enter`: Apply
- `Esc`: Cancel

Bottom center or geometric center is suitable for many game props. Try bottom center first for an object that stands on the ground.

## 10. Save and open projects

VoxelDream projects use `.voxproj`. A project preserves editable source data rather than only a final mesh.

Common commands:

- `File > New`
- `File > Open`
- `File > Save`
- `File > Save As`

Shortcuts:

- `Command/Ctrl + O`: Open
- `Command/Ctrl + S`: Save
- `Command/Ctrl + Shift + S`: Save As

If you save while in Voxel mode, VoxelDream safely returns to World mode, commits the current voxel edit, and then writes the project.

The current version does not promise autosave or crash recovery. Save after important work and use Save As periodically to keep milestone versions.

`.voxproj` is a complete scene project; `.vvox` is an exchange file for one voxel asset.

## 11. Import

### Import VVOX

In World mode choose `File > Import > VVOX…`. The `.vvox` file is added to the scene as a new editable voxel object.

### Import an image

Choose `File > Import > Image…`.

Supported formats:

- PNG
- JPG / JPEG / JFIF
- WebP
- BMP

The import dialog provides direction, width, height, and aspect-ratio settings.

- In World mode, the image creates a new voxel object.
- In Voxel mode, the image is written into the current workspace using one or more selected projection directions.

A single imported object is limited to 256 voxels per side. Choose an appropriate size before importing a high-resolution image. Images with transparent backgrounds are especially useful for icons, pixel art, signs, and thin forms.

## 12. Export FBX

In World mode choose `File > Export > FBX…`.

1. Select one or more objects.
2. Choose an export folder.
3. Enter a filename.
4. Choose triangle or quad topology.
5. Confirm the export.

Objects deleted in World mode are excluded from saved projects and FBX, GLB, publishing, and Minecraft export scopes. Deleting a parent also excludes its children. Disabling an object is not the same as deleting it: it remains in `.voxproj`, although exports based on currently visible meshes may omit it.

The default export location is normally the desktop for an unsaved project, or an `Exports` folder beside a saved project.

Before exporting:

- return to World mode;
- check scale and orientation;
- set an appropriate Pivot;
- select only the required objects in the export dialog;
- save the project;
- inspect scale, materials, orientation, and Pivot in the target application.

FBX is a final mesh for Unity, Unreal, Godot, Blender, and other 3D workflows. It does not replace editable voxel source data in `.voxproj` or `.vvox`.

## 13. Export a Minecraft Add-On

In World mode choose `File > Export > Minecraft Add-On…`.

The current exporter supports official Bedrock and related China Edition Bedrock targets and offers resource types according to object content. The result is normally `.mcaddon` or `.zip`, depending on the target.

Before exporting:

- solid-color voxels and Minecraft block materials are different data;
- models made with a Minecraft palette are better suited to structure export;
- small solid-color models are better suited to custom-block export;
- the exporter may reject models that exceed target limits or use incompatible materials;
- Java, Bedrock, blocks, entities, and world structures are different formats.

Use FBX to bring a Minecraft-style model into a general game engine. Use a Minecraft Add-On only when Minecraft must recognize the package directly.

## 14. Undo, redo, and data safety

- `Command/Ctrl + Z`: Undo
- `Command/Ctrl + Shift + Z`: Redo

World and Voxel modes keep history appropriate to their operations. After a large fill, detach, scale, or generation operation, inspect the result immediately and undo it before continuing if necessary.

Large models may still be rebuilding their display meshes while leaving Voxel mode, saving, or exporting. Do not force-quit the application during this work.

To reduce the risk of losing work:

- save frequently;
- use Save As before large changes;
- keep the original `.voxproj`;
- keep important individual assets as `.vvox` files;
- do not treat exported files as a replacement for the editable project.

## 15. Other features

These features have user-facing entries but are not required for ordinary voxel modeling.

### Asset Library

Open it through `View > Asset Library` to browse built-in assets and categories.

### Single-frame render

In World mode choose `Render > Single Frame Render`, or press `Command/Ctrl + R`, to render the current scene to a PNG image.

### Animation window

Open it through `View > Animation`. Animation is an advanced feature and is not required for ordinary modeling, saving, or FBX export.

### Minecraft terrain generator

In Voxel mode choose `Voxel Edit > Generate Minecraft Terrain`. This experimental feature creates a finite, editable voxel asset. It is not an infinite-world generator or a complete Minecraft world editor.

### Maze and dungeon generator

In Voxel mode choose `Voxel Edit > Generate Maze and Dungeon`. Use it as a starting structure, then inspect, edit, and save the result with the normal voxel tools.

## 16. Shortcut reference

| Action | Shortcut |
| --- | --- |
| Open project | `Command/Ctrl + O` |
| Save project | `Command/Ctrl + S` |
| Save As | `Command/Ctrl + Shift + S` |
| Undo | `Command/Ctrl + Z` |
| Redo | `Command/Ctrl + Shift + Z` |
| Cut / Copy / Paste | `Command/Ctrl + X/C/V` |
| Duplicate object or voxel selection | `Command/Ctrl + D` |
| Select all | `Command/Ctrl + A` |
| Settings | `Command/Ctrl + ,` |
| Delete | `Delete` |
| Focus | `F` |
| Hand / Move / Rotate / Scale | `Q / W / E / R` |
| Enter Voxel mode | `Enter` in World mode |
| Cancel selection or leave Voxel mode | `Esc` |
| Select / Create / Paint / Erase | `1 / 2 / 3 / 4` in Voxel mode |
| Adjust color | `Command/Ctrl + Shift + C` |
| Detach and subdivide | `Command/Ctrl + Shift + D` |
| Adjust voxel workspace size | `Command/Ctrl + Shift + G` |
| Start/stop temporary workspace | `V` in Voxel mode |
| Single-frame render | `Command/Ctrl + R` |

On macOS, use `Command + 1` through `Command + 7` to select the first seven currently visible voxel tools. These numbers refer to toolbar positions because the visible tools change with the current mode.

## 17. Troubleshooting

### Why does Esc not leave Voxel mode immediately?

If a cancellable voxel selection exists, `Esc` cancels it first. Press `Esc` again to return to World mode.

### Why can I not enter Voxel mode?

Select an editable voxel object in World mode, then press `Enter`. An empty object or mesh without voxel source data cannot be edited as a voxel object directly.

### Why is an export command disabled?

FBX and Minecraft Add-On export are enabled only in World mode, and the scene must contain an eligible exportable object.

### Why did Paint not change the model's shape?

Paint changes only the appearance of existing voxels. Use Create to add voxels and Erase to remove them.

### Why can I not select voxels with the Hand tool active?

The Hand tool is for viewing the scene. Press `1` to return to Select mode, or press `W` to use Move before selecting voxels.

### Why did saving return me to World mode?

This is expected. VoxelDream must commit the current voxel edit and update the object's data before saving the complete project.

### Why can leaving Voxel mode or saving a large model take longer?

Voxel data changes require the display mesh to be rebuilt. Larger and more complex edits affect more chunks. Wait for the operation to finish and do not force-quit the application.

### I exported an FBX. Do I still need to save the project?

Yes. FBX primarily contains a final mesh and does not replace editable voxel source data. Keep the `.voxproj` as well.

## 18. Recommended working habits

1. Use one voxel object for each independent prop.
2. Manage multiple objects in World mode and edit one object at a time in Voxel mode.
3. Build the large forms first, add details second, and finish with color.
4. Inspect previews before confirming large operations.
5. Save a milestone version before major changes.
6. Check Pivot, scale, orientation, and object selection before export.
7. Keep both the editable project and the final exported files.
