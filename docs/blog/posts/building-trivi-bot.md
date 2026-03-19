---
date: 2026-03-16
authors:
  - halynagalanzina
categories:
  - AI Engineering
  - Engineering Culture
description: Why I built a 20KB app to stop skipping words — and what it taught me about friction in daily workflows
slug: building-trivi-bot
---

# Building Trivi: A Side-Brain for Trivial Tasks

I built Trivi because I kept skipping words.

Not complicated words — just unfamiliar ones. Terms I half-knew, expressions I'd seen but never pinned down, bash commands I couldn't quite remember. Every time I hit one, the same calculation ran in my head: *Is it worth breaking my flow to look this up?* The answer was usually no.

<!-- more -->

The context switching cost is real. Open a new tab, navigate to Google Translate, type the word, process the answer, switch back. That's 5-8 seconds — and more importantly, a full mental gear shift. Enough for your brain to decide "not worth it." So you skip it. Ten skipped words in an article, and you're reading the surface.

I'm bilingual — Ukrainian and German — and when I hit a tricky English expression, I need it in both languages to really anchor the meaning. I used to type "translate to de and ukr" into my AI chat every single time. That works, but it pollutes the thread. Now I need to scroll past translations to find where I was in the actual conversation.

So I built Trivi. A tiny PWA — 20KB total — that lives on my phone and desktop, always one tap away. You type a word, hit Enter, get all your translations instantly. No chat threads, no scrolling, no accounts, no data collection. Your API keys stay in your browser and go directly to the AI provider.

Then I added more modes: type `e` for a quick explanation, `c` for a bash command, `q` for a direct answer. Each mode is designed to give you exactly what you need and nothing more — so you can get back to what you were doing.

The surprising part wasn't the tool itself — it's how it changed my behavior. After a week, I noticed I was looking up words I would have skipped before. My reading comprehension genuinely improved because I stopped tolerating gaps.

The magic isn't the AI — it's the friction removal. The same information was always available. I just needed it to be fast enough that looking it up became easier than skipping it.

Trivi is open source: [github.com/litai-solutions/trivi-bot](https://github.com/litai-solutions/trivi-bot)

You can also see it in more detail on the [project page](../../portfolio/projects/project-5.md).
