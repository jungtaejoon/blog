---
title: "claude-warmup 0.3: make Claude's 5-hour limit reset right at your busiest time"
description: Set a peak time and claude-warmup works backward so a 5-hour window resets right then. A day doesn't divide into 5-hour windows, so you choose where the 4 empty hours go.
project: claude-warmup
ref: claude-warmup-peak-time
kind: dev
image: https://jungtaejoon.github.io/claude-warmup/og.png
---

[claude-warmup](https://jungtaejoon.github.io/claude-warmup/) is a small tool that keeps a Claude Pro/Max 5-hour window always running. It opens a new window as soon as the last one ends, so whenever you sit down, your first message doesn't start a full 5-hour wait.

Using it, I noticed one thing missing. I get up at about the same time every day, and my busiest hours are about the same too. So the best thing would be a reset **right at that time**. Version 0.2 added a peak time, and 0.3 lets you choose the empty hours yourself.

## What a peak time is

Tell it "weekdays at 11:30 are my busiest," and it works backward. For a reset at 11:30, that window has to start at 06:30, the one before at 01:30, and so on.

## A day leaves 4 hours over

There's a catch. A day is 24 hours and a window is 5, so four windows back to back fill 20 hours and **4 hours have no window.** As long as windows line up with the peak, those 4 empty hours have to go somewhere.

In 0.2 they landed right after the peak (11:30–15:30), right after the busiest time, which is the worst place. So from 0.3 **you choose where they go.** Setting a peak lists the five choices and asks for a number.

```
$ claude-warmup config peak 11:30 weekdays
✓ peak = 11:30 weekdays
  A day is 24 hours, so lining windows up with weekdays 11:30 leaves 4 hours with no window. Where should they go?
    1) 11:30–15:30  (right after the peak)
    2) 16:30–20:30
    3) 21:30–01:30
    4) 02:30–06:30
    5) 07:30–11:30  (right before the peak)
  Number (Enter to decide later): 4
✓ Empty hours (no window): 02:30–06:30
  Pings now line up at 06:30, 11:30, 16:30, 21:30, so a window resets right at weekdays 11:30.
```

I left the early morning empty, while I'm asleep. On weekdays windows now run 06:30 → 11:30 (reset) → 16:30 → 21:30 → 02:30, and only 02:30–06:30 is empty.

| Command | Meaning |
| --- | --- |
| `config peak 11:30 weekdays` | Weekdays at 11:30 (`mon-fri`, `mon,wed,fri` work too; no days means every day) |
| `config gap` | Shows the empty-hour choices again and asks |
| `config gap 4` | Picks choice 4 (or a time inside it: `config gap 03:00`) |
| `config peak off` | Off (windows chain back to back as before) |

## How it behaves

- **The peak applies only once you've chosen the empty hours.** It won't pick them for you.
- **Off an aligned time, it waits.** A window opened at the wrong moment would throw the peak off. While it waits it doesn't call Claude at all, so it costs no tokens.
- **A window that's already off can't be fixed.** If your own message opened a window at another time, it can't be moved. When it ends, claude-warmup lines up again at the next aligned time.
- **With days set, the time in between works as before.** Aligning starts within a day of each peak. When the next peak is far away, like over a weekend, a new window starts as soon as the last one ends.
- **Change the peak** and the choices change too. If the empty hours you chose no longer fit, it asks again.

You can see it all in the status screen:

```
Auto warm-up
  Schedule    06:00–23:00 · every day
  Peak time   weekdays 11:30 · pings lined up at 06:30, 11:30, 16:30, 21:30
  Gap         02:30–06:30
  Next ping   ~16:25, lined up so a window resets at tomorrow 11:30
```

## How to update

```bash
npm install -g github:jungtaejoon/claude-warmup
claude-warmup install
claude-warmup config peak 11:30 weekdays
```

Run `install` again so the background service switches to the new version. If you already use a peak time, choose the empty hours with `claude-warmup config gap`. If you set it up on a server with `scripts/server-setup.sh`, add `--prefix ~/.local` to the npm command so it replaces the same copy. I forgot that at first, and my server kept running the old version.

What changed: [0.3 release notes](https://github.com/jungtaejoon/claude-warmup/releases/tag/v0.3.0) · [0.2 release notes](https://github.com/jungtaejoon/claude-warmup/releases/tag/v0.2.0)
