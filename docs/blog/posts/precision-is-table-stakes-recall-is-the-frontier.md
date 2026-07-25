---
date: 2025-07-20
authors:
  - halynagalanzina
categories:
  - AI Engineering
  - Information Extraction
description: In LLM extraction, recall is the real engineering challenge, and a multi-stage architecture is what pushed it above 90%
slug: precision-table-stakes-recall-frontier
---

# Precision is table stakes; recall is the frontier

Most of the worry around large language models lands on hallucinations, meaning incorrect information. Achieving 100% precision is a prerequisite for any financial data system. According to my evaluations for professional-grade extraction with LLMs, the harder challenge is recall. If an LLM encounters a complex website structure or a 50-page legal document, it misses details buried deep in the text.

<!-- more -->

I addressed this by redesigning the traditional extract-in-one-shot architecture. Splitting the process into multiple stages, first gathering evidence through an LLM-based websearch or scanning, then parsing that evidence into structured models, pushed recall above 90%. It was still a project where precision had the upper hand, so I stopped there. The multi-stage approach prevents the model from being overwhelmed by long contexts, so nuanced details, such as specific investment policy requirements, survive the pass.

Without high recall, automation is just a faster way to get an incomplete picture.
