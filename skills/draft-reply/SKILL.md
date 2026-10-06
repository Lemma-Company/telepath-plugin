---
name: draft-reply
description: Compose a reply to someone in the user's Telegram, in the voice of that conversation, and send it once the user approves the exact text. Use when they ask to answer, reply to, or write back to a named person — "ответь Ивану", "write back to Anna", "draft something for Oleg" — or when they accept an offer to reply after reading a thread.
---

# Writing back as the user

The message goes out **from the user's own account**, to a real person, and
cannot be unsent. Everything here follows from that.

## Read before writing

Resolve the person with `telegram_find_chat`, then read the recent messages of
that chat. You're looking for three things, and you cannot guess any of them:

- **What is actually being answered.** The last message is not always the
  question.
- **The language.** Reply in the language the conversation is in, not the
  language the user is talking to you in. A Russian chat gets a Russian reply.
- **The register.** Look at how these two write to each other: length,
  formality, whether they use names, whether they punctuate. A warm chat and a
  contract negotiation do not take the same sentence.

If the thread leaves the user's intent genuinely ambiguous, ask one question.
One — not a questionnaire.

## Draft

Write **one** draft, in full, and show it. One good draft is easier to react to
than three near-identical ones; offer alternatives only when the register is
genuinely open — short and warm versus formal and precise — and then give two,
clearly different.

Keep it the length the conversation uses. People answer short messages with
short messages, and a paragraph where a line is expected reads as written by
someone else.

## Send only on an explicit yes

Show the **exact final text** and name the recipient, then wait. "Send it" after
seeing the text is approval; "yes" to something else is not. If the user edits
the draft, show the edited version and confirm again — approval attaches to
words, not to the idea.

Then `telegram_send_message`, once. Never twice for one request: if you are
unsure whether a send went through, check with `telegram_get_messages` instead
of sending again.

Two cases worth saying out loud when they apply:

- **In a group there is no business connection**, so the message goes out as the
  bot rather than as the user. Say so before sending, because it changes who the
  group sees talking.
- **A connection with no reply permission** can't send at all. The tool says so;
  pass it on with the fix — *Settings → My Account → Chat automation*, where the
  reply right is granted — rather than retrying.

## After sending

Say it went, to whom. Don't paste the message back — they just read it.
