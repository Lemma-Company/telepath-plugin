---
name: catch-up
description: Report what arrived in the user's Telegram across their conversations — who wrote, what about, what still needs an answer. Use for "what did I miss", "anything new", "what came in today", "что нового", "что я пропустил", and any question about recent activity spread over several chats rather than one named person.
---

# What came in

The answer to "what did I miss" is **who wrote, not every message they sent**.
Replaying one busy conversation line by line is the usual failure here: the one
person who wrote eight times fills the answer, and the three people who wrote
once each disappear.

## Gather

`telegram_recent_messages` for the period, or `telegram_list_chats` when the
user asks more broadly. Prefer one call with a generous limit over several small
ones — you need to see across chats to know what matters.

If `since` is unclear, use the obvious reading: "today" is today, "what did I
miss" is since the user was last active, which is roughly the last day unless
the archive says otherwise.

## Report

One line per conversation, newest first:

- **Name the person once**, at the start of their line. The archive stores a
  name in both long and short form, so pick one and keep it.
- **Say what it was about**, not the raw text. Two or three messages from the
  same person are one line, not three.
- **Mark whose turn it is.** "Anna asked about the invoice" and "you answered
  Anna" are different facts, and the second one means nothing is owed.
- **Timestamps all or nothing.** If everything is from today, say times only;
  if the span crosses days, date every line. A list where some lines carry a
  date and others don't reads like a bug.
- **Attachments count as content**: a photo, document or voice note is worth a
  mention. Voice messages carry a `transcript` field — read it rather than
  calling it "a voice message".

End with what actually needs the user: unanswered questions, anything they
promised, anything that looks time-bound. If nothing does, say that plainly —
"nothing needs you" is a useful answer.

## Then offer the next step

Name one or two conversations worth opening, and stop. Don't pre-fetch every
chat in full: the user picks, and `telegram_get_messages` reads that one.

## When the archive is empty

No chats at all is a setup problem, not a quiet day — see the
`connect-telegram` skill. A quiet period in a working archive is just a quiet
period; say so and don't send anyone through setup.
