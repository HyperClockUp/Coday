<div align="center">

<img src="docs/assets/icon.png" width="96" alt="Coday" />

# Coday

### Keep your editor. Use your own models.

**A BYOK gateway for Cursor, Windsurf, Devin and Kiro.**
Plug in any OpenAI-compatible or Claude API. Chat, completion, Agent and tool calls keep working as usual.

[![Release](https://img.shields.io/github/v/release/HyperClockUp/Coday?style=flat-square&color=2f6bff)](https://github.com/HyperClockUp/Coday/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/HyperClockUp/Coday/total?style=flat-square&color=22c55e)](https://github.com/HyperClockUp/Coday/releases)
[![Stars](https://img.shields.io/github/stars/HyperClockUp/Coday?style=flat-square&color=f59e0b)](https://github.com/HyperClockUp/Coday/stargazers)
![Platform](https://img.shields.io/badge/platform-Windows%2010%2B-0078d4?style=flat-square)
![BYOK](https://img.shields.io/badge/BYOK-OpenAI%20%7C%20Claude-8b5cf6?style=flat-square)

[**Download**](https://github.com/HyperClockUp/Coday/releases/latest) · [Quick start](#quick-start) · [Features](#features) · [FAQ](#faq) · [简体中文](./README.md)

<br />

<img src="docs/assets/coday.png" alt="Coday UI" width="380" />

</div>

---

## The problem

You like Cursor, Windsurf, Devin or Kiro, but:

- The built-in quota is not enough, or you prefer a different model
- You already have your own API key, relay or company gateway, and the editor gives you no way to use it
- You use more than one editor and have to redo the config, prompts and rules for each one

Coday runs a transparent local proxy. It takes the AI requests your editor sends, converts them per each protocol, and forwards them to **the upstream you choose**.
Install, connect, open your editor and use it as usual. Nothing changes on the editor side.

```
  Editor (Cursor / Windsurf / Devin / Kiro)
        |
        |  native editor protocol
        v
  Coday  (local transparent proxy: protocol conversion / routing / failover / prompt injection)
        |
        |  OpenAI-compatible / Claude protocol
        v
  Your API source  (official API / relay / company gateway / self-hosted)
```

## Why Coday

| You want | What Coday does |
|---|---|
| Keep your editor | Native takeover; chat, completion, Agent and tool calls keep working |
| Use your own models | Any OpenAI-compatible / Claude API, one-click model sync |
| No interruption when a source fails | Multi-source failover to the next available source |
| One set of rules across editors | Cross-IDE Skills awareness reads each editor's rule files |
| Remote development | Remote-SSH supported via a reverse tunnel back to the local proxy |
| Debuggable when it breaks | Built-in request inspector, logs, certificate and interception diagnostics |

## Features

### Editor takeover
Supports **Cursor, Windsurf, Devin and Kiro**. Each protocol is detected and converted automatically, so chat, completion, Agent and tool calls all stay available.

### Your models, your sources
- Manage multiple API sources in one place: paste an endpoint and key, sync the upstream model list in one click
- Custom models, display names and price tags; switch the active source anytime
- Built-in sources work out of the box; add any OpenAI-compatible or Anthropic-protocol source

### Multi-source failover
If the current source is rate-limited, returns errors or is unreachable, Coday switches to the next available source automatically so conversations are not cut off. Off by default, opt-in.

### Cross-IDE Skills awareness
Coday reads project-level rule files from every editor convention, so you get the full set of project instructions no matter which editor you are in:

`.windsurfrules` · `.cursor/rules/` · `.kiro/steering/` · `CLAUDE.md` · `.devin/`

### Remote development (Remote-SSH)
When your editor connects to a remote machine over Remote-SSH, its language server and AI traffic run remotely. Coday tunnels that traffic back to the local proxy over a reverse SSH tunnel, so routing and model injection still apply. Linux remotes supported.

### Custom system prompt (persona)
Set a system prompt per editor, with two modes:

- **Replace**: swap the editor's own prompt for yours (tool calls, working directory and other essentials are still preserved)
- **Append**: add your content after the editor's existing prompt

Restore the default anytime.

### More
- **Image generation**: configure a dedicated image endpoint
- **Thinking effort**: adjust model reasoning effort globally, from off to maximum
- **Identity and quota display**: customize the account info shown in the status bar, per editor
- **Diagnostics**: request/response inspector, logs, certificate and interception status in one window
- **Polish**: bilingual UI, dark theme, system tray, launch on startup, automatic update check

## Quick start

1. Download and install the latest build from [Releases](https://github.com/HyperClockUp/Coday/releases/latest)
2. Open Coday, pick a built-in source or enter your own endpoint and key
3. Click Connect. The first run installs a local CA certificate and sets up interception automatically
4. Open Cursor / Windsurf / Devin / Kiro and use it as usual

## FAQ

**Does Coday read or upload my code?**
AI requests go through the local Coday proxy, are converted, and are forwarded to the API source you select in the UI (a built-in source or your own endpoint). Which source and key to use is your choice; if you are sensitive about data flow, use your own endpoint.

**Why does it install a CA certificate?**
Editor AI traffic is HTTPS. Coday needs a local CA to decrypt it, convert the protocol and forward it to your upstream. The certificate is used locally only and can be inspected or removed in the system certificate manager.

**Which models and APIs are supported?**
Any OpenAI-compatible (Chat Completions / Responses) or Claude (Anthropic) protocol endpoint.

**Does it support macOS / Linux?**
Windows 10 x64 and later is the primary platform. Linux is supported only as a Remote-SSH remote host.

**It does not connect or nothing happens. What now?**
Open the built-in diagnostics panel to check the certificate, interception status and request logs. If that does not help, join the group below.

## What's new

### v0.8.1
- Window corner radius aligned with the system radius, no more gaps at the corners
- Fixed the loading arc animation
- Unified glass-style visuals; palette reduced to brand blue plus semantic colors
- Hardened installer, updated minisign signature and auto-update manifest

### v0.7.18
- Desktop pet shows in-progress step and plan progress
- Fixed the Devin Fast Context Unleash toggle

### v0.7.17
- Fast Context hooked into Devin CLI prompt rewriting; patch applied best-effort on connect / startup

### v0.7.16
- Fixed Kiro text turns being treated as truncated and retried repeatedly
- grok-4.x now uses OpenAI Chat Completions per model protocol
- Expanded `$ref` in Kiro tool JSON Schemas to avoid empty 400 replies on some models
- Upstream errors are now visible in the conversation

### v0.7.5
- **Prompt caching across protocols**: fixed Devin / Windsurf multi-turn cache misses across Anthropic, OpenAI Chat Completions and OpenAI Responses
- **CA serial matching**: prevents a stale same-named CA from breaking IDE connections
- Improved Chinese web-search relevance

Older versions: see [Releases](https://github.com/HyperClockUp/Coday/releases).

## Requirements

Windows 10 (x64) or later.

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=HyperClockUp/Coday&type=Date)](https://star-history.com/#HyperClockUp/Coday&Date)

If Coday helps you, a Star is the most direct way to support the project.

## Feedback

Questions, feature requests or just a chat: scan to join the QQ group, or open an [Issue](https://github.com/HyperClockUp/Coday/issues).

<img src="docs/assets/qq-group.jpg" alt="QQ Feedback Group" width="200" />

## License

Proprietary. All rights reserved.
