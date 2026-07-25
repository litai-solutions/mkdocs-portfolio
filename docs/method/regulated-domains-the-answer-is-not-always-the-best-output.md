---
title: In regulated domains, the answer is not always the best output
description: In law, medicine, compliance, and finance, a generated answer is a claim with no chain of custody. The right output is ranked, traceable evidence, and that changes the architecture down to the first pipeline node.
---

# In regulated domains, the answer is not always the best output

Ask most people to build "AI search" today and you get a chatbot: type a question, get a generated paragraph back. In a consumer setting that's fine. In law, medicine, compliance, or finance, it's the wrong shape entirely, and understanding *why* is most of the job.

A generated answer is a claim with no chain of custody. It reads fluently, it's often right, and when it's wrong there is no way to see that from the answer itself. A lawyer can't cite it. A doctor can't act on it. An auditor can't trace it. The professionals in these fields are trained, accountable, and skeptical by profession. They don't want a conclusion; they want the *evidence that lets them draw their own*.

So the output I design for is more than an answer. It is a **ranked list of hits, each one linked back to the exact source document and passage it came from.** The system's job is to find and rank the right evidence with high recall and defensible ordering. The judgment stays with the human who is licensed to make it.

This reframing reaches all the way down the architecture:

- **Retrieval quality becomes the whole game.** If the evidence is right and complete, the professional succeeds. There is no generation step to paper over a bad retrieval, which is honest, because in a generated-answer system, fluent language routinely hides missing facts.
- **Every result must be traceable.** That means provenance carried through the entire pipeline, from raw document through extraction and normalization to the ranked hit, so a click on any result lands on the source. Provenance is a constraint you design from the first node, and it shapes every schema downstream of it.
- **Embeddings alone aren't enough.** Vector similarity is powerful, but on its own it's opaque, and you can't explain *why* a document ranked where it did. A hybrid system pairs embeddings with a linguistically-structured layer: an entity graph plus a domain thesaurus that grows as documents arrive, so one query matches every variant, abbreviation, and OCR error of a term. The embeddings give the system semantic reach, and the linguistic layer lets it show its work: this document ranked here because this term resolved to this entity. In a regulated domain that explanation is the deliverable.

So I start from a different question than "how do we make the model answer well." I start from what an accountable professional needs to see in order to trust and verify the result, and I let that decide the pipeline.
