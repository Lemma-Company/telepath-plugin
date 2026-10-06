---
name: conversation-brief
description: Read through one person's Telegram conversation and report what it amounts to — what they asked, what was agreed, what is still open. Use when the user names someone and wants the thread rather than a list: "what did Oleg write", "what's the state with Anna", "о чём мы договорились с Иваном", "catch me up on this chat".
---

# One conversation, read properly

This is the deep read of a single thread. For activity spread across many
chats, that's the `catch-up` skill instead.

## Find the person

`telegram_find_chat` first, always — the archive is keyed by `chat_id`, not by
name. Two things make a name miss:

- **Script.** A Russian name may be stored in Latin: "Олег" lives in a chat
  titled "Oleg Nikeshin". If the spoken form finds nothing, try the
  transliterated one before telling the user there's no such chat.
- **Case endings.** People say "от Ивана", not "Иван". Trim the ending and
  retry; the match is a substring, so a shorter stem is the more permissive
  query.

If several chats match, ask which one rather than guessing. Picking the wrong
person and summarising their private conversation is not a recoverable mistake.

## Read it as a conversation

`telegram_get_messages` returns oldest first, which is what you want: a thread
reads forward. Read enough to see the shape of it, not only the last few lines
— the question that started it is usually further up than people expect.

Both sides matter. "What did Oleg write" is really "show me that exchange": his
message without the user's reply beside it is half the story, and the user's own
promises are the half that usually matters more.

## Report what it amounts to

Not a transcript — they can read that themselves. Say:

- **What it's about**, in a sentence.
- **What was asked and what was answered.** Name anything asked that never got
  a reply; that is usually why they're asking you.
- **What the user committed to**, with the time if one was given. "You said
  you'd send the invoice tomorrow" is the most useful line you can produce.
- **Where it stands now** — whose turn it is.

Quote sparingly, and only where the exact wording carries the meaning.

## Attachments are part of the thread

A document, photo or voice note mentioned in the thread is content, not a
placeholder. `telegram_get_file` reads spreadsheets, Word files, PDFs and text
formats; `telegram_get_photo` looks at an image; voice messages carry a
`transcript` field. If the answer depends on what's inside one, open it rather
than reporting that a file exists.

## Then offer the next step

Usually that's a reply — the `draft-reply` skill composes one. Offer; don't
start writing unprompted.
