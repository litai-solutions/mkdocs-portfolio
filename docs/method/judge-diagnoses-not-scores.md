---
title: The judge does not score. The judge diagnoses.
description: Two competent LLM graders can disagree by 20+ points on the same answers. A layered evaluation that separates infrastructure, retrieval, generation, and stability failures, so each gets its own verdict.
---

# The judge does not score. The judge diagnoses.

An answer can be wrong for three unrelated reasons: retrieval never found the source document, the model wrote badly from a document that was right there, or the request never completed at all. Most retrieval evaluation collapses all three into one number. "62% correct" separates none of them, and the engineer reading it still has to guess which layer to open first.

Judges vary too. Two competent graders will not agree on the same set of answers unless the rubric and the calibration make them, so a single accuracy score from a single uncalibrated judge tells you as much about the grader as about the system.

The way I build evaluation rests on one decision: **the judge returns a diagnosis.** I ask it for a structured, fact-level decomposition: which required facts are present, which are missing, which extra facts were introduced, whether the central claim holds. Every aggregate number is *derived* from those structured verdicts, so every headline percentage traces down to a specific machine-readable record, the same record the engineer reads to fix the system.

From there the measurement becomes layered, and each layer has a different epistemic status:

- **Infrastructure**: did the request even complete cleanly? Deterministic. No judge needed.
- **Retrieval**: was the correct source document actually in the retrieved set? Deterministic and judge-independent. This is the layer that most often explains the failure.
- **Answer quality**: the structured, fact-level judge verdict described above.
- **Stability**: run the same question three times. A question that's right once and wrong twice is *unstable*, which is a different problem with a different fix than a question that fails every time. Separating stable-correct from stable-wrong from these "flippers" tells you where the system is reliable and where it has been lucky.
- **Capability ceiling**: best result across runs. The gap between the ceiling and what the system does *reliably* is your headroom, and it points at exactly where to invest.

**Audit the benchmark before you trust it.** In one audit, 20% of apparent failures were defective test questions: no valid source mapping, a reference answer that contradicts the documents, a question the corpus can't answer. Twenty percent is at the high end. Up to 10% is a rate I expect to find in any benchmark I did not build myself. Reporting those as system failures is how teams chase ghosts for weeks. Before any result is believed, the benchmark itself gets audited and versioned.

Once the structured verdicts exist, the layered report costs no more to produce than the single number did.

---

This is the evaluation design behind [RAG Evaluation Infrastructure](../case-studies/rag-evaluation-infrastructure.md), where the judge is calibrated against a labelled reference set and runs in CI.
