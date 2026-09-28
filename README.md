# Telepath plugin for Grok Build

Connect Grok Build to your own [Telegram Business](https://telepath.lemma.company)
account: search the whole chat archive, read the documents, photos and
transcribed voice messages inside it, and reply as yourself.

Telepath runs on the official Telegram Business API — a bot you add to your own
account — not on an MTProto user session, so nothing here logs in as you.

## Installation

In Grok Build open `/plugin`, search for **lemma-telepath**, and install.

Two halves are needed, and the second one is the step people miss:

1. In Telegram: **Settings → Telegram Business → Chatbots**, add
   `@lemma_telepath_bot`. That is what starts archiving your chats. Telegram
   Premium is required for Business features.
2. In Grok Build: connect the plugin and sign in with the same Telegram account.

The illustrated walkthrough lives at <https://telepath.lemma.company/start>.

## Authentication

The plugin connects only to `https://telepath.lemma.company`. Authentication is
OAuth 2.1 with PKCE and dynamic client registration — no API key, no token to
paste into chat. Identity comes from the Telegram Login widget, so the account
you sign in with is the archive you get.

Network endpoints:

- `https://telepath.lemma.company/mcp` — hosted MCP (streamable HTTP)
- `https://telepath.lemma.company/authorize`, `/token`, `/register` — OAuth 2.1 + DCR
- `https://telepath.lemma.company/oauth/login` — human sign-in, which loads the
  Telegram Login widget from `oauth.telegram.org`

Credentials: a Telegram account with Telegram Business and our bot added to it.
Tokens are issued per account and are audience-checked; read-only clients get
the search and read tools only, without the ones that send.

## What it touches

Each account gets a physically separate archive, and the tools only ever reach
that one. Messages are processed on Telepath's servers to be searchable — this
is not end-to-end encrypted, and the
[privacy page](https://telepath.lemma.company/privacy) says so plainly. If you
turn on voice transcription, that audio is sent to Mistral for transcription;
everything else stays on our server, whose disk is encrypted at rest.

`/deletedata` in the bot's own chat erases everything we hold for you.

## License

Proprietary. Use of the hosted service is governed by the
[terms](https://telepath.lemma.company/terms). Questions: hello@lemma.company
