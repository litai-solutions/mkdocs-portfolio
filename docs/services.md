---
title: Extraction and evaluation engagements
description: "Discovery call, extraction and retrieval reality check, evaluation infrastructure builds, and ongoing quality monitoring, with pricing and deliverables named."
---

# Services

## :material-phone-outline: Discovery Call (Free)

**What it is**: 30-60 minute conversation about your documents, your search or RAG system, and what "correct" has to mean before it ships.

**Best for**:

- Teams designing a search or extraction system to discuss the method and architecture options
- Teams whose retrieval works in a demo and is unproven on the real archive
- Leaders who need to know whether their problem is retrieval, extraction, or measurement

**What happens**:

- You describe your documents and your use cases
- We work out which parts are solvable with retrieval, and which need work further upstream in ingestion and extraction
- I name the engagement that fits, or say that none of them does
- Clear next step: reality check, build, or nothing

**Timeline**: 30-60 min | **Investment**: Free

[Book Discovery Call :material-arrow-top-right:](https://calendly.com/halyna-litai-solutions/discovery){target="_blank" .md-button .md-button--primary }

---

## :material-magnify: Search and RAG Reality Check

**What it is**: A judgment on which retrieval architecture your documents require, and whether the approach you have in mind will hold up on them. The measurement comes with it, so the judgment is checkable.

**Best for**:

- Teams about to build search or RAG who want the architecture decided by the documents
- Leaders choosing between chunking strategies, hybrid search, or a graph layer
- Teams whose pilot performs on clean files and loses information on harder cases such as scans, tables, or long contracts

**What you get**:

- Document landscape analysis: types, structure, variability, and the edge cases that break parsers
- A retrieval design recommendation with the reasoning shown: BM25 and embeddings, a document-as-graph layer, query-intent interpretation, entity resolution, and where a domain thesaurus earns its cost
- An evaluation set built from your own documents, with the fields, structure, and coverage named
- Metrics defined for your domain, and an LLM judge calibrated against a gold set
- A failure taxonomy: where it breaks, how often, how badly
- A build / don't build / build differently recommendation

Model and method results are specific to your documents and to the models available that quarter, so they get measured for each engagement. A comparison run a year ago on someone else's corpus tells you very little about yours.

**Scope**: an assessment, run on a sample of your real documents rather than a whole corpus. Implementation is the next engagement.

**Timeline**: 2-4 weeks | **Investment**: Starting from $5k

---

## :material-hammer-wrench: Retrieval Build with Measurement

**What it is**: I build the retrieval and the measurement together, on one slice of your problem, so what ships has evidence attached to it.

**Best for**:

- Teams committed to production who want the first slice built to a standard the rest can follow
- Organizations that need every answer traceable to the source passage it came from
- Engineering leads who want to change the system and see whether it improved

**What you get**:

- Everything in the Search and RAG Reality Check, plus:
- An ingestion, extraction, and normalization pipeline for your document types, including scans and multi-page tables
- Hybrid retrieval built to the design the reality check recommended, with ranking you can explain
- Provenance carried end to end, so every hit links back to its source document and passage
- A benchmark on your documents, with metrics defined, calibrated, and automated
- Regression testing wired into CI, so a change that degrades retrieval fails the build
- Error analysis that names where a failure comes from, and the documentation for your team to run the loop without me

**Scope**: 6-8 weeks delivers a working system on your own documents, built to production standard, with the measurement that covers it. That is past a prototype and short of a finished rollout. The estimate assumes a corpus up to roughly 10,000 documents; a larger collection, or one whose formats vary more than the sample suggested, extends the timeline. Scaling out is the phase after this one, and what it takes is one of the things this phase tells you.

**Timeline**: 6-8 weeks | **Investment**: Starting from $15k

---

## :material-shield-check: Continuous Quality Guardian

**What it is**: Monthly support for evolving AI systems that need sustained quality oversight.

**Best for**:

- Teams with complex systems that change frequently
- Organizations adding new document types or use cases
- Companies needing expert oversight during scaling

**What you get**:

- Monthly evaluation runs on production data
- Quarterly gold standard refresh as system evolves
- New evaluator development for emerging needs
- Quality trend analysis and advisory
- Priority support for quality incidents
- Guidance on model upgrades (new GPT/Claude versions, OSS models)

**Timeline**: 3-12 month retainer | **Investment**: Starting from $1k/month

---

<div class="grid cards" style="margin-top: 2rem" markdown>

-   :material-coffee:{ .lg .middle } Not sure which service fits?

    ---

    Start with a free discovery call. I'll name the one that fits, or tell you none of them does.

    [Book Discovery Call :material-arrow-top-right:](https://calendly.com/halyna-litai-solutions/discovery){target="_blank" .md-button .md-button--primary }

</div>
