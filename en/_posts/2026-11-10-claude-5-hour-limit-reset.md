---
title: "How to stop waiting a full 5 hours for Claude's usage limit to reset"
description: I got tired of waiting out nearly 5 hours every time I hit Claude's limit while building Slop, so I made claude-warmup, a small tool that keeps a 5-hour window always running.
project: claude-warmup
ref: claude-5-hour-limit-reset
image: https://jungtaejoon.github.io/claude-warmup/og.png
---

While building [Slop](https://jungtaejoon.github.io/slop/) with Claude Code, I saw the same thing almost every day. A productive morning, then around noon: "limit reached, resets at 2 PM." My own first message at 9 had started a fresh 5-hour clock, so I waited two hours, right when I was most in the flow. So I looked into how the reset is timed and built a small tool.

## The reset is 5 hours after your first message

Claude Pro and Max session limits run on windows that start with **the first message** after the last window ended, not on a fixed clock ([help center](https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work)). Ask your first question at 9:00 and the limit resets at 14:00. The web app, desktop and mobile apps, and Claude Code share it. The weekly limit is separate.

You can see your own reset time by running `/usage` in Claude Code. It runs locally and uses no tokens.

## Keep a window running and you wait less

The problem is that your first message starts the **whole** 5 hours. If a window was already running before you sat down, part of those 5 hours has already passed. Start a new window the moment the last one ends, and you get this:

| Window | Start then, next reset at |
| --- | --- |
| 6:00 to 11:00 | Start at 9:00 → 11:00 (otherwise 14:00) |
| 11:00 to 16:00 | Start at 13:00 → 16:00 (otherwise 18:00) |
| 16:00 to 21:00 | Start at 19:00 → 21:00 (otherwise midnight) |

Whenever you sit down, the next reset is about 2.5 hours away on average. You don't get more usage. You just stop starting from a full 5-hour wait.

## Automating it: claude-warmup

I can't send a message every time a window ends, so I built [claude-warmup](https://jungtaejoon.github.io/claude-warmup/).

- It checks every 5 minutes with `/usage` (0 tokens) and sends "hi" to haiku **only when no window is open**, so a new window follows right after the last one.
- It runs on your own computer or server and never reads your credentials, so no token has to live in another service.
- It shows session and weekly usage with reset times in the terminal.
- It runs on macOS, Linux and Windows, with a setup script for a free always-on server for when your laptop is off.

```bash
npm install -g github:jungtaejoon/claude-warmup
claude-warmup install
claude-warmup config hours 06:00-23:00
```

I run it on a free Oracle Cloud server. Even with my Mac off, windows run back to back from 6 in the morning until night, so the clock is already running whenever I sit down.

The details are in the [Claude usage limit reset guide](https://jungtaejoon.github.io/claude-warmup/claude-usage-limit-reset/). The code is on [GitHub](https://github.com/jungtaejoon/claude-warmup).
