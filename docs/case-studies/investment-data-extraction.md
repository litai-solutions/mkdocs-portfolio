---
title: Investment Data Extraction Pipeline
description: "Automated extraction of 690+ complex entities from investment documents for a VC fund: 94% accuracy, zero hallucinations, multi-stage LLM architecture."
---

# Engineering a High-Scale Data Factory for a Data Intelligence Startup

!!! abstract "Project Summary"
    **Client**: Data Intelligence Startup (Investment Sector)
    **Duration**: 12+ months
    **Industry**: Financial Services / Venture Capital

    **Impact Metrics**:

    - **94% final accuracy** across 690 complex entities (strict matching)
    - **Zero hallucinations**: no unsupported extractions observed in manual review
    - Reduced a 19-person data operation to 5 (collection, management, and QA)
    - Multi-stage LLM architecture with citation-backed, auditable results
    - Phase 1 baseline: 74% → Final: 94% through architectural redesign

<div class="grid cards testimonials" markdown>

-   We run a venture capital market database. We started with 19 people on data collection, management, and QA. Working with Halyna, we automated our core workflows and brought the team down to 5, with better quality and no speed bottleneck. She knows how to orchestrate agents, evaluate what they produce, and build the safeguards that make automation trustworthy.

    **[Anna Scherbak](https://www.linkedin.com/in/anna-scherbak/){target="_blank" rel="noopener"}**, Head of Product at Unicorn Nest

</div>

## Challenge

The client's product value was inseparable from the integrity of its database. The original process was a "human-loop" factory of 19 people across collection, management, and QA: 3 to 7 analysts extracting data at any given time, with mid-level supervisors reviewing and disputing entries. While this maintained high quality, the model couldn't scale. Data was decaying faster than the team could refresh it, and manual extraction became a permanent operational bottleneck.

Our task was to automate the extraction of over 30 complex data entities per record. They were nested structures involving normalization, classification, interpretation, and multi-layered policy requirements.

## Phase 1: Standard Extraction

Using standard extraction patterns, we achieved a field-level accuracy of **74%** against corrected ground truth. **Recall** was the harder problem: the system missed information held in non-standard structures or buried deep in unstructured text, and a precision-first reading of the results would have looked healthy while those misses went uncounted.

Three things moved the number, in order of how much they mattered.

**Two-stage extraction.** Separating evidence-gathering from schema-filling let the first stage do only the finding, with no obligation to produce well-formed output at the same time. That is where the recall came back.

**The data model.** Most of the gain came from changing what the schema asked for. Fields that collapsed several distinct facts into one slot were split, and types that had nothing to be disambiguated against were given competitors.

**Prompt rules, found by reading the reasoning.** Some prompt corrections were necessary, and I found them by reading each model's thinking output. Where the trace showed the model confused by a rule I had written, the rule was the defect and I rewrote it. Rewording prompts without that signal did little.

## The Pivot: Research-First Architecture

To reach production-grade reliability, we moved away from "one-shot" extraction and implemented a multi-stage architecture:

1. **Evidence Collection**: The system identifies and gathers relevant citations across the target's digital footprint using LLM-equipped websearch, exploring each target's web presence in a controlled, evidence-first way.

2. **Structured Synthesis**: Only after evidence is gathered is it parsed into strict Pydantic schemas.

This approach prevents the model from being overwhelmed by long contexts or complex site layouts. Separating "finding" from "parsing" gives each stage one task and a bounded context.

## Results: Audit-Grade Reliability

We conducted structured evaluation across 30 organizations, evaluating **690 complex entities** under a strict matching rule: if a single nested sub-field or list entry was missing or incorrect, the entire entity was marked as a failure.

- **94% final accuracy**, up from the 74% Phase 1 baseline
- **Zero hallucinations**: the system reports "not found" rather than inventing a plausible answer
- **Deterministic validation**: every data point is anchored to a specific citation, so any value in the database can be traced back to the passage it came from

### Evaluation Method

- **Scope**: 30 organizations, 23+ complex entities per record (nested sub-fields, normalized values, roles)
- **Schema**: Strict Pydantic models with validation of nested lists and group-level data
- **Accuracy definition**: Strict match only: any missing sub-field = 0% credit for that entity
- **Architecture**: Multi-stage LLM + websearch evidence-gathering → evidence-to-schema parsing
- **Recall**: Estimated >90% following the research-first architecture redesign

## Tech Stack

- Python, Pydantic (structured extraction)
- LLM integration (OpenAI/Anthropic APIs)
- Custom websearch evidence-gathering pipeline
- Strict schema validation and citation tracking
- Custom evaluation framework with ground-truth benchmarking

## My Role

Sole AI engineer. Designed the architecture across both phases, built the extraction pipeline, created the evaluation framework, identified critical quality issues in the client's existing manual process, and delivered the production-ready system.


The principle behind the data-model changes is in [Entity types are a competing set](../method/entity-types-are-a-competing-set.md).

<div class="grid cards" style="margin-top: 3rem" markdown>

-   :material-coffee:{ .lg .middle } Interested in a similar solution?

    ---

    Let's discuss how automated document extraction can work for your data.

    [Get in touch :material-email-outline:](mailto:halyna@litai-solutions.com)

</div>
