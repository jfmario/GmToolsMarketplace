
# Pathfinder 2e Adventure Path Plugin

This plugin is designed to support a GM running a published Pf2e Adventure Path.

## Project Structure

This plugin assumes the following structure.

- `deviations/`: A directory for files explaining ways in which the campaign in play deviates from the published material. These files should account for both a) major known departures from the storyline that came as a result of party actions, and b) intentional departures from written material (including those planned for the future by the GM). Specific files are flexible, but a good pattern might be `campaign.md`, book files (`book1.md`, etc.), and a `README.md` explaining.
- `logs/`: A directory for session history.
    - `raw/`: A place to store raw logs taken by the GM and/or appointed players. They should all be combined into one file, `session-##.md`. 
    - `cleaned/`: Reserved for files to be created by the agent, synthesizes and cleaning the `raw/` logs into a clean narrative. These are created by the `/pf2e-ap:clean-logs` skill (a part of this plugin).
- `npcs/`: An optional directory containing markdown files describing key NPCs and their current status.
- `party/`: A directory for player character information. An optional `README.md` here can contain some party details.
    - `<character_name>/`: A directory for the character (and their player). It should at minimum contain a JSON export from FoundryVTT or Pathbuilder of the character, along with relevant markdown files including details such as `backstory.md`, `preferences.md`.
- `prep/`: A directory contain session prep files created by the agent. These files are created by the `/pf2e-ap:session-prep` skill (a part of this plugin). Considered deleting the session prep files after sessions, to remove from the agent any temptations to consult them.
- `source/`: A directory for source PDFs. A `README.md` describing its contents is helpful.
    - `adventure/`: The PDFs of the published adventure. 
    - `rulebooks/`: An optional directory for relevant rulebooks. Only particularly relevant rulebooks, such as Player Core and rulebooks with special relevance to the campaign should be here.

## Plugin Contents

### Commands

The following skills are designed to be invoked by the user as commands.

#### AP Question

*Use this skill when you need to ask the agent a question about the published Adventure Path.*

The agent will provide an answer to a question, considering adventure context (including deviations).

```
/pf2e-ap:ap-question

What kinds of encounters are present in the dungeon at the end of Book 4, Chapter 1?
```

#### Clean Logs

*Use this skill to created cleaned logs from raw real-time session notes.*

During an actual session, you (or a player that you appoint) should take detailed real-time notes. These should be captured in `logs/raw/session-##.md`.

The agent will take that raw input and create a more streamlined session log as `logs/cleaned/session-##.md`. It is instructed to avoid markdown tables in the cleaned log since those do not render well in Discord.

```
/pf2e-ap:clean-logs

Session: 8

We covered the scene with the dragon from the end of Book 2, Chapter 1 and also the initial mystery from Chapter 2.
```

#### Inventory Sources

*Use this skill to generate a README.md index of the `source/` directory.*

The agent will create a README.md listing each PDF in the two `source/` directories along with their roles.

```
/pf2e-ap:inventory-sources
```

#### Recap

*Use this skill to create recap ahead of a following session.*

The agent will provide five paragraph recap which summarizes the previous session(s) at a high level and sets the stage for the coming session.

```
/pf2e-ap:recap

Session: 7

The next upcoming scene (from Book 2, Chapter 1) is the one where the party is attacked by assassins.
```

#### Session Prep

*Use this skill to generate a session prep document for an upcoming session.*

The agent will write a helpful markdown file for reference during the upcoming session. You should tell the agent which scene you plan to open with and a few more scenes you expect you might need to run. If any of those scenes are not from the AP or documented in `deviations/`, provide as much context as you can. You can also include key session goals you have.

It will include a recap and a helpful GM reference for the indicated scenes, consulting the campaign source material and looking for ties to character strengths, weaknesses, and backstories.

```
/pf2e-ap:session-prep

Session: 10

We are planning to start with the opening investigation in Chapter 3 of Book 2. We want to make sure our Investigator is able to shine here, as the player is interested in solving these types of things.

Other scenes that we might have:

- The "Escape to the Forest" series of scenes
- The Haunted Settlement

I'm looking for opportunities to bring in our Witch's backstory as well, because I think it might be fun to tie that into the haunted settlement somehow.
```

## Usage

### Initialization

Take the following steps in any case:

- Add all the PDFs of the published adventure to `source/adventure/`.
- Use the `pf2e-ap:inventory-sources` skill to generate `source/README.md`.
- Optionally, add some relevant PDFs to `source/rulebooks/`.
- Document known devations in markdown files under `deviations/`.
- If any character sheets exist (preferably FoundryVTT or Pathbuilder exports), place them in `party/<character_name>/` along with files like `background.md` and other files that seem helpful. You can use `party/CLAUDE.md` to document expectations the agent can have about character directories.
- Optionally, add NPC markdown files to `npcs/`.

If you are initializing a project for a campaign that has been ongoing, take the following steps:

- Gather sessions logs for the last 1-3 sessions and save them as `logs/raw/session-##.md`. If nothing exists, do your best to write a single raw session log for the most recent completed session.
- Use the `pf2e-ap:clean-logs` skill to create cleaned session logs for each raw log (do this in ascending order).

For both new and legacy campaigns, take the steps in the following section ("Before a Session") and begin the play loop. If you are doing this project on a new campaign, you will skip the `pf2e-ap:recap` call go directly to generated the first prep document with the `pf2e-ap:session-prep` skill. Make sure that the agent is told that this is "Session 0" (or "Session 1" if Session 0 will not or did not include starting scene(s)).

### Before a Session

* Read the relevant sections of the AP and consider the next scene and what's likely to follow.
* Document any planned deviations.
* Use the `pf2e-ap:recap` skill to generate a brief recap to share with players in advance.
* Use the `pf2e-ap:session-prep` skill to generate a helpful prep document.

### During a Session

* Take notes in `logs/raw/session-##.md`. Try to account for every significant event. There is not need to record every skill check or combat turn.

### After a Session

* Use the `pf2e-ap:clean-logs` skill to create a cleaned session log.
* Read the log and document any actual deviations from the written adventure that were not already planned.
* If player options have significantly changed (ie, after a level up), re-export their Foundry or Pathbuilder data and replace the JSON file in their character directory under `party/`.
* If you add any source PDFs, use the `pf2e-ap:inventory-sources` skill to regenerate `source/README.md`.