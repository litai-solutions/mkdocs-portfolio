---
date: 2025-07-20
authors:
  - halynagalanzina
categories:
  - AI Engineering
  - Information Extraction
description: In LLM extraction, precision gets the headlines but recall is the real engineering challenge
slug: precision-table-stakes-recall-frontier
---

# Precision is Table Stakes; Recall is the Frontier

In the discussion around Large Language Models, the fear of hallucinations — incorrect information — often dominates the conversation. Achieving 100% precision is a prerequisite for any financial data system; "no garbage in" is a non-negotiable rule. However, for professional-grade extraction, the more difficult challenge is recall. If an LLM encounters a complex website structure or a 50-page legal document, it often loses focus, missing critical details buried in the text.

<!-- more -->

We addressed this by redesigning the traditional extract-in-one-shot architecture. By splitting the process into multiple stages — first gathering evidence through an LLM-based websearch, then parsing that evidence into structured models — we pushed recall above 90%. It was still a project where precision had the upper hand, so we decided to stop there. Such multi-stage approach prevents the model from being overwhelmed by long contexts, ensuring that nuanced details, such as specific investment policy requirements, are not left on the table.

Without high recall, automation is just a faster way to get an incomplete picture.

---

*Based on real-world experience building extraction pipelines where completeness matters as much as correctness.*
