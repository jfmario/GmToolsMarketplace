---
name: clean-logs
description: Create a clean session log from raw notes.
disable-model-invocation: true
---

The task is to create a session summary based on adventure knowledge and raw notes.

## Input

The user will provide:

- The Session number.
- The scenes from the written adventure.

Find the RAW notes for that session under `logs/raw/`. The raw file will have GM notes and may also have notes submitted by specific players.

## Task

Consult the written adventure PDFs in `source/adventure/`. Planned or actual deviations from the written adventure are documented in `deviations/`. 

With the context, create a summary of the Session as `logs/cleaned/session-{sessionNumber_2Digits}.md`.

## Notes

- Raw notes were taken quickly and may have numerous mispellings or assumed context. This is why the adventure and deviations must be consulted to get the full picture.
- In the output, avoid Markdown tables because those do not render in the Discord where this will be posted. Use lists instead.