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
  Windows keep chaining all day. From 01:30 to 06:30 no new one starts (it would run past the gap), and at 06:30 one starts that resets right at weekdays 11:30.
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
- **Windows keep chaining all day.** The only rest is the 5 hours before the gap ends (here 01:30–06:30), since a window started then would run past 06:30. While it rests it doesn't call Claude at all, so it costs no tokens.
- **If the timing gets thrown off, it lines up again by itself.** Even if my own late-night use opens a window at another time, windows keep chaining and line up again at the next gap's end. For example: my window until 14:00 → 14:00 → 19:00 → 00:00 (until 05:00) → rest → 06:30 → reset at 11:30.
- **No rest before a day without a peak.** With weekday peaks, Friday and Saturday nights just keep chaining.
- **Change the peak** and the choices change too. If the empty hours you chose no longer fit, it asks again.

You can see it all in the status screen:

```
Auto warm-up
  Schedule    06:00–23:00 · every day
  Peak time   weekdays 11:30 · windows chain all day; none starts 01:30–06:30, then one starts at 06:30 to end at the peak
  Gap         02:30–06:30
  Next ping   ~14:00, right after the current window resets
```

> **Fixed on 11/16 (0.3.1):** the first version pinged only at exact times and waited in between. So when my own late-night window ran past an aligned time, there was no window for hours, and a bug left the weekend from Friday afternoon to Sunday empty. Now it chains as above and rests only right before the gap.

## How to update

```bash
npm install -g github:jungtaejoon/claude-warmup
claude-warmup install
claude-warmup config peak 11:30 weekdays
```

Run `install` again so the background service switches to the new version. If you already use a peak time, choose the empty hours with `claude-warmup config gap`. If you set it up on a server with `scripts/server-setup.sh`, add `--prefix ~/.local` to the npm command so it replaces the same copy. I forgot that at first, and my server kept running the old version.

What changed: [0.3.1 release notes](https://github.com/jungtaejoon/claude-warmup/releases/tag/v0.3.1) · [0.3 release notes](https://github.com/jungtaejoon/claude-warmup/releases/tag/v0.3.0) · [0.2 release notes](https://github.com/jungtaejoon/claude-warmup/releases/tag/v0.2.0)
