---
title: "Level a profession with yellow or orange recipes only, and see how to learn the rest — ForgeFlow 0.9.9"
description: ForgeFlow 0.9.9 lets you choose which recipe colours the skill route may use, and a material's craft-uses list shows whether each recipe is learned and how to learn it. The craft plan is now kept per character.
project: forgeflow
ref: forgeflow-route-colors
kind: guide
image: https://jungtaejoon.github.io/blog/assets/img/forgeflow/093-skill-route-panel.jpg
---

Using the craft plan from [0.9.8](/blog/en/2026/11/19/forgeflow-craft-plan/) brought three requests, and 0.9.9 answers them.

## 1. Choose the recipe colours of the skill route

The [cheapest skill route](/blog/en/2026/11/16/forgeflow-skill-route/) picks, for every point, the recipe with the lowest expected cost per point. Green recipes rarely give a point, but cheap materials can still make them the pick. In practice, crafting green items that do not raise the skill is frustrating, and the material count is hard to buy exactly.

So the skill route panel has a **"Recipe colour"** button at the bottom. Each click switches it:

- **Up to green (default):** green recipes are used as before.
- **Up to yellow only:** where a recipe turns green, the route moves on to another one.
- **Orange only:** the route uses only orange recipes, which give a point every craft. The craft count is exact, so you can buy just the materials you need, but it can cost more.

The alternative cards per stretch follow the same limit: with "up to yellow", a recipe that is green there is not offered as an alternative either.

## 2. How to learn recipes in the craft-uses list

Hover a material and press Alt to open the list of recipes that use it. Each recipe is now marked **Learned** or **Not learned**, and the ones you lack get a one-line note on how to learn them:

- learned automatically · skill 1
- trainer · skill 15
- recipe item · drop · skill 45
- recipe item · container/drop · skill 100

Hover an unlearned recipe for the details below its materials: the recipe item, the game tooltip's Forever sources, and the trainer's place and cost if you have talked to one. Sources such as drop or vendor after "recipe item" come from older-version reference data and may differ in Forever.

## 3. One craft plan per character

In 0.9.8 the craft plan was shared by the whole account. Characters have different professions and bags, so each now keeps its own. A plan made in 0.9.8 moves to the first character that opens it.

## Get it

- The full list of changes is in the [0.9.9 update notes](/blog/en/forgeflow/updates/0.9.9/).
- The addon is on [CurseForge](https://www.curseforge.com/wow/addons/forgeflow).
- The Windows app is on the [ForgeFlow website](https://forgeflow.co.kr/): 0.12.4 with addon 0.9.9.

Feedback is welcome as a CurseForge comment or on the [support page](https://forgeflow.co.kr/support). The new version is also on [Slop](https://slop.ai.kr/#/p/3ef64616-47bf-4cba-93af-143a36fb5be1).
