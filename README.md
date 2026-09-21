<div align="center">

<img src="docs/assets/icon.png" width="88" alt="Coday" />

# Coday

不换编辑器，用你自己的模型。
支持 Cursor、Windsurf、Devin、Kiro。

[![Release](https://img.shields.io/github/v/release/HyperClockUp/Coday?style=flat-square)](https://github.com/HyperClockUp/Coday/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/HyperClockUp/Coday/total?style=flat-square)](https://github.com/HyperClockUp/Coday/releases)
[![Stars](https://img.shields.io/github/stars/HyperClockUp/Coday?style=flat-square)](https://github.com/HyperClockUp/Coday)
![Platform](https://img.shields.io/badge/platform-Windows-blue?style=flat-square)

[English](./README.en.md) · 简体中文 · [下载](https://github.com/HyperClockUp/Coday/releases/latest)

</div>

<p align="center">
  <img src="docs/assets/coday.png" alt="Coday" width="360" />
</p>

## 功能

- **多编辑器** — 支持 Cursor、Windsurf、Devin、Kiro，聊天、补全、Agent、工具调用照常使用。
- **跨 IDE Skills 感知** — 自动读取项目中各编辑器的规则文件（.windsurfrules、.cursor/rules、.kiro/steering、CLAUDE.md 等），无论你用哪个编辑器都能获得完整的项目指令。
- **自选模型与源** — 接入任意 OpenAI / Claude 兼容接口，一键同步模型，随时切换。
- **多源故障转移** — 当前源不可用时自动切换到下一个可用源。
- **远程开发** — 支持通过 Remote-SSH 连接的远程主机。
- **自定义人设** — 为每个编辑器单独设置系统提示词（替换或追加）。
- **图像生成** — 可配置独立的出图服务。
- **思考强度** — 全局调节模型 reasoning 强度。
- **网络诊断** — 内置请求查看、日志与状态面板。

## 快速开始

1. [下载](https://github.com/HyperClockUp/Coday/releases/latest)并安装 Coday。
2. 选择一个内置源，或填入你自己的接口地址与 Key。
3. 连接后打开编辑器，照常使用。

## 最近更新

### v0.7.5
- **跨协议 Prompt 缓存** — 修复 Devin/Windsurf 多轮对话缓存命中率低的问题；Anthropic、OpenAI Chat Completions、OpenAI Responses 三种协议面全部对齐。
- **CA 证书串号匹配** — 按序列号识别 Coday CA，防止过期同名证书误连导致 IDE 断连。
- 改善中文 Web 搜索结果相关性。

### v0.7.4
- Windsurf 和 Devin 拦截方式改为 hosts 劫持，兼容性更好。

### v0.7.0 – v0.7.3
- **OpenClaw 中心** — 工作区文件编辑器、权限、Agent 与记忆管理一站式面板。
- **CLI Skills 管理器** — 跨工具技能清单，支持从 ZIP 安装与更新检查。
- **CLI MCP 管理器** — 每个 CLI 工具独立切换 MCP Server。
- **CLI 提示词中心** — 单活跃提示词投射到实时文件。
- **CLI 源切换** — 将 Relay 源写入各 CLI Agent 自身配置。
- **OpenAI Responses** — 按源开启 Responses API；Kiro 接入与功能窗口失活修复。
- **多源故障转移 v2** — 源级路由、图像源、跨窗口语言同步、model-source v3 重构。
- 修复 Devin 回退崩溃与并行工具配对问题。

### v0.5.5
- **跨 IDE Skills 感知** — 自动读取项目中各编辑器的规则文件，无论你用哪个编辑器都能获得完整的项目指令。
- 增加上游响应超时时间，减少大模型长对话中断。
- 修正 IDE 环境识别：Devin 不再被误认为 VSCode/Cursor。

## 系统要求

Windows 10（x64）及以上。

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=HyperClockUp/Coday&type=Date)](https://star-history.com/#HyperClockUp/Coday&Date)

## 反馈

<img src="docs/assets/qq-group.jpg" alt="交流群" width="200" />

## 许可

Proprietary. 保留所有权利。
