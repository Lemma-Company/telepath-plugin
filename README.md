# Lemma Telepath — plugin package

Connect your own [Telegram](https://telepath.lemma.company) account to
an AI assistant: search the whole chat archive, read the documents, photos and
transcribed voice messages inside it, and reply as yourself.

## Finish setup in Claude

1. Open **Customize → Plugins → Telepath → Connectors**.
2. Choose **Add** or **Connect** for Telepath, then **sign in with Telegram**.
   If it already says **Connected**, continue to the next step.
3. To receive new Telegram messages, follow the
   [setup guide for your device](https://telepath.lemma.company/start#telegram):
   add **@lemma_telepath_bot** in Telegram's **Chat Automation** settings,
   choose which private chats to share, and save the connection.
4. Return to Claude and try: **“What did I miss in Telegram today?”**

Installing the plugin adds the skills. Signing in connects Claude to your
Telepath account; Chat Automation lets Telepath archive new Telegram messages.
Telegram Premium is not required.

**Can't connect from the plugin?** Open the
[Telepath connector listing](https://claude.ai/directory/lemma-telepath) in your
browser and complete the connection there, then return to Claude. On Team and
Enterprise, an organization Owner may need to add the connector first.

Already connected Telegram? Keep your existing connection. Older messages are
not loaded automatically: send `/import` to [the bot](https://t.me/lemma_telepath_bot)
to add a Telegram Desktop export. For other assistants, see
[Other clients](#other-clients).

Telepath runs on Telegram's official business-bot API — a bot you add to your
own account — not on an MTProto user session, so nothing here logs in as you.

## What this repository is

This repository is the complete, open-source plugin package. It is manifests and
assets only: they point an assistant at the hosted Lemma Telepath MCP service at
`https://telepath.lemma.company/mcp`.

The hosted service is operated by Lemma and is not distributed as part of this
plugin. Nothing in this repository runs on your machine or handles your messages.

## Choose your Telegram chats

Use the [device setup guide](https://telepath.lemma.company/start#telegram),
because the Chat Automation menu differs across Android, iPhone and Telegram
Desktop. Choose the private chats the bot may access and save your changes.
New messages from those chats are archived after connection; removing the bot
stops new messages from arriving. Add the bot to a group to archive its new
messages too. Group archiving is free.

Open [@lemma_telepath_bot](https://t.me/lemma_telepath_bot) for connection status,
imports and help. Send `/deletedata` to delete your Telepath archive.

## Other clients

**Cursor** — install **lemma-telepath** from the marketplace.

**Gemini CLI** — `gemini extensions install https://github.com/Lemma-Company/telepath-plugin`

**Grok Build** — open `/plugin`, search for **lemma-telepath**, install.

**Claude Code** —

```
claude plugin marketplace add Lemma-Company/telepath-plugin
claude plugin install lemma-telepath@lemma
```

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
