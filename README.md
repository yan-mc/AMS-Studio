# AMS Studio

> **本地优先的 AI 音乐工作站。**  
> 一个桌面启动器 + 一个可插件化的 AI 音乐内核 + 本地音频服务 + 模型转换工具。所有用户数据留在安装目录内，不依赖云端账号，不碰现有 DSH 的 `.dsh`。

AMS Studio 的目标是让“炼制自己的音色、分离人声、变声、换源、TTS、V 家填词”这些流程在一个本地工作台里跑通，同时允许用户自带 DeepSeek Key/兼容端点。

## 架构

```text
AMS Studio Launcher (桌面入口/安装更新)
        │
        ├── AMS Kernel (DeepSeek Harness fork)
        │       └── AMS 音乐插件 (功能页 + Host bridge)
        │
        ├── 本地 Gateway (FastAPI，127.0.0.1)
        │       ├── RVC / pymss / MSVC 任务
        │       └── artifacts / voices
        │
        └── data/ (安装目录内：kernel、plugins、voices、artifacts、logs)
```

## 子模块

| 目录 | 仓库 | 作用 |
|---|---|---|
| `launcher/` | [ams-launcher](https://github.com/yan-mc/ams-launcher) | 桌面启动器、组件安装/更新、内核/Gateway 生命周期 |
| `kernel/` | [ams-harness](https://github.com/yan-mc/ams-harness) | AMS Kernel：DSH fork，无登录直接工作区 |
| `plugins/` | [ams-plugins](https://github.com/yan-mc/ams-plugins) | 音乐工作台 UI + Host 工具桥 |
| `services/` | [ams-services](https://github.com/yan-mc/ams-services) | 本地 Gateway 与 RVC/pymss/MSVC 服务 |
| `tools/` | [ams-tools](https://github.com/yan-mc/ams-tools) | MSVC/XINYU_AI → RVC pth 等转换工具 |
| `docs/` | [ams-docs](https://github.com/yan-mc/ams-docs) | 设计、计划、测试、发布、事故记录 |
| `release/` | [ams-release](https://github.com/yan-mc/ams-release) | 签名更新 feed、Release 资产与打包脚本 |

## 克隆

本总仓库与大部分子仓库目前是 **private**，需要 yan-mc 账号凭据：

```powershell
git clone --recurse-submodules https://github.com/yan-mc/AMS-Studio.git
cd AMS-Studio
```

已克隆后更新：

```powershell
git pull --recurse-submodules
git submodule update --init --recursive
```

## 当前状态

- M0/M1/M2 方案、启动器、内核、插件、Gateway、更新 feed 已完成。
- AMS Kernel 已移除登录/引导，只保留连接设置（网址 + Key）。
- 所有 AMS 数据位于安装目录下 `data`，不写入现有 DSH 的 `.dsh`。
- 公开更新源：[ams-release](https://github.com/yan-mc/ams-release)。

## 文档入口

- [安装与连接设置](https://github.com/yan-mc/ams-docs)
- [生命周期验证与清理](https://github.com/yan-mc/ams-docs)
- 各子仓库 README 的第一屏说明其职责。

## 开发约定

- 子仓库独立开发、独立提交；总仓库只更新 submodule 指针。
- 提交前确保对应子仓库 README/描述与实际职责一致。
- 不提交用户音源、模型权重、生成音频或 API Key。
