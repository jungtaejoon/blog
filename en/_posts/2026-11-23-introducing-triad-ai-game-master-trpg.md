---
title: "A tabletop RPG with an AI game master, free to play right now: Triad (6 rulesets, first come, first served)"
description: I opened Triad, a web service where Claude runs the game and friends play together in the browser. It is free, first come, first served, on credit the operator puts up each month. How the AI is kept from fudging dice, how five openly licensed rulesets were carried over from their source texts, and what a turn costs under a monthly cap.
project: triad
ref: introducing-triad-ai-game-master-trpg
kind: dev
---

I opened [trpg.slop.ai.kr](https://trpg.slop.ai.kr/?utm_source=slop-log). Claude is the game master (GM), and several people gather in one room in the browser to play a tabletop RPG. It is called Triad. There is no sign-up: open a room and share the invite code. There is an English interface (language menu at the bottom right).

> **It's free right now.** As the operator I've put up a month of AI usage (about $113). Anyone can play without signing up, **first come, first served**. The first screen shows what is left in real time; once it's used up it reopens at the next monthly reset, and your adventure stays saved.

![The "Free play this month" notice and remaining credit on the first screen](../../../../../assets/triad/en-1-free.jpg)

It began with one line: "make a tabletop RPG ruleset like GURPS, and turn it into a web service where an AI is the game master." I handed it to Claude Code and steered.

## How it works

1. One person picks a ruleset and a world (sword and sorcery, neon city, misty village, frontier star system, or their own) and opens a room.
2. Everyone makes a character.
3. When the host starts, the GM opens the first scene and players say what they do in chat.
4. Once everyone present has declared an action, or after 3.5 seconds, the GM resolves them together.

If tabletop RPGs are new to you, turn on beginner mode: each turn shows a summary and 3–4 things you could try as cards.

![Beginner mode: under the GM's narration, a summary of where things stand and four suggested actions as cards](../../../../../assets/triad/en-2-beginner.jpg)

## The server owns the dice; the AI owns the story

Hand the whole GM job to an AI and you get familiar problems: it says it rolled and invents the result, or it gives in when a player insists "I succeed."

So there is one rule: **the GM cannot decide rolls, damage or hit points itself.** It calls a tool, the server rolls, and the GM only narrates what came back. The numbers on a character sheet live on the server. Nothing typed in chat changes them.

On screen it unfolds as "narration → dice → outcome", one step at a time, and each player advances with a key or a tap at their own pace.

![Server-rolled 3d6 attack cards between the GM's narration: two sling shots at Wren, both misses](../../../../../assets/triad/en-3-dice.jpg)

When a fight starts the top bar turns red and the GM lays out a zone map, shown as a minimap on the right. Melee only reaches within the same zone, and ranged attacks get harder with distance.

![Combat: the battlefield map with Wren and the goblins on the rubble heap, and the next suggested actions](../../../../../assets/triad/en-4-combat.jpg)

All screenshots are from a real session I played in English (sword and sorcery, beginner mode).

## Six rulesets

You pick the rules when you open a room.

- **Triad**: this service's own rules. Three dice (3d6), characters bought with 120 points, and heavy combat where one or two hits put you in danger.
- **Fate Core**, **SRD 5.2.1 (5E compatible, levels 1–20)**, **Basic Roleplaying**, **Forged in the Dark**, **Dungeon World**: all carried over from their openly licensed source texts.

The main care with the open rulesets was keeping the AI from making rules up from memory.

- The official source (a PDF or the text in a repository) is split into sections and stored on the server. 5E's 364 pages became 1,266 sections; Basic Roleplaying's 303 pages became 1,031.
- When a rule is unclear, the GM looks up the source with a `lookup_rules` tool and applies it.
- Numbers and lists (339 spells, skills, tables) are checked against the source by tests.

## The GM's memory, and cost

In a long adventure the conversation keeps growing, and so does the bill. Three things keep it down.

- **Rules sit in the system prompt**, fixed per room, so they are read from the prompt cache. Measured, about 80% of input came from cache.
- **Campaign notes**: the GM writes the world, its plot ideas and a running summary with a tool. Players never see them.
- **Compaction**: when the conversation gets long, the GM brings its notes up to date and the history is cleared. The next turn starts from the notes, the latest scene and the character sheets.

These are single measurements of the same fight scene on the real API; scenes vary a lot.

| Model / effort | One turn |
|---|---|
| Opus 5.5 / medium | about $0.22 |
| Opus 5.5 / low (current default) | about $0.08–0.15 |
| Sonnet 5.5 / medium | about $0.05 |

I pay for it as the operator and it is free for players, so there is a **monthly cap**. It is first come, first served; once it is used up, no new turns until the next cycle. Rooms and characters stay, and you can continue in the next cycle. The first screen shows what is left.

## What's weak

- A turn takes from a few seconds to over ten. It is not a human GM's quick back-and-forth.
- There is an English interface, but a few labels (like the map legend) are still in Korean.
- Some rules are not automated yet, such as certain 5E magic item effects; the GM reads the source and rules on those.
- Rooms and history are stored in a file, so it runs on a single server for now.

## Try it and judge it

You can open a room right away at [trpg.slop.ai.kr](https://trpg.slop.ai.kr/?utm_source=slop-log), alone or with friends through the invite code. The free credit is first come, first served, so play one while it lasts.

Is an AI game master a gem or slop? Judge it on [the Slop post](https://slop.ai.kr/#/p/e5c75ba1-34a9-4e05-9013-82655a382014), and tell me which ruleset felt most convincing.
