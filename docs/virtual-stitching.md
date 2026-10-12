---
tags:
   - imaging
   - stitching
   - alignment
---

*Move the tiles of a converted, tiled image by hand to correct how they sit next to each other, or move one channel against the others.*

Moves are written to the image as you make them, so they affect everyone who opens it. Only the image's owner, or a site administrator, can move tiles.

---

## Steps

1. Open the image with `Open Dataset` in `Library`, or open a scene that holds it from `Scenes`. It opens in the viewer window.
2. In the viewer window, open the `Layers` tab and click the tiled image layer to select it.
3. In the main window, click `Virtual Stitching` in the sidebar, under `Plugins`. The panel opens with the layer that is selected in the viewer. To add another layer, `Ctrl`+click (`Cmd`+click on macOS) it in the viewer's `Layers` tab.
4. `Auto-select` follows the viewer: it selects the tile under the viewer's position. Turn it off before you select several tiles.
5. Select tiles under `Tile Grid`:
    - Click a tile to select it. The viewer centers on that tile.
    - Drag from one tile to another to select the rectangle between them.
    - `Ctrl`+click (`Cmd`+click on macOS) toggles one tile, and `Shift`+click selects a range.
    - Click a row or column header to select the whole row or column.
    - `Select all` and `Deselect all` act on all tiles.
6. On a multi-channel image, choose the channels to move under `Move channels:`. Only the chosen channels move.
7. Under `Move tile`, use the `X`, `Y` and `Z` sliders, the arrow buttons (minus and plus for `Z`) or the number fields. `Step` sets how far a button click moves. Positive X moves the tile right, Y down and Z deeper. The viewer refreshes when you release the slider.
8. Click `Confirm` to clear the modified marker. `Discard` returns the modified tiles to the positions the panel loaded, or to the last `Confirm`.

Tiles marked with a dot have been moved and not yet confirmed. Unselected ones are orange. `N tile(s) modified` counts each moved channel of a tile. The number fields show the shift since the panel loaded the tiles or you last clicked `Confirm`. A move from an earlier visit to the panel is already saved and cannot be discarded. Move it back by hand. How far a tile can move depends on the margin left when the image was converted. An axis with no room is grayed out.

`Export` under `Tile Grid` downloads the tile positions of the first selected layer as a JSON file.

---

## Automatic alignment

The `Alignment` section has `Auto-align`, `Reset` and `Restore`. `Refine` also appears when the chosen `Engine` offers it. `Engine` and `Estimate from` choose the method and the reference channel, and `Manual link` fixes a single seam by hand. The buttons run as background jobs, which are listed under `Jobs`. They need exactly one layer selected, so hover over a grayed button for the reason.

`Auto-align`, `Refine` and `Reset` set one position for all channels of each tile, so they replace a correction made on a single channel. `Reset` returns all tiles to their converted positions. `Restore` puts back the positions saved before the last run, and undoes only one run. Run the automatic steps before you correct a single channel. See [Move one channel](#move-one-channel).

---

## Move one channel

Use this when one channel of a multi-channel image sits shifted against the others. It needs an image that holds several channels in one layer. An image converted with `Split into separate layers per channel` has no `Move channels:` row, so this does not apply to it.

1. Open the panel and select the image layer, as in the steps above.
2. Under `Tile Grid`, turn `Auto-select` off, then click `Select all`.
3. Under `Move channels:`, click `Deselect all`, then click the chip of the channel to correct. Leave the reference channel unselected.
4. Under `Move tile`, move the channel with the `X` and `Y` controls until its features line up with the reference channel in the viewer window. Positive X moves the channel right, and positive Y down.
5. Click `Confirm`.
6. Repeat for the next channel that needs a correction.

There are two `Deselect all` buttons. The one under `Tile Grid` clears the tile selection, and the one under `Move channels:` clears the channel selection.

---

## Troubleshooting

- **`Select layers above to view tiles.`**: the panel has no layer. Click the image layer in the viewer's `Layers` tab, then open the panel again, or `Ctrl`+click (`Cmd`+click on macOS) the layer.
- **`No SISF tiles found in this layer.`**: choose an image layer that was converted with `Convert to SISF` and that you can open. A single-tile image has a one-cell grid.
- **A tile moved back, or a channel correction disappeared**: `Discard` was clicked, or an automatic step (`Auto-align`, `Refine`, `Reset` or `Restore`) ran afterwards. Repeat the move.
- **The move does not stay**: only the owner of the image, or a site administrator, can move tiles.
- **A channel chip has no color**: the chip still works. The color comes from the channel settings in the viewer.
- **The viewer does not change**: wait a moment after you release the slider. If it still does not change, look for an error message, then reload the viewer window.
- **The selection collapses to one tile**: turn `Auto-select` off.
- **The panel says `Please open a scene to use Virtual Stitching`**: open a scene first, and keep the viewer window open.

To change the tile overlap or the voxel size recorded at conversion, use `Edit Metadata` in `Library`. See [Edit Metadata](edit-metadata.md).

---

## Next

- [Scene Viewer](scene-display-window-operations.md)
