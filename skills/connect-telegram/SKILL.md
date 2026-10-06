---
name: connect-telegram
description: Set up or repair the user's Telegram connection for Telepath, then answer what they actually asked. Use whenever they ask about their Telegram messages, chats, voice notes or files; mention Telegram, Телеграм or переписка; or when a Telepath tool is unavailable, returns nothing, or asks for authentication.
---

# Connecting Telegram to Telepath

Telepath reads the user's own Telegram through a hosted MCP server. It needs two
halves, and a half-connected setup looks exactly like an empty inbox — which is
why this skill exists. Work out which half is missing, fix that one, then go back
and do what the user originally asked.

**Do not stop at "you're connected now."** The user asked a question. Setup is
the detour, not the destination.

## Step 1 — is the connector authenticated?

Call a cheap Telepath tool, such as `telegram_list_chats`.

**If the tool is missing, fails to connect, or reports a 401 / authentication
error**, the connector is installed but not signed in. Say so briefly and give
the path for where the user is:

- **Claude Code**: run `/mcp`, pick **telepath**, and follow the browser.
- **Claude app, Cowork, or anywhere else**: open the connector settings and
  connect **Telepath**; a browser window opens.

Signing in is a Telegram login — there is no password to invent. It is what tells
the server whose archive this is. Wait for the user to say they are done, then
try the tool again.

## Step 2 — is Telegram itself connected?

A signed-in account with no bot added in Telegram has an empty archive. If the
tool succeeds but returns no chats, or a search over a period the user says
should have messages comes back empty, this is the missing half.

Tell them, in their own language, to open Telegram and do this once:

> **Settings → My Account → Chat automation** → add **@lemma_telepath_bot**

Worth adding, briefly, only where it helps:

- It is available on **every** Telegram account — no Premium, no paid plan.
- By default the bot gets **all** private chats. Anything excluded under
  *Chats the bot can access* never reaches the server at all.
- Archiving starts **from that moment**. Earlier history is not imported unless
  they ask for it: `/import` in the bot walks through a Telegram Desktop export.
- Groups work separately: add the bot to a group, then write one message there
  yourself to claim it.
- Step by step with pictures: https://telepath.lemma.company/start

The bot sends a confirmation in Telegram once it connects. That is the signal
the second half is done.

## Step 3 — answer the original question

As soon as the tools return real chats, carry out the request that started all
this. If the user asked what Yulia wrote, resolve the name with
`telegram_find_chat`, then read it with `telegram_get_messages`. Do not make them
ask a second time.

## When nothing is wrong

If the tools already work and return chats, this skill has nothing to do: use the
tools and answer. Never walk a connected user through setup.
