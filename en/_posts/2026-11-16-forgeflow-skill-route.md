---
title: "How much to reach that skill? The cheapest skill route in ForgeFlow 0.9.3"
description: ForgeFlow 0.9.3 plans the cheapest way to your target profession skill from auction and merchant prices, including what your crafted results sell back for.
project: forgeflow
ref: forgeflow-skill-route
kind: guide
image: https://jungtaejoon.github.io/blog/assets/img/forgeflow/093-skill-route-panel.jpg
---

The tedious part of leveling a profession is asking, again and again, "what's the cheapest thing to craft right now?" Orange always gives a point but costs more; yellow and green look cheap but only give a point by chance. Material prices keep moving, and selling the results gets some of the money back. [ForgeFlow](/blog/en/2026/11/11/introducing-forgeflow/) 0.9.3 works it out for you with the **cheapest skill route**. The screenshots are from the Korean client; the addon also runs in English.

## The whole route on one screen

![The ForgeFlow cheapest skill route panel: tailoring from 100 to 150 via Silk Bolt, Bright Yellow Shirt (unlearned), Azure Silk Hood (unlearned) and Azure Silk Cloak (unlearned), with expected crafts and costs; the tooltip on the left shows how to learn the unlearned pattern.](/blog/assets/img/forgeflow/093-skill-route.jpg)

Enter a **target skill** at the bottom of the profession window and press **Skill route**. You get, for each stretch of skill, what to craft, how many times, and what it costs.

- Orange always gives a point; yellow and green give one with a chance that shrinks toward grey. For every skill point the route picks the recipe with the **lowest expected cost**.
- **Unlearned recipes**, and higher-level ones you learn later on, are candidates too, marked as unlearned.
- Choose how results count: **no sale, merchant sale, auction sale (after the fee), or the higher of the two**. If something rarely sells at auction, keep it conservative with the merchant price.
- When you reach the target, the game's repeat crafting **stops automatically** and you are told.

## Where do I learn that recipe?

Hover an unlearned recipe in the route. Recipes learned from a pattern show the **pattern's own tooltip**; trainer recipes show the **required skill and trainer**; automatic ones say so. The game's own Forever source lines are remembered once they appear on screen and shown elsewhere too.

The **learning rank** is fixed as well: about 1,200 recipes showed the Classic rank (e.g. Cured Medium Hide 100 instead of the real 75). It now comes from the game client.

## Prices in seconds

![The ForgeFlow crafted goods page with 393 skill route candidates and the material tree of Watcher's Leather Gauntlets, each material showing its total and unit price × quantity.](/blog/assets/img/forgeflow/093-auction-tree.jpg)

The route needs prices. **Price skill route** on the auction recipe page fetches the lowest price for **50 items per request**. Before, it asked one item at a time, so a few hundred items took a long while; now 129 items took 3 requests and about 3 seconds, with far less load on the server. Prices seen in the last 30 minutes are reused. These quick prices are used only for the route; buying still uses the exact quotes.

Pick **Skill route candidates** in the list on the left to open each candidate, and material rows now show the **total (unit × quantity)** first, next to the sub-craft cost.

## Also new

- **Merchant shortfall**: beside the merchant window, the selected recipe's materials that merchant sells, only what you are short for your craft count, bought only when you click.
- Yellow, green and grey ranks and the current skill-up chance in tooltips; the skill-up filter picks orange, yellow and green.
- Bag deduction no longer counts 0 for some materials with extra fields in their Forever item links.

The full list is in the [0.9.3 update note](/blog/en/forgeflow/updates/0.9.3/). Get it on [CurseForge](https://www.curseforge.com/wow/addons/forgeflow) (public after review); the Windows app 0.12.1 is on [ForgeFlow web](https://forgeflow.co.kr/). Feedback is welcome in the CurseForge comments or on the [support page](https://forgeflow.co.kr/support).
