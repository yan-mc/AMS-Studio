# AMS Studio

> 本地优先的 Windows AI 音乐工作站。桌面启动器 + DeepSeek Harness Kernel + Cordis 插件 + FastAPI Gateway + RVC/pymss/TTS 本地能力。所有用户数据位于安装目录 data，不写 C 盘 AppData。

## 当前状态（2026-10-25）

- 阶段 A–F 核心完成；G 发布收尾中。
- 公开组件 feed：2042。
- setup：2,438,343 字节，SHA256 D2DEFF5125CD857F41D9CE7A7C689E79A1DDA88AADA55F486DF4AE6060338B45。
- 本机安装：F:/AMS-Studio；源码：F:/Deepseek_harness/AI音乐处理/08_项目代码。
- 用户音色：曼波；测试工程已移入 data/trash/projects。
- Kernel 当前会话 watchdog：data/tools/kernel-watchdog.ps1。

## 完整记录

- [PROJECT_RECORD.md](PROJECT_RECORD.md)（唯一总记录）
- [docs/PROJECT_RECORD.md](docs/PROJECT_RECORD.md)（docs 子仓库镜像）

## 子模块

| 目录 | 仓库 | 作用 |
|---|---|---|
| launcher | ams-launcher | Tauri 启动器、组件安装、Kernel 生命周期 |
| kernel | ams-harness | AMS Kernel（DSH fork） |
| plugins | ams-plugins | 音乐 UI + Host 桥接 |
| services | ams-services | Gateway、RVC/pymss/TTS/train/evaluate/mix |
| tools | ams-tools | MSVC/模型转换工具 |
| docs | ams-docs | 设计、计划、验证、发布、事故记录 |
| release | ams-release | feed、签名、发布与打包 |

## 安装

1. 运行 setup；
2. 安装/更新组件；
3. 启动 Kernel；
4. 所有数据留在安装目录 data。

## 已知限制

- 干净 VM/卸载未完全验收；
- Kernel 无系统级常驻；
- F 插件未拆；
- 混音不是完整 DAW；
- VC 长稳未做；
- feed CDN 可能延迟；
- 测试数据集仍占用 data/datasets。

## 安全

- 不写 C 盘用户目录；
- 不做目录递归删除；
- 删除前确认路径，优先移动到隔离目录；
- 用户音色/模型/真实项目不进入 Git。
