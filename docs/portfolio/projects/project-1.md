---
title: Investment Data Extraction Pipeline
description: Automated extraction of 690+ complex entities from investment documents for a VC fund — 94% accuracy, zero hallucinations, multi-stage LLM architecture.
---

# Engineering a High-Scale Data Factory for a Data Intelligence Startup

!!! abstract "Project Summary"
    **Client**: Data Intelligence Startup (Investment Sector)
    **Duration**: 12+ months
    **Industry**: Financial Services / Venture Capital

    **Impact Metrics**:

    - **94% final accuracy** across 690 complex entities (strict matching)
    - **Zero hallucinations** — no unsupported extractions observed in manual review
    - Replaced a 3-7 person manual workflow (high turnover, scaling bottleneck)
    - Multi-stage LLM architecture with citation-backed, auditable results
    - Phase 1 baseline: 74% → Final: 94% through architectural redesign

## Challenge

The client's product value was inseparable from the integrity of its database. The original process was a "human-loop" factory: 3 to 7 analysts manually extracting data, with mid-level supervisors reviewing and disputing entries. While this maintained high quality, the model couldn't scale. Data was decaying faster than the team could refresh it, and manual extraction became a permanent operational bottleneck.

Our task was to automate the extraction of over 30 complex data entities per record. These weren't simple strings — they were nested structures involving normalization, classification, interpretation, and multi-layered policy requirements.

## Phase 1: Standard Extraction

Using standard extraction patterns, we achieved a field-level accuracy of **74%** against corrected ground truth. The challenge wasn't just accuracy — it was **recall**. The system would often miss information hidden in non-standard structures or deep within unstructured text.

## The Pivot: Research-First Architecture

To reach production-grade reliability, we moved away from "one-shot" extraction and implemented a multi-stage architecture:

1. **Evidence Collection**: The system identifies and gathers relevant citations across the target's digital footprint using LLM-equipped websearch, exploring each target's web presence in a controlled, evidence-first way.

2. **Structured Synthesis**: Only after evidence is gathered is it parsed into strict Pydantic schemas.

This approach prevents the model from being overwhelmed by long contexts or complex site layouts. By separating "finding" from "parsing," we ensured the system didn't lose focus.

## Results: Audit-Grade Reliability

We conducted structured evaluation across 30 organizations, evaluating **690 complex entities** under a strict matching rule: if a single nested sub-field or list entry was missing or incorrect, the entire entity was marked as a failure.

- **94% final accuracy** — significantly outperforming the Phase 1 baseline
- **Zero hallucinations**: The system is designed to report "not found" rather than invent a plausible answer — and it holds this promise
- **Deterministic validation**: By anchoring every data point to a specific citation, we transformed the database from a collection of claims into a verifiable data asset
- **Competitive advantage** in data freshness, accuracy, and coverage

### Evaluation Method

- **Scope**: 30 organizations, 23+ complex entities per record (nested sub-fields, normalized values, roles)
- **Schema**: Strict Pydantic models with validation of nested lists and group-level data
- **Accuracy definition**: Strict match only — any missing sub-field = 0% credit for that entity
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

<div class="grid cards" style="margin-top: 3rem" markdown>

-   :material-coffee:{ .lg .middle } Interested in a similar solution?

    ---

    Let's discuss how automated document extraction can work for your data.

    [Book Discovery Call :material-arrow-top-right:](https://calendly.com/halyna-litai-solutions/discovery){target="_blank" .md-button .md-button--primary }

</div>
