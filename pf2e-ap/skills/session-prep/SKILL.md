---
name: session-prep
description: Prepare for the upcoming session.
disable-model-invocation: true
---

The task is to create a markdown file for the GM to reference during an upcoming session.

## Input

The user will provide:

- The session number
- A list of expected scenes to prep

For each scene, the user may optionally include:

- Adjustments or deviations from the written adventure for that scene
- Specific details that must be included in the prep for that scene (this can include anticipated player actions or questions the user wants addressed)

## Task

The task is to create a session prep markdown file as `prep/session-{number}.md`. Pad the session number to two digits (ie, 01, 02, etc).

Consult the written adventure PDFs in `source/adventure/`. Planned or actual deviations from the written adventure are documented in `deviations/`. Also consider the characters (under `party/`).

When compiling the prep, consider:

* Opportunities to highlight strengths and weaknesses.
* Hooks to character backgrounds.
* Opportunities to deliver on players interests or expectations (if defined in their character directories).
* Foreshadowing opportunities.

For sessions after Session 0, logs can be consulted as well.

With the context, create the helpful session prep document with the following:

- If the session is not Session 0, a brief paragraph reminding the players where they are and what the current scene is.
- For each scene the user listed, a scene section with three parts, in this order:
  1. **Pre-read** - a short prose paragraph describing the scene, for the GM to read ahead of the session (what's happening, why, tone). Full scene details aren't needed here since the GM has the adventure book.
  2. **Quick reference** - condensed, scannable lookup material for the scene: names, locations, key NPC motivations, relevant DCs/numbers, and for any enemies their key features/abilities and tactical considerations worth having on hand. Do not include full enemy stat blocks - the GM has those in the book.
  3. **Beat-by-beat** - terse tables or short bullet points walking through the scene's beats in order, meant to be glanced at while running the table, not read as prose. Fold in guidance for any must-include details or anticipated player actions/questions the user flagged for this scene, and enemy tactics notes for encounters.

## Notes

You don't need previous session prep files (if they are even kept). Do not read them.

Feel free to recommend departures from the written material for the following causes:

- To make the adventure more thematic.
- To make the adventure tie more directly into a character's backstory or interests.