---
title: "A dungeon survivors game inside WoW: Dungeon Rush"
description: Dungeon Rush is a survivors-style minigame addon for WoW Forever. Pick one of nine classes and fight through the dungeons, boss by boss.
project: dungeonrush
ref: introducing-dungeon-rush
kind: guide
image: https://jungtaejoon.github.io/blog/assets/img/dungeonrush/logo.png
---

Waiting on auction prices or a group, I kept wishing for something quick to play without leaving the game. So I made **[Dungeon Rush](https://www.curseforge.com/wow/addons/dungeon-rush)**, a minigame addon that runs inside WoW Forever. Like [ForgeFlow](/blog/en/2026/11/11/introducing-forgeflow/), I built it with Claude Code and tuned it by playing it in game. It is under review on CurseForge right now.

## How it plays

Open it with `/dungeonrush` or `/drush`. Pick a class and a dungeon and move with WASD; your skills fire on their own. Space or Shift dashes, and every level up offers three cards to choose from.

- **Classes and talents.** Nine classes with three specs each. Every skill is a real class ability turned into an automatic attack, with its name and icon from the game. Each level gives a talent point; deeper tiers open as you spend, and the end of a tree completes the spec's signature skill.
- **Dungeons and bosses.** 35 dungeons in level order, starting with Ragefire Chasm, each with its real bosses in kill order. Between bosses you choose a road of trash, elite, campfire, merchant and event rooms.
- **Not just for ranged.** Every boss has a move that punishes standing far away, and every dungeon has monsters that close the gap fast. Melee and ranged both have to keep moving.
- **Levelling never makes you safe.** Monsters get tougher and more numerous with every room and every level. Choose Story, Normal, Heroic, Mythic, or Mythic+ keystones from +2 to +20 with Fortified, Tyrannical, Raging, Volcanic and Bolstering.
- **WoW's own sounds.** Footsteps, hits, level-ups, buttons and dashes use sounds from the game client.

## What lasts

Emblems from every run buy permanent upgrades, classes gain mastery, clears open the next dungeons, and a run in progress continues after a /reload.

Turn on **game progress backup** in the ForgeFlow Windows Companion 0.12.0 and your progress is kept on your account, so it comes back on a new PC or after a reinstall. It is off by default.

## Safe to play

Entering combat pauses the game at once, closes the window and gives your keyboard back. It makes no protected calls and no network traffic.
