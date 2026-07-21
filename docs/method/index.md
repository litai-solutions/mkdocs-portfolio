---
title: How I think about search
description: Problem-level principles behind reliable retrieval in regulated domains: the answer is the wrong output, the judge diagnoses instead of scores, and entity types are a competing set.
---

# How I think about search

Three principles behind how I design and evaluate retrieval systems for high-stakes documents. Not case studies: the way of thinking, with the mechanism shown.

<div class="grid cards" markdown>

-   :material-file-search-outline:{ .lg .middle } **In regulated search, the answer is the wrong output**

    ---

    Why lawyers, doctors, and auditors need ranked, traceable evidence, not a generated paragraph, and how that reframes the whole architecture.

    [Read →](regulated-search-answer-is-the-wrong-output.md)

-   :material-clipboard-check-outline:{ .lg .middle } **The judge does not score. The judge diagnoses.**

    ---

    Two competent LLM graders can disagree by 20+ points on the same answers. A layered evaluation that separates retrieval, generation, and stability failures instead of collapsing them into one number.

    [Read →](judge-diagnoses-not-scores.md)

-   :material-vector-link:{ .lg .middle } **Entity types are a competing set**

    ---

    You can't recognize persons without modeling cities and companies: the same string is all three. A principle from rule-based extraction that decides whether an LLM schema is actually separable.

    [Read →](entity-types-are-a-competing-set.md)

</div>
