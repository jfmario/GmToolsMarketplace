---
name: recap
description: Create a recap paragraph based on the cleaned session log.
disable-model-invocation: true
---

The task is to provide a recap paragraph based on a session log.

## Input

The user will provide:

- The session number of the session to recap.
- Information about the next expected scene.

Find the session log for that session under `logs/cleaned/`.

## Instructions

The task is provide a recap with the following paragraphs, each 1-3 sentences.

- A paragraph which references the adventure path arc.
- A paragraph which references the book arc.
- A paragraph which references the chapter arc.
- A paragraph about the immediately preceding scene(s).
- A paragraph which sets the current scene.

Note that the earlier paragraphs may be sparse - the players may not have context on much of the adventure as a whole or the book based on where they are. In such cases, those might be short, 1 sentence paragraphs vaguely referencing the theme may be enough.

Consult the written adventure PDFs in `source/adventure/`. Planned or actual deviations from the written adventure are documented in `deviations/`. 

## Notes

- Do not directly reference books or chapter numbers.