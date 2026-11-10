---
title: "Is everything AI-made just slop? I built Slop, a community that finds the gems"
description: Post AI-made writing, images, web apps and code. People who try them judge each one ▲gem or ▼slop, and you grow the good ones into the next version.
project: slop
ref: introducing-slop
kind: guide
image: https://jungtaejoon.github.io/slop/og.png
---

Anyone can now write, draw, and even ship small web apps and games with AI. That also means a lot of it gets waved off with "it's just AI-made." People call that **slop**.

But mixed into the pile are things that are genuinely useful or fun. The problem is there is no good place to sort them out. So I built **[Slop](https://jungtaejoon.github.io/slop/)**.

## How Slop works

1. **Post.** Share AI-made writing, images, runnable HTML, code or links in topic communities. You can note which tools and prompts you used.
2. **Try.** Runnable HTML plays right in a sandbox, so you can try an AI-made web app or game without installing anything.
3. **Judge.** People who try it vote **▲gem** or **▼slop**. Comments carry a type such as "found value", "suggestion" or "question", so the reason behind each judgment stays visible.
4. **Grow.** The author posts a **new version** based on the feedback. You can compare what changed between versions, and adopted suggestions get marked. Others can **remix** it too.

> The question is not "was it made by AI?" but "is it worth something once you try it?"

## Communities anyone can start, like Reddit

There are communities for AI art, AI music, prompts, small web apps and more. Follow the ones you like and they fill your home feed; the popular feed shows everything. You can sort by hot, new, top, controversial, or **awaiting judgment**, so you can find posts nobody has judged yet and leave the first vote.

## Things to try right now

- **Judge one post:** open the [judge screen](https://jungtaejoon.github.io/slop/#/judge) and a card shows up. Press ▲ or ▼, that's it.
- **See this week's gems:** the [weekly gems](https://jungtaejoon.github.io/slop/best/) page refreshes every three hours.
- **Use it like an app:** on your phone, choose "Add to Home Screen" in the browser to install it.
- **Subscribe:** follow new posts with [RSS](https://jungtaejoon.github.io/slop/rss.xml).

## How I built it

I built Slop together with Claude Code. The front end uses Vite, and data and sign-in run on Supabase (Postgres with row-level security rules). The code is public on [GitHub](https://github.com/jungtaejoon/slop). I will keep writing here about what happens while building it: bugs fixed, and what I try to bring people in.

It is still early, so every vote and comment really helps. If you have made something with AI, post it and see how it is judged.

**[Explore Slop →](https://jungtaejoon.github.io/slop/)**
