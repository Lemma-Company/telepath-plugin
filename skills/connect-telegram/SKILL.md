---
name: connect-telegram
description: Set up or repair the user's Telegram connection for Telepath, then return to their original request. Use when they ask to connect Telegram or when Telepath tools are unavailable, require authentication, or return no chats. An empty search alone is not evidence of a connection problem. Not for developing or administering the Telepath service or its plugin listings.
---

# Connecting Telegram to Telepath

Check which step is incomplete and explain only that step, in the user's
language. Signing in connects the assistant to a Telepath account. Telegram's
Chat Automation connection lets Telepath receive new messages. These are
separate steps; completing one does not prove the other is done.

## 1. Check access from the assistant

If available, call a cheap read tool such as `telegram_list_chats`. If the tools
work and return chats, continue with the original request. An empty search for
a person, date or phrase does not mean setup is broken.

If tools are unavailable or explicitly require sign-in, give the path for the
client the user is using. Missing tools do not prove a connector is installed.

- **Claude apps and Cowork with the Telepath plugin:** open **Customize →
  Plugins → Telepath → Connectors**. If Telepath is **Not added**, add it from
  this tab, then connect it. If **Not connected**, choose **Connect** and sign
  in with Telegram. If **Connected**, try a read tool before suggesting any
  setup changes. On Team or Enterprise, an organization Owner may need to add
  the connector before members can sign in.
- **Claude fallback:** if the plugin's connection flow fails, or the user has
  no plugin, open https://claude.ai/directory/lemma-telepath in a browser,
  connect Telepath and complete sign-in, then return to Claude. If that also
  fails, ask for the displayed error and offer https://t.me/hellolemma rather
  than repeatedly sending them through sign-in.
- **Claude Code:** open `/mcp`, select the Telepath server and follow the
  authentication prompt in the browser.
- **Other clients:** use the client's connector authentication flow. The MCP
  server URL is `https://telepath.lemma.company/mcp`. Do not give Claude menu
  paths to someone using another assistant.

Signing in identifies the user's Telepath account. It does not enable Telegram
Chat Automation. When using Telegram on another device, return to the original
browser window to finish sign-in. Retry the read tool after sign-in completes.

A timeout or server error alone is not evidence of missing authentication.
If the connector says Connected but tools remain unavailable, ask for the error
or suggest opening a new conversation; do not tell the user to delete a working
connection or repeat login indefinitely.

## 2. Check whether new messages can arrive

Zero chats can mean Telegram is not connected, no selected chat has received a
new message yet, or no history has been imported. Do not claim disconnection
solely from an empty archive or missing older messages.

Ask the user to check connection status in https://t.me/lemma_telepath_bot.
Use any explicit connection status returned by available tools. If Telegram is
not connected, direct them to the guide for their device:
https://telepath.lemma.company/start#telegram

The action is to add **@lemma_telepath_bot** in Telegram's **Chat Automation**
settings, choose which private chats it may access, and save the connection.
Menu paths vary by Telegram app and version; use the maintained guide instead
of assuming the same path on every device. Telegram Premium is not required.
If the menu is missing, ask which Telegram app/device they use and follow the
guide's troubleshooting steps.

If Telegram is already connected, keep the existing connection. Explain the
relevant next step:

- **New messages:** only messages received after connection from selected chats
  are available. Check the chat selection and wait for a new message there,
  then retry the read tool.
- **Older messages:** older history is not loaded automatically. Send `/import`
  to the bot to add a Telegram Desktop export. Do not prescribe reconnection
  to recover old history.
- **Groups:** add the bot to the group to archive its new messages. Group
  archiving is free. Share this only when the user asks about a group.

## 3. Resume the original request

Once access works, do what the user originally asked. For a named person,
resolve the chat with `telegram_find_chat`, then use `telegram_get_messages`.
If no messages are available yet, explain that clearly and give the relevant
next step. Never imply that sign-in alone has already imported their history.
