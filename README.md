<p align="center">
  <img src="docs/images/icon.png" alt="Topview 3D Builder" width="150" height="150">
</p>

# Topview 3D Builder for ComfyUI

**English** · [简体中文](README.zh-CN.md)

Build a 3D scene, frame your shot, and export images or animated videos directly to the ComfyUI canvas.

Based on [Topview 3D Builder](https://github.com/topviewai/topview-3d-builder), a 3D staging tool for planning character placement, camera angles and camera moves for AI video. This ComfyUI adaptation packages the interactive editor and local assets for use in node workflows, without the agent integration.

The compiled editor and built-in assets are included. No frontend build, Node.js runtime, account or API key is required to use the plugin.

![Topview 3D Builder scene editor](docs/images/editor.png)

## Features

- **Interactive 3D staging:** place and transform characters and primitive objects, adjust poses, and compose your scene.
- **Bundled assets:** 4 characters, 121 static poses and 5 primitive types, available locally.
- **Camera tools:** camera preview, shot composition and camera movement presets.
- **Timeline:** edit scene animation and export a selected frame range as video.
- **Image and video export:** choose camera, frame or frame range, resolution and aspect ratio. Download locally or export directly to the ComfyUI canvas.
- **Native workflow integration:** image exports create `LoadImage` nodes; video exports create `LoadVideo` nodes for downstream processing.
- **Compact editor:** a centered floating window occupying 90% of the viewport, with a single toolbar and **Save and Exit**.
- **Scene persistence:** editable scene data is stored in the Builder node's properties and included when you save the ComfyUI workflow.
- **15 UI languages:** English, Simplified Chinese, Traditional Chinese, Japanese, Korean, French, German, Spanish, Portuguese, Russian, Arabic, Turkish, Indonesian, Malay and Vietnamese.

## Requirements

- A working ComfyUI installation with its Python dependencies installed.
- A browser with WebGL support. Video export also depends on browser codec support.
- A ComfyUI version providing the native `LoadVideo` node for video export to the canvas.

Validated locally with ComfyUI **0.22.0** and frontend **1.43.18**. Other versions have not all been tested.

## Installation

**Option 1 — Git (recommended)**

Open a terminal inside your `ComfyUI/custom_nodes` folder and run:

```sh
git clone https://github.com/gyx85542-dot/ComfyUI-Topview-3D-Builder.git
```

For Windows portable, the parent folder is typically:

```text
ComfyUI_windows_portable/ComfyUI/custom_nodes/
```

**Option 2 — Download ZIP**

Use **Code → Download ZIP** on this repository. Extract the plugin folder into `ComfyUI/custom_nodes`. Make sure `__init__.py` is directly inside the plugin folder, with no extra nested repository folder:

```text
ComfyUI/
└── custom_nodes/
    └── ComfyUI-Topview-3D-Builder/
        ├── __init__.py
        ├── backend.py
        ├── assets/
        ├── editor/
        └── web/
```

Restart ComfyUI, then refresh the browser (**Ctrl+F5** if cached files remain). Install only one copy of this plugin: if an older `Topview-3D-Builder` folder already exists, update or replace that copy instead of keeping both names installed.

## Quick start

1. Add **Topview → Topview 3D Builder** from the node menu or search for **Topview 3D Builder**.
2. Click **Open 3D Builder**. Add characters or objects, adjust poses, and set up your camera.
3. Click the central **Export** button. Select **Image** or **Video**, then configure the output.
4. Click **Export to ComfyUI canvas**. After successful export and saving, the editor closes and the exported media appears as a native node.
5. To save the scene without creating a media node, click **Save and Exit**. This updates the Builder card's preview and closes the editor.
6. **Save your ComfyUI workflow** to keep the editable scene with the graph. Saving inside the editor does not save the workflow file itself.

The Builder node has no input/output ports. Connect the exported image or video node to the rest of your workflow. You can also drag [the example workflow](examples/topview-3d-preview.json) into ComfyUI to try a two-character scene.

## Export preview

Choose **Image** or **Video** in the same export dialog, then download the result or send it to the ComfyUI canvas.

![Image export settings](docs/images/export-image.png)

![Video export settings](docs/images/export-video.png)

## Updates

For a Git installation, open a terminal inside the installed plugin folder:

```sh
git pull
```

Restart ComfyUI and refresh the browser. For a ZIP installation, replace the plugin files with the latest download after backing up any custom changes.

## Storage and troubleshooting

- Scene previews and corresponding JSON files: `ComfyUI/input/topview3d/`.
- Exported images and videos: `ComfyUI/input/topview3d/exports/`.
- After moving a workflow to another machine, open the Builder and select **Save and Exit** to regenerate a missing preview. Copy exported media separately if your workflow references it.
- If the node is missing, check the installation folder structure and ComfyUI startup logs, then restart and refresh.
- If `LoadVideo` is unavailable, update ComfyUI or use **Download** in the export dialog.
- If loading fails, use **Retry** or **Exit Without Saving**. The latter restores the Builder scene state from before opening the editor. If saving fails, the editor stays open so you can retry.

## Current scope

The bundled library contains static poses, **not character motion clips**. The empty Motions tab is hidden; camera moves and timeline animation remain available. Depth, normal and OpenPose render passes, external model import, and API-only rendering are not included. Only one Builder editor can be open at a time.

## Development and credits

- Original project: [topviewai/topview-3d-builder](https://github.com/topviewai/topview-3d-builder).
- ComfyUI adaptation source and build instructions: [feature/comfyui-plugin](https://github.com/gyx85542-dot/topview-3d-builder/tree/feature/comfyui-plugin/comfyui).
- This repository distributes the ready-to-install plugin.

## License

- Code: [Apache-2.0](LICENSE), [NOTICE](NOTICE).
- Bundled assets: [assets/LICENSE](assets/LICENSE), [assets/NOTICE](assets/NOTICE).
- Fonts: [Darker Grotesque OFL](licenses/OFL.txt), [Instrument Sans OFL](licenses/OFL-instrument-sans.txt).
- Frontend dependencies: [JavaScript notices](editor/main.js.LEGAL.txt), [CSS notices](editor/main.css.LEGAL.txt).
