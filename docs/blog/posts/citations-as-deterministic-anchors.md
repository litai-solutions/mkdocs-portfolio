---
date: 2025-09-10
authors:
  - halynagalanzina
categories:
  - Evaluation
  - Information Extraction
description: "Why I build both instruments: a benchmark that says whether the pipeline can ship, and a citation on every field that lets a user check one value without trusting the aggregate."
slug: citations-as-deterministic-anchors
---

# Citations as deterministic anchors

Trust in AI is built on transparency. Every extracted field carries a citation back to the exact source passage, and the full extraction set is scored against a benchmark. They answer different questions, at different moments. The benchmark answers whether the pipeline is good enough to ship; that is my question, once, before release. The citation answers where a specific number came from; that is the user's question, every day after.

<!-- more -->

In my extraction pipelines I treat every data point as a claim that must be proven. Each of the several dozen fields I track per topic requires a citation, so a probabilistic output becomes an auditable record. No value has to be taken on faith.

Validation becomes much simpler when the system provides its own audit trail. When extracting contact form locations or complex entity names, the system returns the specific URL and the surrounding context the value was found in. That is how I reached a 90-99% accuracy rate while maintaining a 0% hallucination rate: the system is designed to report "not found" rather than invent a plausible answer.

Citations also make automated evaluation reliable. I built a custom framework that compares extractions against benchmarks and uses the citations to resolve disagreements between the old manual data and the new automated results.
