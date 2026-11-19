---
title: "Plan several crafts at once and buy only what you lack — ForgeFlow 0.9.8 craft plan"
description: The craft plan in ForgeFlow 0.9.8 groups several recipes and craft counts, totals their materials, subtracts your bags and lets you buy only the shortfall from merchants and the auction house. Ctrl+click a material to mark its merchants on the map.
project: forgeflow
ref: forgeflow-craft-plan
kind: guide
image: https://jungtaejoon.github.io/blog/assets/img/forgeflow/098-craft-plan.jpg
---

Until now the merchant shortfall purchase in [ForgeFlow](/blog/en/2026/11/11/introducing-forgeflow/) counted one recipe at a time: pick a recipe, set the craft count at the merchant and buy what that recipe lacks. Levelling a profession, though, you often mix bags, cloaks and shoulders, and thread and dye are shared between them. Buying recipe by recipe gets the totals wrong. 0.9.8 fixes that. The screenshots are from the Korean client; the addon also runs in English.

## 1. Craft plan: write down everything you will make

![ForgeFlow craft plan page. On the left: Bolt of Silk Cloth ×5, Red Linen Bag ×6, Reinforced Linen Cape ×4, Double-stitched Woolen Shoulders ×4. On the right: fine thread, coarse thread, red dye, linen, silk and wool with needed, owned and short amounts, the number of merchants selling each and the distance to the nearest.](/blog/assets/img/forgeflow/098-craft-plan.jpg)

The crafting workshop has a new "Craft plan" tab. Add recipes and counts on the left; the right side totals the materials for the whole plan.

- **Needed · owned · short.** Owned counts your bags. Short materials come first.
- **What the plan crafts is subtracted.** Plan bolts of linen together with a bag that uses them, for example, and the need drops by the bolts the plan makes.
- **Where to buy.** Materials sold by merchants show how many merchants sell them and the distance to the nearest; the rest say "auction house".

Add recipes from three places:

- "+ Add to craft plan" on the workshop
- the button on the profession window's panel (left click +1, right click −1)
- "+ Add selected recipe" on the plan page

## 2. Buy it all at the merchant

![The shortfall window beside a merchant with the "Craft plan (4)" tab selected: buy buttons for 12 coarse thread, 14 fine thread and 6 red dye, "3 short materials not sold here · Show on map", a total of 16 silver 38 copper and "Buy all shortfalls".](/blog/assets/img/forgeflow/098-merchant-plan.jpg)

Open a merchant and the shortfall window gets a "Craft plan" tab. It lists the plan materials this merchant sells with the missing amounts, and "Buy all shortfalls" buys them in whole merchant bundles. Materials this merchant does not sell are counted separately and can be marked on the map right away.

The "Selected recipe" tab still buys for one recipe. It only buys on your click and never in combat.

For auction materials, "Buy at auction" on the plan page opens the purchase page with the missing quantity filled in; you press the final buy button.

## 3. Ctrl+click a material to see its merchants on the map

Finding who sells a material was a lot of walking around. Now **Ctrl+click** a material anywhere (bags, the profession window's reagent slots, merchants, chat links) and its merchants are marked on the world map.

- **Only merchants of your faction** are shown.
- **The nearest merchant** gets a large star and the game's map pin.
- **Marks add up** as you click more materials. A bar at the top of the map shows which materials are marked, with their icons and names.
- **Clearing.** Right click a material's icon in the bar to clear it, or "Clear all" for everything. The map pin ForgeFlow placed goes too; pins you placed stay.

It started as Alt+click, but Alt already opens the tooltip's list of recipes using a material. So the default is Ctrl+click, and the plan page lets you switch to Ctrl+Alt+click or Alt+click.

Merchant locations cover 39 materials and 520 merchants from WoW Forever data, plus merchants you or shared data have seen.

## 4. Also

- **Auction sort by required level.** Item search results can be sorted by minimum required level, cheaper first on ties.
- **Gear fixes.** Equipped items missing from the gear list (quest rewards and the like) read their equip effects from the tooltip, and damage casters count their wand for the time they are out of mana.

## Limits

- 19 of the 58 materials sold by merchants have no location data yet (crystal vials, rune thread and others). They show only merchants seen in game.
- Owned amounts count bags only, not the bank or mail.
- Whether an intermediate is crafted depends on whether its recipe is in the plan; otherwise it is treated as bought.

## Get it

- The full list of changes is in the [0.9.8 update notes](/blog/en/forgeflow/updates/0.9.8/).
- The addon is on [CurseForge](https://www.curseforge.com/wow/addons/forgeflow).
- The Windows app is on the [ForgeFlow website](https://forgeflow.co.kr/): 0.12.4 with addon 0.9.8.

Feedback is welcome as a CurseForge comment or on the [support page](https://forgeflow.co.kr/support). The new version is also on [Slop](https://slop.ai.kr/#/p/3ef64616-47bf-4cba-93af-143a36fb5be1).
