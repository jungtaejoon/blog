---
title: "3,915 PSAT past-exam questions as mock tests: alltests, built in a day with Claude Code"
description: I built alltests.ai.kr, a site for taking every published Korean PSAT past exam like the real thing. How the questions were cut out, how 3,915 explanations were written, the answer-key errors the explanations caught, and keyless API calls for daily updates.
project: alltests
ref: alltests-psat-mock
kind: dev
---

I opened [alltests.ai.kr](https://alltests.ai.kr/), a site for taking the PSAT (the aptitude test for Korean civil-service exams: grade 5, diplomats, grade 7, private-sector hires, regional talent) as real timed mock tests. I asked Claude Code to "collect every past exam and run it as a mock-test site" and mostly just steered.

## What's in it

- 117 papers from 2005–2026, 3,915 questions
- **Exam mode**: 90-minute timer for 40 questions, an OMR answer sheet, graded on submit
- **Practice mode**: graded per question, with the explanation right there
- **Random tests**: pick sections, exams and a year range and mix them (unseen questions first)
- **History and wrong-answer notes**: kept in the browser, retry only what you missed
- An AI explanation for every question: fastest approach → evidence → each choice → a time-saving tip

## Collecting the papers

The papers are published on the Korean government's civil-service recruitment site. There are seven exam tracks, but many share the same paper on the same day, so deduplicating by a text fingerprint left 117 papers. This year's files only come through a dedicated downloader widget, so a headless browser clicks it.

Answer keys came in a different format almost every era: a bitmask for recent years, an HTML popup for older ones, and for this year only a PDF answer sheet that is read by coordinates.

## Cutting out questions

PSAT papers are two-column, questions spill across columns and pages, and some passages are shared by two or three questions. Each question runs from its number line to just before the next one, and only those coordinates are stored. The site draws just that region of the original PDF with pdf.js, so tables and charts stay sharp vector graphics and the data stays small.

There were plenty of small traps: choice ⑤ at the bottom of a page mistaken for the page number, zero-width box borders that never intersected anything, and old papers where "문" and "1." are separate text lines. All 3,915 questions are cut correctly now.

## 3,915 explanations

Explanations for past papers were written inside a Claude Code session, one agent per paper, each reading the question images directly. The official answer is fixed; the job is to explain *why* it's right. A checker then flags formatting problems, explanations that claim a different answer, and explanations that talk about a different question. It did catch two papers where parallel agents had collided on a temp-file name and mixed up their output; those were rewritten.

New papers are handled every night by GitHub Actions: it checks for new papers and confirmed answers and writes explanations only for questions that don't have one yet, via the Claude API (Message Batches).

## Answer-key errors the explanations caught

The fun part: the explanation writers kept raising a hand saying "the passage doesn't support the official answer." It turned out the 2005 answer keys were misaligned with the papers. For Verbal Reasoning, answers 1–20 and 21–40 were swapped wholesale; for Data Interpretation, 1–5 and 21–25. Every question, flagged or not, fit the same swap, so the key was the problem.

One 2011 question was the same story: booklet "간" said ①, the passage pointed to ④, and the other booklet's key had ④ for the same question. These fixes live as rules in the scraper so the nightly update won't undo them.

## Calling the API without a key

Instead of storing an API key in GitHub, the nightly job uses workload identity federation from the Claude Console. Each run exchanges GitHub's OIDC token for a short-lived Anthropic token, so there's no stored secret and nothing to rotate.

One snag: the rule's subject was `repo:owner/repo:ref:refs/heads/main`, and it was rejected. This repo uses GitHub's newer "immutable subject" format, which embeds numeric IDs (`repo:owner@id/repo@id:ref:...`). Checking the repo's `actions/oidc/customization/sub` setting and updating the rule fixed it.

## A Slop ad, PSAT-style

The exam-picker and results pages carry a house ad for [Slop](https://slop.ai.kr/), shaped like a PSAT question ("Which is the most appropriate way to judge an AI-made app?"). Answer it and a button takes you to judging. It never shows while you're taking a test.

## What I learned

My biggest worry was wrong AI explanations. Pinning the official answer and telling the model to raise a hand instead of papering over a mismatch did the opposite: it found errors in the source. Making doubt visible was the most useful accuracy tool.

Try a round at [alltests.ai.kr](https://alltests.ai.kr/) and judge it gem or slop on [the Slop post](https://slop.ai.kr/#/p/05501232-1492-4a45-bca5-8f87f2cc607f). The code is on [GitHub](https://github.com/jungtaejoon/psat-mock).
