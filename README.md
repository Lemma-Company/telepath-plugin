# Lemma Telepath — plugin package

Connect your own [Telegram](https://telepath.lemma.company) account to
an AI assistant: search the whole chat archive, read the documents, photos and
transcribed voice messages inside it, and reply as yourself.

**Two steps, both free.**

1. **Connect the connector** —
   [claude.ai/directory/lemma-telepath](https://claude.ai/directory/lemma-telepath)
   → **Connect**, then sign in with Telegram. Installing the plugin does not do
   this: the connector ships with it, but stays switched off until you connect it.
   In other clients, see [Step 2](#step-2--connect-your-assistant) below.
2. **Add the bot in Telegram** — **Settings → My Account → Chat automation** →
   add **@lemma_telepath_bot**. Open to every account, no Premium.

Until both are done, the assistant opens an archive with nothing in it.

Telepath runs on Telegram's official business-bot API — a bot you add to your
own account — not on an MTProto user session, so nothing here logs in as you.

## What this repository is

This repository is the complete, open-source plugin package. It is manifests and
assets only: they point an assistant at the hosted Lemma Telepath MCP service at
`https://telepath.lemma.company/mcp`.

The hosted service is operated by Lemma and is not distributed as part of this
plugin. Nothing in this repository runs on your machine or handles your messages.

## Step 1 — add the bot in Telegram

**Do this first.** Without it the assistant connects to an archive with nothing
in it, which is the single most common way this goes wrong.

You add our bot in Telegram under **Settings → My Account → Chat automation**
(**Telegram Business → Chatbots** on Premium)
and choose which conversations it may access. Messages are archived from that
moment on; removing the bot stops it. Every capability is a switch you control
from the bot itself, and `/deletedata` erases everything we hold for you.

Step by step, with screenshots: [telepath.lemma.company/start](https://telepath.lemma.company/start)

## Step 2 — connect your assistant

**Cursor** — install **lemma-telepath** from the marketplace.

**Gemini CLI** — `gemini extensions install https://github.com/Lemma-Company/telepath-plugin`

**Grok Build** — open `/plugin`, search for **lemma-telepath**, install.

**Claude Code** —

```
claude plugin marketplace add Lemma-Company/telepath-plugin
claude plugin install lemma-telepath@lemma
```

**Claude apps** — connect from the [directory listing](https://claude.ai/directory/lemma-telepath).

**Cline** — `cline mcp install lemma-telepath --transport http https://telepath.lemma.company/mcp`

**ChatGPT and other MCP clients** — add
`https://telepath.lemma.company/mcp` as a connector.

On first connect the assistant opens our sign-in page and you log in with
Telegram. That is what tells us which archive is yours; there is no password to
invent. The full walkthrough, with screenshots, is at
[telepath.lemma.company/start](https://telepath.lemma.company/start).

If you install the plugin and get to this later, you do not have to remember any
of it. Ask your assistant about your Telegram messages and it will pick the
setup up from wherever you left off, or run `/lemma-telepath:connect-telegram`
to start it yourself.

## Honest limits

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
