# Telepath

![Telepath logo](assets/logo.png)

Your Telegram, inside Claude. Catch up on conversations, find a message or
shared document, read available voice transcripts, and draft a reply using
your authorized Telegram archive.

## Connect in Claude

1. After adding the plugin, open **Customize → Plugins → Telepath → Connectors**.
2. If the connector is **Not added**, choose **Add**, then **Connect**. If it is
   **Not connected**, choose **Connect**. Complete **Sign in with Telegram**;
   if you approve on another device, return to the original browser to finish.
   If it already says **Connected**, keep that connection.
3. To receive new private-chat messages, open Telegram's **Chat Automation**,
   add **@lemma_telepath_bot**, choose the chats to share, and save:
   - Android: **Settings → Account → Chat automation**; tap **✓**.
   - iPhone/iPad: **Settings → Edit → Chat Automation**; go **Back**.
   - Telegram Desktop: **Settings → ⋮ → Edit profile → Chat automation**;
     go **Back**.
4. Return to Claude and try **“Show my latest available Telegram messages.”**

Telegram Premium is not required. Installing the plugin, signing in, and
connecting Telegram chats are separate steps. Menu paths vary by Telegram app
and version; use the [device guide](https://telepath.lemma.company/start#telegram)
if you cannot find the menu or need screenshots.

If the plugin's connection flow fails, use the
[Telepath connector listing](https://claude.ai/directory/lemma-telepath), finish
sign-in there, and return to Claude. On Team and Enterprise, an organization
Owner may need to enable the connector before members can sign in.

## Try it

- “Help me connect Telegram and check that it works.”
- “Show my latest available Telegram messages.”
- “Summarize my most recent Telegram conversation.”

The plugin includes five skills: connection setup, catching up across chats,
briefing one conversation, finding a message or file, and drafting a reply.
You can also use the connector's tools for Notes, tasks, reminders, and
authorized channel actions; those features do not need a separate skill each.

## New messages and optional history

New messages from selected chats are archived while the Telegram connection is
active. A newly connected archive can be empty until messages arrive. Signing
in alone does not connect private chats or import history.

Importing older history is optional and can be done later from a computer.
Send `/import` to [@lemma_telepath_bot](https://t.me/lemma_telepath_bot) for an
upload link, then upload a Telegram Desktop JSON export without media. Imported
history includes text and message details; exported media files are not uploaded.

Add the bot to a group to archive new messages it has permission to receive.
Connect channels through the bot; channel actions require the appropriate
ownership and bot permissions.

## Permissions and limits

Results cover the available Telepath archive, not every Telegram conversation.
Message search covers text, captions, and available voice/video transcripts;
it does not search file contents or filenames directly. Claude can inspect
photos and read supported documents with the file tools when media is available.

Private chats use Telegram's official Business API, not an MTProto user session.
You choose which chats the bot may access and whether it may send messages.
Private Business sends and edits require the appropriate permissions and an
incoming message in that chat within the previous 24 hours. Group replies use
the bot's name. Drafting does not authorize sending: the exact content and
recipient must be approved under the tool's confirmation requirements.

If a send result is uncertain, the skills direct Claude to check rather than
automatically send again. An archived conversation does not prove that sending
is currently permitted.

## Troubleshooting

- **Missing tools, Unknown tool, or authentication errors:** use the
  `connect-telegram` skill to check connector access. These errors alone do not
  prove that Telegram is disconnected or that the archive is empty.
- **Connected but no messages:** check Telegram connection status and selected
  chats in the bot. New messages may not have arrived yet. Importing old history
  is optional; repeating sign-in does not recover it.
- **A search finds nothing:** try a narrower search or inspect the relevant
  conversation. An empty search is not evidence that setup is broken.
- **Access still fails after sign-in:** try a new conversation and contact
  [support](https://telepath.lemma.company/support) with the displayed error.
  Never share login codes or tokens in chat.

## Service and data

This repository contains manifests, skills, and assets that connect assistants
to `https://telepath.lemma.company/mcp`. The plugin starts no local server and
contains no account credentials. Claude sends tool requests to the hosted
Telepath service under the user's authorization. The service is operated by
Lemma and is not distributed with this plugin.

Telepath stores the authorized Telegram archive and processes messages and
available media to provide search, file reading, and transcription. It is not
end-to-end encrypted: these features require server-side access to content.
The [privacy policy](https://telepath.lemma.company/privacy) describes collection,
storage, processing, and retention.

Use the bot for connection status, imports, and settings. `/deletedata` asks for
confirmation before permanently deleting your Telepath archive, notes, settings,
and subscription record. Remove the bot from Chat Automation to stop new
private-chat collection.

## Other clients

**Claude Code:**

```text
claude plugin marketplace add Lemma-Company/telepath-plugin
claude plugin install lemma-telepath@lemma
```

Open `/mcp`, select Telepath, and complete authentication in the browser.

**Cursor:** install **lemma-telepath** from the marketplace.

**Gemini CLI:** `gemini extensions install https://github.com/Lemma-Company/telepath-plugin`

**Grok Build:** open `/plugin`, search for **lemma-telepath**, and install.

**Cline:** `cline mcp install lemma-telepath --transport http https://telepath.lemma.company/mcp`

**Other MCP clients:** add `https://telepath.lemma.company/mcp` through the client's
connector controls and sign in with Telegram. The Telegram chat connection is
still required for collecting new private messages.

## Links and license

[Setup guide](https://telepath.lemma.company/start) ·
[Privacy](https://telepath.lemma.company/privacy) ·
[Terms](https://telepath.lemma.company/terms) ·
[Support](https://telepath.lemma.company/support)

Built and operated by [Lemma](https://lemma.company).
The plugin package is MIT licensed; see [LICENSE](LICENSE).
The hosted service is governed by its own [terms](https://telepath.lemma.company/terms).
