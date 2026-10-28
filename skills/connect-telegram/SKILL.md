---
name: connect-telegram
description: Set up or troubleshoot the user's Telepath connection, then return to their original request. Use for plugin setup, connection questions, missing Telepath tools, Unknown tool errors, or authentication errors. An empty search alone is not a connection failure. Not for administering Telepath or developing its integrations.
---

# Connect Telegram

Explain the missing step in the user's language. Signing in connects the
assistant to a Telepath account; Telegram Chat Automation lets Telepath receive
new private-chat messages. Completing one does not prove the other is done.

## Check assistant access

If tools are available, use `telegram_list_chats` or the read tool needed for
the original task. Returned chats establish archive access, not necessarily an
active Telegram connection. A search with no matches does not establish a
connection problem.

If tools are missing, require authentication, or return `Unknown tool` or
`Tool not found`, explain that tool access is unavailable. A loaded skill does
not prove the connector is added or signed in. Use the tools exposed by the
host; do not invent names or namespace prefixes or repeat an unavailable call.
The error alone says nothing about whether Telegram is connected or the archive
is empty. If sign-in status is unknown, ask whether it was completed.

For a missing connector or incomplete sign-in, give the appropriate path:

- **Claude apps and Cowork with the plugin:** open **Customize → Plugins →
  Telepath → Connectors**. **Not added** needs **Add**, then **Connect**;
  **Not connected** needs **Connect** and **Sign in with Telegram**.
- **Claude without the plugin, or if that flow fails:** open the
  [Telepath connector listing](https://claude.ai/directory/lemma-telepath),
  add or connect it, and sign in. Do not create a second connection if an
  existing one works. On Team or Enterprise, an organization Owner may need
  to enable the connector first.
- **Claude Code:** open `/mcp`, select Telepath, and follow the authentication
  prompt in the browser.
- **Other assistants:** use their connector authentication controls. The server
  is `https://telepath.lemma.company/mcp`; do not give them Claude menu paths.

If approval happens in Telegram on another device, return to the original
browser to finish. Never ask for login codes, passwords, or tokens in chat.
For first-time setup, also include the short Telegram step below, so the user
knows signing in alone does not connect private chats.

After sign-in, retry one read using an available tool. If the connector is
Connected but tools are still unavailable, suggest a new conversation and
offer https://telepath.lemma.company/support if the problem persists. Do not
remove a working connection, loop through login, or claim Chat Automation
fixes an Unknown tool error. A timeout or server error is not proof of missing
authentication; explain the actual error.

## Connect Telegram chats when needed

Use explicit connection status from a tool response first. If status is unknown,
ask whether Chat Automation is connected or direct the user to the bot's status
screen. An empty archive can also mean no new messages have arrived yet or no
older history was imported.

When Telegram needs connecting, give the action directly:
**Open Telegram settings → Chat Automation → add @lemma_telepath_bot → choose
private chats → save.** Use the same Telegram account used for sign-in.
Telegram Premium is not required.

Use the device already known; give its manual path when useful:

- Android: **Settings → Account → Chat automation**; tap **✓** to save.
- iPhone/iPad: **Settings → Edit → Chat Automation**; go **Back** to save.
- Telegram Desktop: **Settings → ⋮ → Edit profile → Chat automation**;
  go **Back** to save.

Menu paths vary by app and version. If the menu is missing, the path fails, or
the user needs screenshots, offer https://telepath.lemma.company/start#telegram.
Ask which Telegram app they use only when needed; do not make visiting the guide
a prerequisite for following the direct steps.

If Telegram is already connected, preserve the connection. New messages from
selected chats are archived while it is active; older history does not appear
automatically. Import is optional and can be done later from a computer: send
`/import` to the bot for an upload link, then upload a Telegram Desktop JSON
export without media. Do not require importing or reconnecting to start using
new messages. Discuss groups or channels only when relevant: groups need the
bot with message access, and channels need connection and authorization through
the bot.

## Return to the request

Once access works, carry out the original request. For a setup-only request,
verify with a small read and show a brief result unless the user wanted only
instructions. If the archive is empty, say new messages will become available
as they arrive and offer older-history import as optional. Do not promise a
useful digest before any messages exist, or invent example conversations.
Verification does not authorize sending, reacting, marking read, or other changes.
