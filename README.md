# Topview 3D Builder for ComfyUI

Standalone interactive 3D staging editor with local characters, poses, primitives,
camera controls and timeline. No agent, account, API key or Node.js runtime required.

## Install

From your `ComfyUI/custom_nodes` directory:

```sh
git clone https://github.com/gyx85542-dot/ComfyUI-Topview-3D-Builder.git
```

Restart ComfyUI and refresh the browser. The compiled editor and built-in assets
are included; no frontend build, Node.js, account or API key is required.
To update, run `git pull` inside the cloned folder, then restart and refresh.

## Use

The editor and plugin controls follow ComfyUI's `Comfy.Locale` setting. Supported UI
languages: English, Simplified/Traditional Chinese, Japanese, Korean, French, German,
Spanish, Portuguese, Russian, Arabic, Turkish, Indonesian, Malay and Vietnamese.
Regional aliases (for example `zh` and `pt-BR`) are mapped automatically; unsupported
languages fall back to English. Changing language does not rewrite scene data or
recreate the editor. Raw backend/third-party diagnostic details retain their original language.

1. Place this complete folder inside `ComfyUI/custom_nodes` and restart ComfyUI.
2. Add **Topview 3D Builder**, under **Topview**.
3. Click **Open 3D Builder** to create or edit a scene in a centered 90% floating window.
4. Use **Export → Export to ComfyUI canvas** to create a native `LoadImage` or `LoadVideo` node. Set camera, resolution and frame range in the export dialog. After a successful export, the scene and card preview are saved automatically and the editor closes to reveal the ComfyUI canvas. Export or save failures keep the editor open for retry.
5. Click **Save and Exit** to save the scene and camera preview to the Builder card, then close the editor. If saving fails, the editor remains open for retry.
6. Save the ComfyUI workflow to preserve the editable scene and keyframes with your graph.

Builder icons, text and previews allow dragging the node directly. Exported video
previews fit the video aspect ratio when loaded or resized; drag the picture to move
the node and use the bottom controls for playback.

The Builder card has no input or output ports. Connect the exported image or video
nodes to your workflow. Existing Builder scene data is migrated automatically from
older workflows; its old input/output connections are removed.
The internal `Topview3DScene` class ID is retained for compatibility.

Drag `examples/topview-3d-preview.json` into ComfyUI for a two-character scene.
Scene edits synchronize to the card's properties. Save and Exit also writes a PNG
preview and matching scene JSON under `ComfyUI/input/topview3d`. This saves the
scene, not a separate ComfyUI workflow file; save that file through ComfyUI.
Media exports are stored under `ComfyUI/input/topview3d/exports`.
The Download action in the export dialog saves media locally.

The preview uses the active camera and frame. To recreate a missing preview after
moving a workflow to another computer, open 3D Builder and choose Save and Exit.
The bundled assets must be installed there too.

Depth, normal and OpenPose passes, external model import and API-only rendering
are not included. Only one editor is open at a time. No changes to ComfyUI core
or other custom nodes are needed.

## Development

This repository contains the ready-to-install ComfyUI plugin. Development sources
and build instructions are available in the [source repository](https://github.com/gyx85542-dot/topview-3d-builder/tree/feature/comfyui-plugin/comfyui).

Code: Apache-2.0, see LICENSE and NOTICE. Bundled asset attribution: assets/LICENSE
and assets/NOTICE. Frontend third-party dependency notices: editor/main.js.LEGAL.txt.

A single toolbar contains the scene name and save status, central **Auto** and **Export** controls, and **Save and Exit** on the right. Select Image or Video inside the Export dialog. On initialization failure, use **Retry** or **Exit Without Saving**; the latter restores the Builder card state from before opening the editor.
