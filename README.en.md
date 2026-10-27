<div align="center">

<img src="docs/assets/icon.png" width="96" alt="Coday" />

# Coday

### Keep your editor. Use your own models.

**Devin first, plus Cursor, Windsurf, Kiro and VS Code.**
Plug in any OpenAI-compatible or Claude API. Chat, completion, Agent and tool calls keep working as usual.

[![Release](https://img.shields.io/github/v/release/HyperClockUp/Coday?style=flat-square&color=2f6bff)](https://github.com/HyperClockUp/Coday/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/HyperClockUp/Coday/total?style=flat-square&color=22c55e)](https://github.com/HyperClockUp/Coday/releases)
[![Stars](https://img.shields.io/github/stars/HyperClockUp/Coday?style=flat-square&color=f59e0b)](https://github.com/HyperClockUp/Coday/stargazers)
![Platform](https://img.shields.io/badge/platform-Windows%2010%2B-0078d4?style=flat-square)
![BYOK](https://img.shields.io/badge/BYOK-OpenAI%20%7C%20Claude-8b5cf6?style=flat-square)

**[Download the latest build](https://github.com/HyperClockUp/Coday/releases/latest)** · [Quick start](#quick-start) · [Features](#features) · [FAQ](#faq) · [简体中文](./README.md)

<br />

<img src="docs/assets/home.png" alt="Coday home: IDE management, relay config, usage and the Devin suite" width="820" />

</div>

---

## Sound familiar?

- You are mid-task in Devin and the quota notice appears
- You want a model you like better, but the editor hardcodes its own
- You already have an API key, a relay or a company gateway, yet the editor only talks to its own endpoint
- You rotate between three or four editors and redo prompts and rules in each one

**Coday fixes all of it at once.** It runs a transparent local proxy that catches the editor's AI requests, converts them to the protocol you need, and forwards them to the upstream you choose.
Nothing changes on the editor side: chat, completion, Agent and tool calls all keep working.

```
Devin    ┐
Cursor   ├──>  Coday (local transparent proxy)  ──>  OpenAI-compatible / Claude / self-hosted
Windsurf │      protocol conversion / model injection / multi-source routing
Kiro     ┘
```

## Why try it

| | Editor's own model | Hand-edit base_url | **Coday** |
|---|---|---|---|
| Editor config changes | none | required | **none** |
| Protocol conversion | none | on you | **local, automatic** |
| Automatic multi-source failover | no | no | **yes** |
| Per-editor persona | no | no | **yes** |
| Shared project rules across editors | no | no | **yes** |
| Remote-SSH scenarios | limited | limited | **supported (Linux remote)** |
| Request-level visibility | no | packet capture | **built-in console** |

## Features

### The Devin suite (flagship)
More than traffic takeover. Everything Devin-related lives in one panel:

| Feature | What it does |
|---|---|
| Fast Context | Reuses your local Devin sign-in for codebase search, no extra setup |
| Devin Tab completion | Official GetTab Supercomplete, using your own account credentials |
| CLI prompt rewriting | Length-preserving rewrite of the system prompt in local Devin CLI / Devin Local / ACP, with AGENTS.md injection and one-click rollback |
| Devin localization | Simplified Chinese UI, applied across four layers, restorable in one click |

Other editors are supported too, see below.

### One-switch takeover
Flip a switch and Coday takes over Devin, Cursor, Windsurf, Kiro and VS Code (GitHub Copilot). It detects each protocol's differences and converts them, so chat, completion, Agent and tool calls keep working. No `base_url` to hand-edit.

<p align="center">
  <img src="docs/assets/demo-takeover.gif" alt="One-switch takeover across editors" width="700" />
</p>

### Your models, your sources
Paste an endpoint and key, sync the upstream model list in one click. Rename models, tag prices, add custom entries. Works with any OpenAI-compatible or Anthropic-protocol endpoint; switch the active source anytime.

<p align="center">
  <img src="docs/assets/models.webp" alt="Syncing the upstream model list" width="440" />
</p>

### Multi-source failover
If the current source is rate-limited, errors out or is unreachable, Coday switches to the next available source and your conversation keeps going. Off by default, opt-in.

### Cross-IDE Skills awareness
Reads project rule files from every editor convention, so switching editors does not lose project context:

`.windsurfrules` · `.cursor/rules/` · `.kiro/steering/` · `CLAUDE.md` · `.devin/`

### Per-editor persona
Set a system prompt per editor, with two modes:

- **Replace**: swap the editor's own prompt for yours (tool calls, working directory and other essentials are preserved)
- **Append**: add your content after the editor's existing prompt

Restore the default anytime.

### Remote development (Remote-SSH)
With Remote-SSH the language server and the AI traffic run on the remote host, out of a local proxy's reach. Coday tunnels that traffic back to the local proxy over a reverse SSH tunnel, so routing and model injection still apply. Linux remotes supported.

### Visible and accountable
Built-in request console, usage stats, and certificate / interception diagnostics. You can see whether the relay is actually working and what each request cost.

### Small things that matter
- A dedicated image-generation source
- Global reasoning-effort control
- Per-editor status-bar identity and quota display
- Built-in MCP server management, coding pet and scratch notes
- Bilingual UI, dark theme, system tray, launch on startup, automatic update check

## Quick start

1. Download and install the latest build from [Releases](https://github.com/HyperClockUp/Coday/releases/latest)
2. Open Coday, pick a built-in source or enter your own endpoint and key
3. Click Connect. The first run installs a local CA certificate and sets up interception
4. Open Devin (or Cursor / Windsurf / Kiro / VS Code) and use it as usual

That is the whole setup. From then on, the editor's AI requests go through the source you selected.

## FAQ

**Where do my requests go?**
They pass through the local Coday proxy, are converted, and are forwarded to the API source you selected in the UI (a built-in source or your own endpoint). If you are sensitive about data flow, use your own endpoint.

**Why does it install a CA certificate?**
Editor AI traffic is HTTPS. Coday needs a local CA to decrypt it, convert the protocol and forward it. The certificate is used locally only and can be inspected or removed in the system certificate manager.

**Which models and APIs are supported?**
Any OpenAI-compatible (Chat Completions / Responses) or Claude (Anthropic) protocol endpoint.

**Does it support macOS / Linux?**
The client is Windows 10 x64 or later only for now; remote development supports Linux remote hosts.

**My editor cannot reach the network after installing.**
Check the certificate and interception status on the built-in diagnostics page. If that does not help, join the group below or open an Issue.

## What's new

### v0.8.1
- Window corner radius aligned with the system radius, no more gaps at the corners
- Fixed the loading arc animation
- Unified liquid-glass visuals; palette reduced to brand blue plus semantic colors
- Hardened installer, updated minisign signature and auto-update manifest

### v0.7.18
- Desktop pet shows in-progress step and plan progress
- Fixed the Devin Fast Context Unleash toggle

### v0.7.17
- Fast Context hooked into Devin CLI prompt rewriting

### v0.7.16
- Fixed Kiro text turns being treated as truncated and retried repeatedly
- grok-4.x now uses OpenAI Chat Completions per model protocol
- Upstream errors are now visible in the conversation

<details>
<summary>Earlier releases</summary>

### v0.7.5
- **Prompt caching across protocols**: fixed Devin / Windsurf multi-turn cache misses across Anthropic, OpenAI Chat Completions and OpenAI Responses
- **CA serial matching**: prevents a stale same-named CA from breaking IDE connections
- Improved Chinese web-search relevance

Full history: [Releases](https://github.com/HyperClockUp/Coday/releases).

</details>

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=HyperClockUp/Coday&type=Date)](https://star-history.com/#HyperClockUp/Coday&Date)

If Coday saved you an afternoon of config wrangling, a **Star** is the best way to say thanks. It is also how the next person stuck on the same problem finds this repo.

## Feedback

Questions, feature requests or just a chat: scan to join the QQ group, or open an [Issue](https://github.com/HyperClockUp/Coday/issues).

<img src="docs/assets/qq-group.jpg" alt="QQ Feedback Group" width="200" />

## License

Proprietary. All rights reserved.
