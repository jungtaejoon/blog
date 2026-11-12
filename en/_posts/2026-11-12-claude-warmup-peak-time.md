---
title: "claude-warmup 0.2: make Claude's 5-hour limit reset right at your busiest time"
description: Set a peak time and claude-warmup works backward to time its pings so a 5-hour window resets right then. You can limit it to weekdays, too.
project: claude-warmup
ref: claude-warmup-peak-time
kind: dev
image: https://jungtaejoon.github.io/claude-warmup/og.png
---

[claude-warmup](https://jungtaejoon.github.io/claude-warmup/) is a small tool that keeps a Claude Pro/Max 5-hour window always running. It opens a new window as soon as the last one ends, so whenever you sit down, your first message doesn't start a full 5-hour wait.

Using it, I noticed one thing missing. I get up at about the same time every day, and my busiest hours are about the same too. So the best thing would be a reset **right at that time**. Version 0.2 adds exactly that.

## What a peak time is

```bash
claude-warmup config peak 11:30 weekdays
```

Tell it "weekdays at 11:30 are my busiest," and it works backward. For a reset at 11:30, that window has to start at 06:30, the one before at 01:30, and the ones before that at 20:30 and 15:30 the previous day. So pings go out only at those times (minus any outside your `hours`).

| Command | Meaning |
| --- | --- |
| `config peak 14:00` | Every day at 14:00 |
| `config peak 11:30 weekdays` | Weekdays at 11:30 (`mon-fri`, `mon,wed,fri` work too) |
| `config peak off` | Off (windows chain back to back as before) |

## How it behaves

- **Off an aligned time, it waits.** A window opened at the wrong moment would throw the peak off. While it waits it doesn't call Claude at all, so it costs no tokens.
- **A window that's already off can't be fixed.** If your own message opened a window at another time, it can't be moved. When it ends, claude-warmup lines up again at the next aligned time.
- **With days set, the time in between works as before.** Aligning starts within a day of each peak. When the next peak is far away, like over a weekend, a new window starts as soon as the last one ends. For weekdays at 11:30, that means always-on from Friday afternoon to Sunday morning, then lining up for Monday 11:30 from Sunday 15:30.
- **The trade-off: no window runs while it waits.** If you start working in that gap, your own message opens the window. If you'd rather avoid that, turn the peak time off.

You can see it all in the status screen:

```
Auto warm-up
  Schedule    06:00–23:00 · every day
  Peak time   weekdays 11:30 · pings lined up at 06:30, 15:30, 20:30
  Next ping   ~15:25, lined up so a window resets at tomorrow 11:30
```

## How to update

```bash
npm install -g github:jungtaejoon/claude-warmup
claude-warmup install
claude-warmup config peak 11:30 weekdays
```

Run `install` again so the background service switches to the new version. If you set it up on a server with `scripts/server-setup.sh`, add `--prefix ~/.local` to the npm command so it replaces the same copy. I forgot that at first, and my server kept running the old version.

The full list of changes is in the [release notes](https://github.com/jungtaejoon/claude-warmup/releases/tag/v0.2.0).
