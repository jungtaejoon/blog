---
title: "Gear advice that includes dungeon drops, worked out from your talents and spells — ForgeFlow 0.9.5"
description: Gear by level in ForgeFlow 0.9.5 compares crafted items and dungeon drops and picks the set with a damage and healing simulation of your class, learned talents and the Forever spell data. Plus alternative item cards per slot and alternative recipes in the skill route.
project: forgeflow
ref: forgeflow-gear-sim
kind: guide
image: https://jungtaejoon.github.io/blog/assets/img/forgeflow/095-gear-window.jpg
---

Until now, "Gear by level" in [ForgeFlow](/blog/en/2026/11/11/introducing-forgeflow/) showed the highest item-level crafted item per slot from the recipes you know. Levelling with it, two things fell short: dungeon gear was missing, and a higher item level is not always better for your class. 0.9.5 rebuilds the window. The screenshots are from the Korean client; the addon also runs in English.

## 1. Crafted items and dungeon drops together

![The ForgeFlow gear window for a level-24 hunter: from head to ranged, the recommended item per slot with its source (crafted · leatherworking · material cost, or dungeon · Wailing Caverns · Lady Anacondra · drop 26.9%) and the gain over the current gear.](/blog/assets/img/forgeflow/095-gear-window.jpg)

There are two kinds of candidates:

- **1,320 crafted items.** Choose between the recipes you know and all recipes.
- **1,178 drops from 28 WoW Forever dungeons and raids.** This includes dungeons new to Forever, such as the Drowned City and Alcaz Prison. A button decides whether raid gear is included.

Stats are the **real values as changed in Forever**, not the Classic ones. Rockslicer from the Deadmines, for example, is rare in Forever, item level 23, with +7 Strength. Dungeon gear shows the dungeon, the boss and the drop chance; crafted gear shows the profession and material cost.

## 2. Damage and healing, not item level

The window works out **expected DPS** (damage dealers and tanks) or **expected HPS** (healers) for your character and finds the set with the highest value. The summary reads like this:

> Lv 24 · Beast Mastery talents 15/0/0 · Ranged damage · Expected DPS 77.6 (current gear 71.0, +9.2%) · Spells Arcane Shot·Multi-Shot · mana lasts 100%

The calculation includes:

- **Weapons and physical stats:** weapon damage and speed, attack power, hit, dodge, crit and the crit multiplier. Dual wielding counts off-hand damage and the higher miss chance.
- **Spells:** each rank of your class's main spells with its real Forever amount, spell power coefficient, mana cost and cast time, plus spell crit and hit.
- **Mana:** how long intellect, spirit and mana per 5 keep you casting through a 60-second fight (75 for healers). When mana runs short, a more efficient rank is picked.
- **Talents:** see below.

At your own level it starts from what you wear and keeps swapping a slot whenever something better exists, so slots that already have good gear stay "Keep equipped". Two-handers and one-hand + off-hand are worked out separately and compared; shield tanks only look at a one-hander with a shield.

### The talents you actually learned

Forever's talent window looks like the three Classic trees, but underneath it is the new talent system. ForgeFlow reads **which talent you learned and at what rank** for each node, and takes the numbers from the talent description the game shows at that rank.

Forever talents differ quite a bit from Classic. Cruelty and Malice give their full 5% with a single point, and Mental Strength now adds 15% Intellect. So nothing is guessed; the game's own descriptions are read. The talents that counted are named in the summary, such as "Talents counted: Focused Fire".

### Hunters, Arcane Shot and spell power

I checked in the Forever spell data whether Arcane Shot scales with spell power. Frostbolt (coefficient 0.814) and Smite (0.714) have a coefficient; Arcane Shot has none. So spell power is not counted for hunters. Their shots do cost mana, though, so intellect and mana per 5 still matter. A paladin's Seal of Righteousness and a shaman's Earth Shock do take spell power, so it counts for their melee damage.

## 3. Good-enough alternatives

![Main-hand alternative cards, sorted by the smallest loss against the best (-0.0%, -0.3%, -0.7% and so on), each with its icon, dungeon, boss and drop chance.](/blog/assets/img/forgeflow/095-gear-alternatives.jpg)

When the best item drops 2% of the time, a close second is often quicker to get. **"Alt N ▼"** on each slot opens **item cards** for every item within a chosen loss.

- Choose the range at the top right: within 3%, 5% or 10%, or off. Every item in range is listed, however many.
- Each card shows the icon, name, source, drop chance and the loss (e.g. -0.7% DPS). Hovering shows the game's item tooltip, and a crafted card selects its recipe.

## 4. Alternative recipes in the skill route

![Alternative recipe cards beside the cheapest skill route: for a stretch, the other recipes with expected crafts, net cost and the extra over the cheapest.](/blog/assets/img/forgeflow/095-route-alternatives.jpg)

The cheapest skill route from [0.9.3](/blog/en/2026/11/16/forgeflow-skill-route/) offers alternatives the same way. For each stretch, the other recipes that give a point over the whole stretch appear as cards with expected crafts, net cost and the extra over the cheapest. If you already have the materials for a slightly dearer recipe, you can pick that one. The range is within 10%, 25% or 50%, or off.

## Limits

- Set bonuses, procs (extra attacks, summoned helpers and so on), buffs and enchants are not counted yet. Items with a proc are marked "Special effect not counted".
- For a level other than your own, base stats are estimated per class.
- Tanks are scored on damage too; health and armor only break ties.

## Get it

- The full list is in the [0.9.5 update note](/blog/en/forgeflow/updates/0.9.5/).
- The addon is on [CurseForge](https://www.curseforge.com/wow/addons/forgeflow).
- The Windows app 0.12.3 with addon 0.9.5 is on [ForgeFlow web](https://forgeflow.co.kr/).

Feedback is welcome in the CurseForge comments or on the [support page](https://forgeflow.co.kr/support). The new version is also on [Slop](https://slop.ai.kr/#/p/3ef64616-47bf-4cba-93af-143a36fb5be1).
