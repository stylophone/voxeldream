# VoxelDream（体素梦工厂）

[English](README.md) · [使用指南](docs/User-Guide.zh-CN.md) · [更新日志](CHANGELOG.md)

> 像搭积木一样简单，但做出的资产真的能进入后续项目。

VoxelDream 是一款可控的体素化 3D 创作工具，用于制作、编辑和变换可进入游戏制作流程的资产与场景。你可以从零开始，也可以从图片、Mesh 或已有体素内容出发，使用直接编辑工具继续精修，并将作品导出到 Minecraft、游戏引擎或标准 3D 工作流。

> **Very Early Beta / 极早期测试版**
>
> 当前版本可能包含缺陷、未完成功能，项目文件格式也可能发生变化。请为重要作品保留备份。

## 截图

<table>
  <tr>
    <td><img src="screenshots/terrain-island.png" alt="编辑大型体素地形岛屿"></td>
    <td><img src="screenshots/voxel-building-edit.png" alt="编辑体素建筑"></td>
  </tr>
  <tr>
    <td align="center"><sub>大型体素地形</sub></td>
    <td align="center"><sub>体素建模与选择</sub></td>
  </tr>
  <tr>
    <td><img src="screenshots/relay-arena.png" alt="彩色体素竞技场"></td>
    <td><img src="screenshots/world-pivot-editing.png" alt="在 World 模式中编辑体素资产"></td>
  </tr>
  <tr>
    <td align="center"><sub>大型精细体素资产</sub></td>
    <td align="center"><sub>World 模式与 Pivot 编辑</sub></td>
  </tr>
</table>

## 下载

请从 [GitHub Releases](https://github.com/stylophone/voxeldream/releases/latest) 下载最新版本。

VoxelDream 也可以通过 [itch.io](https://stylophone.itch.io/voxeldream) 获取。

## 可以用它做什么

### 塑形与修整

- 使用画笔自由创作，或通过直线、面、方框、球体、圆柱、棱锥、棱柱和楼梯快速搭建形体。
- 选择连续表面或区域，再进行调色、复制、移动、旋转、缩放与分离。
- 使用纯色 Palette 或 Minecraft 方块材质创作。

### 制作完整资产

- 在同一个工程中保留多个体素资产，并在 World 模式中编辑对象 Transform、层级与 Pivot。
- 在 World 模式和专注的体素编辑之间切换，同时保留原始可编辑体素数据。
- 导入 VVOX，或将 PNG、JPEG、WebP 和 BMP 图片转换为可继续编辑的体素内容。
- 保存并重新打开完整的 `.voxproj` 工程，而不只是保留扁平化的导出文件。

### 把成果带到其它项目

- 导出 FBX Mesh，进入常规 3D 软件与游戏引擎工作流。
- 为当前支持的 Bedrock 目标导出 Minecraft Add-On 包。
- 使用内置资源库快速开始，并将作品离线渲染为 PNG 图片。

## 反馈

发现问题或有功能建议？请[提交 Issue](https://github.com/stylophone/voxeldream/issues)。

报告缺陷时，请尽量附上操作系统、VoxelDream 版本和可复现问题的操作步骤。

## 授权

VoxelDream 可免费用于个人和商业用途。使用 VoxelDream 创作的内容归创作者所有，并可用于商业项目；但导入的素材仍需遵守其原始权利与许可要求。

详情请参阅 [LICENSE](LICENSE)。
