# Lemma Telepath — plugin package

Connect your own [Telegram Business](https://telepath.lemma.company) account to
an AI assistant: search the whole chat archive, read the documents, photos and
transcribed voice messages inside it, and reply as yourself.

Telepath runs on the official Telegram Business API — a bot you add to your own
account — not on an MTProto user session, so nothing here logs in as you.
Connecting a business bot does not require Telegram Premium.

## What this repository is

This repository is the complete, open-source plugin package. It is manifests and
assets only: they point an assistant at the hosted Lemma Telepath MCP service at
`https://telepath.lemma.company/mcp`.

The hosted service is operated by Lemma and is not distributed as part of this
plugin. Nothing in this repository runs on your machine or handles your messages.

## Layout

| File | Read by |
|---|---|
| `plugin.json` | Agent Plugins clients |
| `.cursor-plugin/plugin.json` | Cursor |
| `mcp.json` | both of the above, for the server address |
| `.grok-plugin/plugin.json` | Grok Build |
| `.mcp.json` | Grok Build, for the server address |
| `assets/logo.png` | listings |

The two MCP files hold the same server address under the two names different
hosts look for; `mcp.json` is the Agent Plugins name, `.mcp.json` the one Grok
reads. Change the address in both or in neither.

## Installing

**Cursor** — install **lemma-telepath** from the marketplace.

**Grok Build** — open `/plugin`, search for **lemma-telepath**, install.

**Claude** — connect from the [directory listing](https://claude.ai/directory/lemma-telepath).

**ChatGPT and other MCP clients** — add
`https://telepath.lemma.company/mcp` as a connector.

On first connect the assistant opens our sign-in page and you log in with
Telegram. That is what tells us which archive is yours; there is no password to
invent. The full walkthrough, with screenshots, is at
[telepath.lemma.company/start](https://telepath.lemma.company/start).

## Before you connect

You add our bot in Telegram under **Settings → Telegram Business → Chatbots**
and choose which conversations it may access. Messages are archived from that
moment on; removing the bot stops it. Every capability is a switch you control
from the bot itself, and `/deletedata` erases everything we hold for you.

Telepath is not end-to-end encrypted: searching and transcribing require our
servers to read your messages. Each account's archive is a separate database on
a disk that is encrypted at rest. We say this plainly rather than implying
otherwise — the details are in the
[privacy policy](https://telepath.lemma.company/privacy).

## Links

[Documentation](https://telepath.lemma.company/start) ·
[Privacy](https://telepath.lemma.company/privacy) ·
[Terms](https://telepath.lemma.company/terms) ·
[Support](https://telepath.lemma.company/support)

Built and operated by [Lemma](https://lemma.company).

## Licence

The plugin package in this repository is MIT licensed — see [LICENSE](LICENSE).
The hosted service it points at is governed by its own
[terms](https://telepath.lemma.company/terms).
