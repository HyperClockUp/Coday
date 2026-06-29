# Coday

English | [简体中文](./README.zh-CN.md)

> A desktop client that lets you keep your familiar AI coding experience in **Cursor**, **Windsurf / Devin** and **Kiro**, while routing the upstream to your own configured API source.

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

### v0.5.5
- **Cross-IDE Skills awareness** — the relay now reads project-level rules from all IDE conventions (.windsurfrules, .cursor/rules/, .kiro/steering/, CLAUDE.md, .devin/) regardless of which editor you're using, so the model always sees your full project instructions.
- Increased upstream response timeout for long conversations.
- Fixed IDE environment identification — Devin is no longer misidentified as VSCode or Cursor.

### v0.5.2
- Fixed: the active-SSH detector no longer flags git transport (git push / fetch over SSH to GitHub / GitLab / etc.) as a Remote-SSH host to intercept.

### v0.5.1
- **Remote SSH interception (new)** — when your editor's language server runs on a remote machine over Remote-SSH, Coday now brings that AI traffic back to the local proxy so routing / model injection still apply (Linux remotes).
- UI/UX polish — the CA-certificate dialog no longer covers the window controls; custom sources can edit their URL and name inline; destructive actions (delete model / host, clear logs) now confirm first; dialogs close with Esc and forms submit with Enter.
- Stability — fixed a startup crash in the packed (protected) build.

### v0.5.0
- Improved context handling for Cursor multi-turn conversations — smoother behavior when switching models or in long chats, with less wasted usage.
- Fixed several issues when calling Claude / OpenAI models under Cursor, for better stability.
- Fixed Token-pack mode requiring a manual "Apply" after switching from custom-API mode — switching modes now takes effect right away.

---

## 💬 Feedback

Questions, feature requests, or just want to chat — scan to join the QQ feedback group:

<img src="docs/assets/qq-group.jpg" alt="QQ Feedback Group" width="240" />

---

## License

Proprietary. All rights reserved.
