---
title: "Only greens and blues, and your recipe stays picked — ForgeFlow 0.9.4"
description: ForgeFlow 0.9.4 filters by result quality in the profession window and the auction house, keeps your last recipe per profession, and shows the skill route right after login.
project: forgeflow
ref: forgeflow-grade-filter
kind: guide
image: https://jungtaejoon.github.io/blog/assets/img/forgeflow/094-auction-grade.jpg
---

After adding the cheapest skill route in [0.9.3](/blog/en/2026/11/16/forgeflow-skill-route/) and using it daily, a few small annoyances stood out. I wanted to see only greens and blues worth selling, but greys and whites came along. Switching profession tabs sent my recipe back to the top of the list. And right after login the skill route stayed empty until I visited the auction house. [ForgeFlow](/blog/en/2026/11/11/introducing-forgeflow/) 0.9.4 fixes all three. The screenshots are from the Korean client; the addon also runs in English.

## 1. Filter by result quality

### Profession window

![The ForgeFlow profession filter menu: under sort, learned state and conditions there is a new "Item quality · any of" section with poor, common, uncommon, rare and epic; rare is checked.](/blog/assets/img/forgeflow/094-profession-grade-filter.jpg)

The profession window's **Filter** menu has a new **Item quality · any of** section, coloured as in the game: poor (grey), common (white), uncommon (green), rare (blue), epic (purple).

- Several picks show results of **any** of them: uncommon and rare show greens and blues together.
- It applies **together** with the other conditions. "Skill-up + uncommon" leaves green gear that gives a point and sells well.
- The summary line under the list shows the picked qualities in colour.
- Recipes without an item result (such as enchanting) are hidden while a quality filter is on.

### Crafted goods at the auction house

![The ForgeFlow crafted goods page at the auction house: uncommon is picked next to the list scope, and only 11 green crafted goods are listed.](/blog/assets/img/forgeflow/094-auction-grade.jpg)

The auction house **crafted goods** page has the same filter next to the list scope (learned, interests, skill route candidates and so on).

![The quality menu: all, common, uncommon, rare, epic, poor and uncommon and better, each in its colour.](/blog/assets/img/forgeflow/094-auction-grade-menu.jpg)

- Besides each quality there is **uncommon and better** (green, blue, purple), probably the one you will use most for things to sell.
- The choice is kept the next time you open the auction house.
- The count line says e.g. "uncommon · 11 crafted goods", and tells you to change the quality when none match.

Qualities come from the game. Items not loaded yet are requested and the list fills in as they arrive.

## 2. Each profession remembers your last recipe

![The leatherworking window: the filter leaves only one recipe in the list, yet the last picked Mutated Scale Belt is still selected on the right with its materials.](/blog/assets/img/forgeflow/094-recipe-kept.jpg)

Before, picking a recipe in leatherworking and glancing at first aid made the game select the top of the list when you came back; changing filters did the same. ForgeFlow now remembers **the last recipe you picked, per profession and per character**, and selects it again when you:

- switch profession tabs and come back,
- close and reopen the window,
- change filters so the recipe leaves the list (above).

Only **your own clicks** are remembered, never the game's automatic picks.

### The merchant shortfall panel on open

Because the selection stays put, opening a merchant shows **the shortfall panel for that recipe** at once. Buying still happens only when you click.

## 3. The skill route right after login

![The cheapest skill route panel: leatherworking 147 to 300 with recipes and costs per stretch; the summary says "Includes saved past prices · oldest 1 day ago".](/blog/assets/img/forgeflow/094-skill-route-saved.jpg)

In 0.9.3 the route only filled in after a fresh auction lookup. Two things caused it:

1. **"No listing" records.** A material with nothing listed at that moment was saved as "no listing", which hid its earlier price, so every recipe using it dropped out.
2. **Saved prices ignored right after login.** They were not read until the server was confirmed.

The route now uses **the most recent real price** among the exact quotes, quick quotes and price history, and keeps the last price when a later lookup finds no listing. When prices older than 30 minutes are mixed in, the summary says **"Includes saved past prices · oldest N days ago"**, so you can decide whether to look prices up again. These prices are used only for the route; purchases still use fresh quotes.

## Get it

- The full list is in the [0.9.4 update note](/blog/en/forgeflow/updates/0.9.4/).
- The addon is on [CurseForge](https://www.curseforge.com/wow/addons/forgeflow).
- The Windows app 0.12.2 with addon 0.9.4 is on [ForgeFlow web](https://forgeflow.co.kr/).

Feedback is welcome in the CurseForge comments or on the [support page](https://forgeflow.co.kr/support). The new version is also on [Slop](https://slop.ai.kr/#/p/3ef64616-47bf-4cba-93af-143a36fb5be1).
