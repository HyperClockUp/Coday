<div align="center">

<img src="docs/assets/icon.png" width="88" alt="Coday" />

# Coday

Keep your editor. Use your own models.
Cursor, Windsurf, Devin, and Kiro.

[![Release](https://img.shields.io/github/v/release/HyperClockUp/Coday?style=flat-square)](https://github.com/HyperClockUp/Coday/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/HyperClockUp/Coday/total?style=flat-square)](https://github.com/HyperClockUp/Coday/releases)
[![Stars](https://img.shields.io/github/stars/HyperClockUp/Coday?style=flat-square)](https://github.com/HyperClockUp/Coday)
![Platform](https://img.shields.io/badge/platform-Windows-blue?style=flat-square)

English · [简体中文](./README.md) · [Download](https://github.com/HyperClockUp/Coday/releases/latest)

</div>

<p align="center">
  <img src="docs/assets/coday.png" alt="Coday" width="360" />
</p>

Coday runs a transparent local proxy that intercepts the AI requests from these editors, converts them per each protocol, and forwards them to the upstream you specify (both OpenAI-compatible and Claude APIs are supported). Install, connect, open your editor and use it as usual — no changes needed on the editor side.

---

## ✨ Features

### 🔌 Editor takeover
Supports Cursor, Windsurf / Devin and Kiro. Auto-detects each protocol and converts it, so chat, completion, Agent and tool calls all keep working in the editor.

### 🛰️ Remote SSH interception
When your editor connects to a remote machine over Remote-SSH, its language server — and the AI traffic — runs remotely, out of the local proxy's reach. Coday tunnels that traffic back to the local MITM (reverse SSH tunnel + remote redirect + remote CA injection), so routing and model injection still apply. Linux remotes supported.

### 🧩 Custom API sources & model library
- Manage API sources in one place: paste your endpoint and key, sync the upstream model list with one click.
- Custom models, display names and price tags; switch the active source anytime.
- Built-in sources work out of the box; add any OpenAI-compatible / Anthropic-protocol source.

### 🔁 Multi-source failover
When enabled, if the current source fails (rate-limited, error, unreachable) Coday automatically switches to the next available source, reducing sudden interruptions. Off by default, opt-in.

### 🖋️ Custom system prompt (persona)
Set a system prompt per editor, with two injection modes:
- **Replace** — replace the editor's own prompt with yours (tool calls, working directory and other essentials are still preserved).
- **Append** — append your content after the editor's existing prompt.
Restore to default anytime.

### 🎨 Image-generation source
Configure a dedicated image endpoint; image generation in the editor routes through the service you specify.

### 🪪 Identity & quota display
Customize the account info shown in the status bar per editor — independent across editors.

### 🧭 Thinking effort
Globally adjust the model's reasoning effort, from off to maximum.

### 📊 Network & diagnostics
Built-in request/response inspector, logs, and certificate / interception diagnostics — one window to figure out "why isn't it working".

### 🌗 Polish
- Bilingual (English / Chinese) UI, switch anytime.
- Dark theme, system tray quick controls, launch on startup.
- Automatic update check after install.

---

## 💻 Requirements

| Platform | Minimum |
|----------|---------|
| Windows | Windows 10 x64 |

> Windows is the primary platform for now.

---

## 🚀 Getting Started

1. Download and install the latest build from [GitHub Releases](../../releases).
2. Open Coday, add your API source and key under "Relay Config".
3. Click Connect — the first run installs a local CA certificate and sets up interception automatically.
4. Open Cursor, Windsurf / Devin or Kiro and use it as usual.

All AI requests are transparently routed to your configured upstream.

---

## 🆕 What's New

### v0.7.14
- **Devin GetChatMessage aligned with official live capture** — Connect frames, empty/1302 retry, F7 usage, keepalive.
- **Devin Local usage** — SSE usage and Cascade F7 tokens so the 1M progress bar no longer stays at 0.
- **Cursor protocol fixes** from cursor-byok 1.0.1.
- Drop grok user-echo / task restatements that painted duplicate Thoughts.
- Cut capture / fail-dump load; Kiro keepalives no longer open empty Thinking widgets.

### v0.7.5
- **Prompt caching across protocols** — fixed Devin/Windsurf turns losing cache hits; volatile IDE state no longer breaks the cached prefix across Anthropic, OpenAI Chat Completions and OpenAI Responses surfaces.
- **CA serial matching** — the relay now matches the Coday CA by serial number, preventing a stale same-named CA from breaking IDE connections.
- Improved Chinese web-search result relevance.

### v0.7.4
- Windsurf and Devin interception switched to hosts-based redirect for improved compatibility.

### v0.7.0 – v0.7.3
- **OpenClaw center** — workspace file editor, permissions, agents and memory management from a single panel.
- **CLI Skills manager** — cross-tool skill inventory with install-from-ZIP and update checks.
- **CLI MCP manager** — one MCP server library toggled per CLI tool.
- **CLI prompt center** — single-active prompts projected to live files.
- **CLI provider switch** — relay sources written into each CLI agent's own config.
- **OpenAI Responses** — per-source Responses API support; Kiro integration and feature-window deactivation fix.
- **Multi-source failover v2** — source-level routing, image source, cross-window locale sync, model-source v3 refactor.
- Devin rollback crash and parallel tool pairing fix.

### v0.5.5
- **Cross-IDE Skills awareness** — the relay reads project-level rules from all IDE conventions (.windsurfrules, .cursor/rules/, .kiro/steering/, CLAUDE.md, .devin/) regardless of which editor you're using.
- Increased upstream response timeout for long conversations.
- Fixed IDE environment identification — Devin is no longer misidentified as VSCode or Cursor.

---

## ⭐ Star History

[![Star History Chart](https://api.star-history.com/svg?repos=HyperClockUp/Coday&type=Date)](https://star-history.com/#HyperClockUp/Coday&Date)

---

## 💬 Feedback

Questions, feature requests, or just want to chat — scan to join the QQ feedback group:

<img src="docs/assets/qq-group.jpg" alt="QQ Feedback Group" width="240" />

---

## License

Proprietary. All rights reserved.
