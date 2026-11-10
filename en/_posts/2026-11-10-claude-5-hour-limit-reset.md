---
title: "How to make Claude's 5-hour limit reset in the middle of your workday"
description: I kept hitting Claude's limit around noon while building Slop, so I made claude-warmup, a small tool that opens the 5-hour window before work.
project: claude-warmup
ref: claude-5-hour-limit-reset
image: https://jungtaejoon.github.io/claude-warmup/og.png
---

While building [Slop](https://jungtaejoon.github.io/slop/) with Claude Code, I saw the same thing almost every day. A productive morning, then around noon: "limit reached, resets at 2 PM." Two hours of waiting, right when I was most in the flow. So I looked into how the reset is timed and built a small tool.

## The reset is 5 hours after your first message

Claude Pro and Max session limits run on windows that start with **your first message**, not on a fixed clock ([help center](https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work)). Ask your first question at 9:00 and the limit resets at 14:00. The web app, desktop and mobile apps, and Claude Code share it. The weekly limit is separate.

You can see your own reset time by running `/usage` in Claude Code. It runs locally and uses no tokens.

## Open the window early and the reset moves up

If you start work at 9:00, send one short message at 6:00.

| Time | Window |
| --- | --- |
| 6:00 to 11:00 | First window (you only use 9 to 11) |
| 11:00 | A fresh window, right when the morning would hit the limit |
| 16:00 | Another fresh window |

You don't get more usage. The waiting just moves out of your best hours.

## Automating it: claude-warmup

I can't wake up at 6 every day to send a message, so I built [claude-warmup](https://jungtaejoon.github.io/claude-warmup/).

- It checks every 5 minutes with `/usage` (0 tokens) and sends "hi" to haiku **only when no window is open**.
- It runs on your own computer or server and never reads your credentials, so no token has to live in another service.
- It shows session and weekly usage with reset times in the terminal.
- It runs on macOS, Linux and Windows, with a setup script for a free always-on server for when your laptop is off.

```bash
npm install -g github:jungtaejoon/claude-warmup
claude-warmup install
claude-warmup config hours 06:00-23:00
```

I run it on a free Oracle Cloud server. Even with my Mac off, the window opens at 6 every morning, and resets land at 11 and 16.

The details are in the [Claude usage limit reset guide](https://jungtaejoon.github.io/claude-warmup/claude-usage-limit-reset/). The code is on [GitHub](https://github.com/jungtaejoon/claude-warmup).
