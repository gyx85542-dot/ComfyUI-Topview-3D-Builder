<p align="center">
  <img src="docs/images/icon.png" alt="Topview 3D Builder" width="150" height="150">
</p>

<h1 align="center">Topview 3D Builder for ComfyUI</h1>

[English](README.md) · **简体中文**

在 ComfyUI 中搭建 3D 场景、调整机位，并将图片或动画视频直接导出到画布。

## 安装和更新

**方法一：Git 安装（推荐）**

在 `ComfyUI/custom_nodes` 目录打开终端，执行：

```sh
git clone https://github.com/gyx85542-dot/ComfyUI-Topview-3D-Builder.git
```

**方法二：下载 ZIP**

点击仓库页面的 **Code → Download ZIP**，将插件文件夹解压到 `ComfyUI/custom_nodes`。确认 `__init__.py` 直接位于插件文件夹内，不要多嵌套一层目录。目录结构如下：

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

安装后重启 ComfyUI 并刷新浏览器。

### 更新

通过 Git 安装的用户，在 `ComfyUI/custom_nodes` 目录打开终端，依次执行以下命令，进入插件目录并拉取最新版本：

```sh
cd ComfyUI-Topview-3D-Builder
git pull --ff-only origin main
```

## 教学

[3D Builder 教学：搭建场景、编排动作与运镜](https://www.topview.ai/academy/spatial-control#3-1-3d-builder-build-scenes-stage-action-and-move-the-camera)

## 功能介绍

- **3D 场景搭建**：放置角色与物体，调整姿势、位置和构图。
- **内置素材**：4 个角色、121 个静态姿势、5 种基础几何体。
- **机位与运镜**：设置相机角度、预览镜头，使用运镜预设和时间轴编排动画。
- **图片与视频导出**：选择机位、帧范围、分辨率和画幅，下载到本地或直接导出到 ComfyUI 画布。
- **多语言**：跟随 ComfyUI 语言设置，支持 15 种语言。

![Topview 3D Builder 场景编辑器](docs/images/editor.png)

### 使用流程

1. 从节点菜单 **Topview → Topview 3D Builder** 添加节点，或搜索 **Topview 3D Builder**。

   https://github.com/user-attachments/assets/0a73724f-d75e-4f62-acef-ac1c4d1b27bd

2. 点击 **打开 3D Builder**，添加角色与物体、调整姿势，并设置相机。

   https://github.com/user-attachments/assets/0b66c435-75dd-4bd6-8efe-86ca57b2cd6e

3. 点击中间的 **导出**，选择图片或视频，并设置输出参数。

   https://github.com/user-attachments/assets/724a4556-249e-46e8-bf8a-daa5b9f1234d

4. 点击 **导出到 ComfyUI 画布**。导出和保存成功后，浮窗自动关闭，画布中出现对应的原生媒体节点。
5. 如只需保存场景，点击 **保存并退出**，即可更新 Builder 节点预览并关闭浮窗。
6. **保存 ComfyUI 工作流**，以保留可编辑场景。编辑器里的保存不会代替工作流文件保存。

## 开发

该项目基于我们的另一个项目 [Topview 3D Builder](https://github.com/topviewai/topview-3d-builder) 开发，支持接入任意 Agent 工具，生成 3D 场景动画。

## 许可证

- 代码：[Apache-2.0](LICENSE)、[NOTICE](NOTICE)。
- 内置素材：[assets/LICENSE](assets/LICENSE)、[assets/NOTICE](assets/NOTICE)。
- 字体：[Darker Grotesque OFL](licenses/OFL.txt)、[Instrument Sans OFL](licenses/OFL-instrument-sans.txt)。
- 前端依赖：[JavaScript 声明](editor/main.js.LEGAL.txt)、[CSS 声明](editor/main.css.LEGAL.txt)。

---

支持我们的另一个项目：[Topview 3D Builder](https://github.com/topviewai/topview-3d-builder)，支持通过 Agent 创建 3D 场景。
