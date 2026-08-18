---
name: ap-question
description: Answer a question about the adventure.
disable-model-invocation: true
---

The task is to give a best-effort answer to the user's question about the adventure.

## Input

The user will provide a question about the Adventure. The may also provide the character of the player asking it.

It may be a straightforward question that is simply a matter of looking the answer up in the adventure PDFs. It might be a less object, more theoretical one that requires a best guess based on context.

## Task

Provide an answer to the question. In addition to the relevant sections of the adventure PDF(s), consider deviations. 

If a character is given, consider that character's directory. It may be worth looking at recent session logs, if available.

