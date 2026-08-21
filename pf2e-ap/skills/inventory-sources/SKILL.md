---
name: inventory-sources
description: Create a README.md in source/ describing the directory contents.
disable-model-invocation: true
---

The task is to create or replace `source/README.md` with a terse file which gives a 1 sentence explanation of each PDF in each of the two source/ subdirectories.

## Instructions

The assumption is that the `source/` directory has two subdirectories:

- `adventure/`: Contains volumes of the adventure(s) belonging to the campaign.
- `rulebooks/`: May contain select rulebooks particularly relevant to the campaign.

Produce `source/README.md` that lists all PDFs in both of those directories with a short description of what they are. For the `rulebooks/` entries, indicate why they might be relevant to the campaign.

## Notes

If the file already exists, you may overwrite it so that it is current.