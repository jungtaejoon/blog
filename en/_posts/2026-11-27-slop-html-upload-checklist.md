---
title: "Five things to check before posting an AI-made HTML game or tool on Slop"
description: What to fix in a single HTML file from Claude or ChatGPT before posting it on Slop as a runnable app, so it doesn't break in the sandboxed frame and actually gets votes.
project: slop
ref: slop-html-upload-checklist
kind: guide
image: https://slop.ai.kr/og.png
---

The most fun posts on [Slop](https://slop.ai.kr/) are HTML apps you can try right there on the page. Ask an AI for "a game where you guess 10 seconds," paste the single file it gives you, and it runs inside the post. But a file that worked fine on your machine can freeze once it's posted, or run fine and still get no votes at all. Based on the hints and checks built into the post editor, here are five things to look at before you post.

## 1. Put everything in one file

An app post means pasting one whole HTML file. If the CSS and scripts live in separate files, they don't come along. It's easiest to tell the AI up front: "one HTML file, no external files."

## 2. Drop requests that leave the page

If the code calls `fetch` or loads an outside URL, the editor shows a warning. Take it out unless you really need it. Apps that send data elsewhere can be reported. When the app runs entirely on its own, the editor tells you so.

## 3. Don't break when storage is blocked

The app runs in an isolated frame, so storage like localStorage is blocked. AI-made games often try to save a high score, hit an error, and freeze on the first screen. Ask the AI to wrap the saving code in try/catch, then play one full round in the editor's preview.

## 4. Check it at phone width

A lot of judging happens on phones. If the viewport meta tag is missing, the editor will tell you. If the game only works with a keyboard, one more line asking for touch controls goes a long way. [Time Sense](https://slop.ai.kr/p/467f9a5d-f560-47fa-8bc8-6feb41078077/) takes both phone taps and the PC spacebar.

## 5. Keep the description short, with strengths and weaknesses apart

Lists only show the first two or three lines. Say what the app does in the first line and add one line on how to play. Then list what's good and what's lacking separately; posts written that way draw more votes. Naming the weak spots yourself tends to get you "here's how to fix it" comments instead of a flat "this is slop." End with one question you'd like answered, and fill in the "tool" and "prompt" fields. Both are optional, but they let other people reproduce and remix your work.

## After you post

When you fix things based on comments, post it as a new version rather than a new post. Each version can be compared with the last, so the path from slop to gem stays on record. And if you've tried someone else's app, open [Judge](https://slop.ai.kr/#/judge) and press ▲ or ▼. That's all it takes.
