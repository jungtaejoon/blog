---
title: "Where does this recipe come from? Sources in the tooltip — ForgeFlow 0.9.11"
description: ForgeFlow 0.9.11 builds in where 1,320 recipe items drop and who sells them. On a Korean client the zone, creature and vendor names are the game's own. Here is how it was made.
project: forgeflow
ref: forgeflow-recipe-sources
kind: guide
image: https://jungtaejoon.github.io/blog/assets/img/forgeflow/profession-window.jpg
---

[0.9.9](/blog/en/2026/11/20/forgeflow-route-colors/) added "how to learn" to the craft-uses list. Where to find a recipe item, though, was only known when the game tooltip showed its "Forever sources" block. That block is gone from the game tooltips now, so nearly every recipe fell back to older data.

## The game does not carry sources

First I checked whether the game can tell us. A diagnostic command listed the client's functions and tooltip data, and I went through the 701 Forever client tables published on the data-mining site wago.tools.

The answer was no. Item names, recipes and reagents live in the client, but which creature drops an item and which vendor sells it live only on the server. Other addons and fan sites show what players saw in game, and addons such as the dungeon journal bundle data from those sites.

## So ForgeFlow now bundles ForeverChanges data

[ForeverChanges](https://foreverchanges.pro) is a Forever fan site that records drops with their counts, vendors and quest rewards from player observations. I fetched its 1,510 recipe item pages slowly and kept the sources of 1,320 recipe items. Tooltips name the source and the date.

Hovering a recipe item in your bags now shows, for example:

```
Sources (from: ForeverChanges)
  Drop: Gnarlpine Augur (Teldrassil) · 1/160
  Drop: Greymist Seer (Darkshore) · 1/212
  Drop: and 17 more locations
```

The same lines appear under "How to learn" of unlearned recipes and in the craft-uses list (Alt), shortened there to one line such as "Recipe item · Drop/Sells · skill 100".

## The game's own names

The site is in English. On a Korean client the names should match what the game shows, so ForgeFlow translates them:

- **Zones, items, currencies and containers:** the Korean names from the Forever client tables.
- **Creatures and vendors:** NPCs from Classic have Korean names on record, so most are shown in Korean.
- **Quests:** the title is loaded from the game by quest id.
- **Vendors new in Forever:** the vendors selling recipes for Merchant's Favor have no Korean name anywhere yet. They start in English; open their shop once and ForgeFlow remembers the name the game shows.

When the game tooltip shows its own "Forever sources" block again, that comes first. Lines marked "Classic data" come from Classic and may differ in Forever.

## Get it

- The full list of changes is in the [0.9.11 update notes](/blog/en/forgeflow/updates/0.9.11/).
- The addon is on [CurseForge](https://www.curseforge.com/wow/addons/forgeflow).
- The Windows app is on the [ForgeFlow website](https://forgeflow.co.kr/): 0.12.5 with addon 0.9.11.

Feedback is welcome as a CurseForge comment or on the [support page](https://forgeflow.co.kr/support). The new version is also on [Slop](https://slop.ai.kr/#/p/3ef64616-47bf-4cba-93af-143a36fb5be1).
