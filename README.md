<div align="center">

<img src="docs/assets/icon.png" width="96" alt="Coday" />

# Coday

### 不换编辑器，用你自己的模型。

**Cursor / Windsurf / Devin / Kiro 的 BYOK 网关。**
接入任意 OpenAI / Claude 兼容接口，聊天、补全、Agent、工具调用全部照常工作。

[![Release](https://img.shields.io/github/v/release/HyperClockUp/Coday?style=flat-square&color=2f6bff)](https://github.com/HyperClockUp/Coday/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/HyperClockUp/Coday/total?style=flat-square&color=22c55e)](https://github.com/HyperClockUp/Coday/releases)
[![Stars](https://img.shields.io/github/stars/HyperClockUp/Coday?style=flat-square&color=f59e0b)](https://github.com/HyperClockUp/Coday/stargazers)
![Platform](https://img.shields.io/badge/platform-Windows%2010%2B-0078d4?style=flat-square)
![BYOK](https://img.shields.io/badge/BYOK-OpenAI%20%7C%20Claude-8b5cf6?style=flat-square)

[**下载最新版**](https://github.com/HyperClockUp/Coday/releases/latest) · [快速开始](#快速开始) · [功能](#功能) · [常见问题](#常见问题) · [English](./README.en.md)

<br />

<img src="docs/assets/coday.png" alt="Coday 界面" width="380" />

</div>

---

## 它解决什么问题

你习惯了 Cursor、Windsurf、Devin 或 Kiro，但是：

- 官方额度不够用，或者想用自己更熟的模型
- 手里有自己的 API Key / 中转站 / 公司网关，却没法在编辑器里直接用
- 同时用好几个编辑器，每个都要单独折腾一遍配置、提示词和规则

Coday 在本机运行一个透明代理，把编辑器发出的 AI 请求按各自协议转换后，转发到**你指定的上游**。
安装、连接、打开编辑器，和平时一样用，编辑器侧不需要任何改动。

```
  编辑器 (Cursor / Windsurf / Devin / Kiro)
        |
        |  编辑器原生协议
        v
  Coday  (本机透明代理：协议转换 / 路由 / 故障转移 / 提示词注入)
        |
        |  OpenAI 兼容 / Claude 协议
        v
  你的 API 源  (官方接口 / 中转站 / 公司网关 / 自建服务)
```

## 为什么用 Coday

| 你想要的 | Coday 怎么做 |
|---|---|
| 不换编辑器 | 原生拦截，聊天、补全、Agent、工具调用照常可用 |
| 用自己的模型 | 任意 OpenAI / Claude 兼容接口，一键同步模型列表 |
| 一个源挂了不中断 | 多源故障转移，限流、报错、不可达时自动切到下一个 |
| 多个编辑器共用一套规则 | 跨 IDE Skills 感知，自动读取各编辑器的规则文件 |
| 远程开发也能用 | 支持 Remote-SSH，流量通过反向隧道回到本机 |
| 出问题能定位 | 内置请求查看器、日志、证书与拦截诊断 |

## 功能

### 多编辑器接管
支持 **Cursor、Windsurf、Devin、Kiro**。自动识别各自协议并做转换，聊天、补全、Agent 与工具调用都保持可用。

### 自选模型与 API 源
- 集中管理多个 API 源：填入接口地址与 Key，一键同步上游模型列表
- 自定义模型、显示名称、价格标签，随时切换当前源
- 内置源开箱即用，也可添加任意 OpenAI 兼容 / Anthropic 协议的源

### 多源故障转移
当前源出现限流、报错或不可达时，自动切换到下一个可用源，减少对话被突然打断。默认关闭，按需开启。

### 跨 IDE Skills 感知
自动读取项目中各编辑器的规则文件，不管你当前用哪个编辑器，都能拿到完整的项目指令：

`.windsurfrules` · `.cursor/rules/` · `.kiro/steering/` · `CLAUDE.md` · `.devin/`

### 远程开发（Remote-SSH）
编辑器通过 Remote-SSH 连接远程主机时，语言服务和 AI 流量都跑在远端。Coday 通过反向 SSH 隧道把这部分流量带回本机，路由与模型注入照常生效。支持 Linux 远程主机。

### 自定义人设
为每个编辑器单独设置系统提示词：

- **替换**：用你的提示词替换编辑器自带提示词（工具调用、工作目录等关键内容仍会保留）
- **追加**：在编辑器原有提示词之后追加你的内容

可随时恢复默认。

### 更多能力
- **图像生成**：可配置独立的出图服务
- **思考强度**：全局调节模型 reasoning 强度，从关闭到最高
- **身份与额度展示**：按编辑器分别自定义状态栏显示的账号信息
- **网络诊断**：请求 / 响应查看器、日志、证书与拦截状态一站式排查
- **体验细节**：中英双语界面、深色主题、系统托盘、开机自启、自动检查更新

## 快速开始

1. 从 [Releases](https://github.com/HyperClockUp/Coday/releases/latest) 下载并安装最新版
2. 打开 Coday，选择一个内置源，或填入你自己的接口地址与 Key
3. 点击连接。首次运行会自动安装本地 CA 证书并配置拦截
4. 打开 Cursor / Windsurf / Devin / Kiro，照常使用

## 常见问题

**Coday 会读取或上传我的代码吗？**
AI 请求经本机的 Coday 代理转换后，转发到你在界面里选定的 API 源（内置源或你自己填写的接口）。用哪个源、填哪个 Key 由你决定；如果对数据流向敏感，建议使用你自己的接口地址。

**为什么需要安装 CA 证书？**
编辑器的 AI 请求是 HTTPS 加密的。Coday 需要本地 CA 来解密、转换协议后再转发给你的上游。证书只在本机使用，可在系统证书管理中查看与移除。

**支持哪些模型和接口？**
任意 OpenAI 兼容（Chat Completions / Responses）或 Claude（Anthropic）协议的接口。

**支持 macOS / Linux 吗？**
目前主要支持 Windows 10 x64 及以上。Linux 仅作为 Remote-SSH 的远程主机受支持。

**连不上或没反应怎么办？**
打开内置的网络诊断面板，查看证书、拦截状态与请求日志；仍无法解决请加入下方交流群反馈。

## 最近更新

### v0.8.1
- 窗口圆角与系统实际半径对齐，消除四角缝隙
- 修复加载弧线动画失效
- 界面视觉统一为玻璃质感，色彩收敛为品牌蓝加语义色
- 安装包加固，并更新 minisign 签名与自动更新清单

### v0.7.18
- 桌宠显示进行中的步骤与计划进度
- 修复 Devin Fast Context Unleash 开关

### v0.7.17
- Fast Context 接入 Devin CLI prompt 改写，连接 / 启动时尽力应用补丁

### v0.7.16
- 修复 Kiro 文本轮被当成截断而反复重试
- grok-4.x 按模型协议走 OpenAI Chat Completions
- 展开 Kiro 工具 Schema 的 `$ref`，避免部分模型 400 空回复
- 上游错误在对话中可见

### v0.7.5
- **跨协议 Prompt 缓存**：修复 Devin / Windsurf 多轮对话缓存命中率低的问题，Anthropic、OpenAI Chat Completions、OpenAI Responses 三种协议全部对齐
- **CA 证书序列号匹配**：避免过期同名证书导致 IDE 断连
- 改善中文 Web 搜索结果相关性

更早的版本见 [Releases](https://github.com/HyperClockUp/Coday/releases)。

## 系统要求

Windows 10（x64）及以上。

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=HyperClockUp/Coday&type=Date)](https://star-history.com/#HyperClockUp/Coday&Date)

如果 Coday 对你有帮助，欢迎点一个 Star，这是对项目最直接的支持。

## 反馈与交流

使用问题、功能建议或闲聊，欢迎扫码加入 QQ 交流群，也可以直接提 [Issue](https://github.com/HyperClockUp/Coday/issues)。

<img src="docs/assets/qq-group.jpg" alt="交流群" width="200" />

## 许可

Proprietary. 保留所有权利。
