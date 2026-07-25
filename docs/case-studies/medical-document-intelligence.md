---
title: Medical Document Intelligence
description: A citation-first search solution that turns unsorted patient documents into a structured, searchable per-patient index.
---

# Medical Document Intelligence

!!! abstract "Project Summary"
    **Client**: Healthcare / Clinical Operations
    **Industry**: Medical / Health Tech
    **Status**: Working demonstrator

    **Focus Areas**:

    - Citation-first retrieval: physicians see cited hit lists, never generated answers
    - Clinical entity extraction and normalization across heterogeneous document formats
    - A self-growing medical thesaurus for clinical variants, acronyms, and OCR errors
    - Evaluation framework for medical-grade accuracy requirements

Designed and built an OpenSearch-based search solution that turns unsorted patient documents (PDFs, scans, DOCX) into a structured, searchable per-patient index. Built on one firm constraint: physicians see cited hit lists, not the generated answers.

## Challenge

Medical documents are among the hardest to process automatically. Clinical lab results and doctor reports come in inconsistent formats: different labs, different templates, multi-page reports with scattered data points. The accuracy requirements are high because downstream decisions affect patient care, and an accountable clinician needs to verify every result against its source.

## Approach

A search solution built around the document formats that arrive in practice:

- **Bounded-context pipeline**: ingestion, extraction, normalization, indexing, and query rewriting as separate, testable stages, with a provider-agnostic LLM layer
- **Traceable index**: an OpenSearch index with a per-mention entity graph and source deep links, so every hit traces back to the exact document and passage
- **Self-growing medical thesaurus**: matches a clinician's query against clinical variants, abbreviations, and OCR errors across the corpus
- **Evaluation-first design**: gold-standard benchmarks and recall experiments that show where structured-only retrieval misses clinically relevant documents

### What a thesaurus entry has to hold

Two entries, to show the shape. A clinician asking about type 2 diabetes writes one term; the documents contain all of these.

**Diagnosis.** `Type 2 diabetes mellitus` ← `type 2 diabetes`, `T2DM`, `DM2`, `NIDDM`, `adult-onset diabetes`

**Lab value.** `HbA1c` ← `hemoglobin A1c`, `glycated hemoglobin`, `A1C`, `Hb A1c`, `HbAlc`

`NIDDM` was retired as a term years ago and still appears in older records, which a patient history has to span. The last form on the lab line is OCR reading the digit 1 as a lowercase L: a scan that produces `HbAlc` puts that value outside every search for `HbA1c`, with nothing to announce the miss.

The clinical synonyms are what a domain expert would list. The OCR forms are what you get from reading the scanner output, and they carry the same weight.

### Where it is wrong, and why that is tolerable here

A thesaurus that grows from the documents makes mistakes. This one merges concepts that are clinically distinct: kidney disease and renal insufficiency end up under one normal form, though they describe different conditions. That is over-normalization.

Here it costs nothing, for two reasons that only work together. Search is always patient-scoped, so the patient identifier is the first filter applied. And the system is built for recall. A patient with both conditions documented gets both back; a patient with one gets that one. A false neighbour cannot arrive from another patient's record, because those documents were never in scope.

The same merge would be a real defect in a cross-patient cohort query. The design holds because of what this search is for.

## Current Status

A working demonstrator: unsorted patient documents in, a structured, searchable per-patient index out, with cited hit lists and full source traceability. Ongoing work expands document coverage and improves accuracy across edge cases.

## Tech Stack

- Python
- OpenSearch (per-mention entity graph, source deep links)
- Document AI / OCR pipeline
- Medical entity recognition, normalization, and self-growing thesaurus
- Custom evaluation framework
- On-premise LLM inference


The reasoning behind the citation-first design is in [In regulated domains, the answer is not always the best output](../method/regulated-domains-the-answer-is-not-always-the-best-output.md).

<div class="grid cards" style="margin-top: 3rem" markdown>

-   :material-coffee:{ .lg .middle } Working with complex medical documents?

    ---

    Tell me what your documents look like and where the current process loses them.

    [Get in touch :material-email-outline:](mailto:halyna@litai-solutions.com)

</div>
