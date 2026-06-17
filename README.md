# Coday

English | [简体中文](./README.zh-CN.md)

> Keep your familiar AI coding experience in **Cursor** and **Windsurf / Devin**, while routing the upstream to your own configured API source.

Coday is a Windows desktop client. It runs a transparent local proxy that intercepts the AI requests from these editors, converts them per each protocol, and forwards them to the upstream you specify (both OpenAI-compatible and Claude APIs are supported). Install, connect, open your editor and use it as usual — no changes needed on the editor side.

> This repository is only for **installer downloads and automatic update distribution**. It contains no source code.

---

## ⬇️ Download

Grab the latest `Coday_x.y.z_x64-setup.exe` from [Releases](../../releases/latest) and run it. Installed older versions will receive an upgrade prompt on launch.

---

## ✨ Features

- **Takes over Cursor / Windsurf / Devin**: auto-detects and converts each protocol; chat, completion, Agent and tool calls keep working.
- **Custom API sources & model library**: manage endpoints and keys in one place, sync the upstream model list with one click, switch the active source anytime; supports any OpenAI-compatible / Anthropic-protocol source.
- **Multi-source failover**: auto-switch to the next available source when the current one is rate-limited / errors / unreachable (off by default, opt-in).
- **Custom system prompt (persona)**: per editor, "replace" or "append"; replace mode still preserves tool calls, working directory and other essentials, with one-click restore.
- **Image-generation source**: configure a dedicated image endpoint.
- **Identity & quota display**: customize the account info shown in the status bar per editor.
- **Thinking effort**: globally adjust the model's reasoning effort.
- **Network & diagnostics**: built-in request inspector, logs, certificate / interception diagnostics.
- **Bilingual UI, dark theme, system tray, launch on startup, automatic updates.**

---

## 🚀 Getting Started

1. Download and install the latest build.
2. Open Coday, add your API source and key under "Relay Config".
3. Click Connect — the first run installs a local CA certificate and sets up interception automatically.
4. Open Cursor or Windsurf / Devin and use it as usual.

All AI requests are transparently routed to your configured upstream.

---

## 💻 Requirements

| Platform | Minimum |
|----------|---------|
| Windows | Windows 10 x64 |

---

## 🆕 What's New

### v0.5.0
- Improved context handling for Cursor multi-turn conversations — smoother behavior when switching models or in long chats, with less wasted usage.
- Fixed several issues when calling Claude / OpenAI models under Cursor, for better stability.
- Fixed Token-pack mode requiring a manual "Apply" after switching from custom-API mode — switching modes now takes effect right away.

---

## 💬 Feedback

Questions, feature requests, or just want to chat — scan to join the QQ feedback group:

<img src="docs/qq-group.jpg" alt="QQ Feedback Group" width="240" />
