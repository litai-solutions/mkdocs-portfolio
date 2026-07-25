---
title: The judge does not score. The judge diagnoses.
description: Two competent LLM graders can disagree by 20+ points on the same answers. A layered evaluation that separates infrastructure, retrieval, generation, and stability failures, so each gets its own verdict.
---

# The judge does not score. The judge diagnoses.

On the *same set of answers*, two competent LLM graders can disagree by more than twenty percentage points on how many are "correct." If your quality metric is a single accuracy score from a single judge, you don't know whether you improved the system or just changed the grader.

Most retrieval evaluation is broken in a specific way: it collapses three different kinds of failure into one number. An answer can be wrong because retrieval missed the source document, because the model wrote badly from a good document, or because the request never completed at all. "62% correct" tells you none of that. An engineer reading it still has to guess which layer to open first.

The way I build evaluation rests on one decision: **the judge returns a diagnosis.** I ask it for a structured, fact-level decomposition: which required facts are present, which are missing, which extra facts were introduced, whether the central claim holds. Every aggregate number is *derived* from those structured verdicts, so every headline percentage traces down to a specific machine-readable record, the same record the engineer reads to fix the system.

From there the measurement becomes layered, and each layer has a different epistemic status:

- **Infrastructure**: did the request even complete cleanly? Deterministic. No judge needed.
- **Retrieval**: was the correct source document actually in the retrieved set? Deterministic and judge-independent. This is the layer that most often explains the failure.
- **Answer quality**: the structured, fact-level judge verdict described above.
- **Stability**: run the same question three times. A question that's right once and wrong twice is *unstable*, which is a different problem with a different fix than a question that fails every time. Separating stable-correct from stable-wrong from these "flippers" tells you where the system is reliable and where it has been lucky.
- **Capability ceiling**: best result across runs. The gap between the ceiling and what the system does *reliably* is your headroom, and it points at exactly where to invest.

**Audit the benchmark before you trust it.** In practice, a meaningful fraction of "failures" turn out to be defective test questions: no valid source mapping, a reference answer that contradicts the documents, a question the corpus genuinely can't answer. Reporting those as system failures is how teams chase ghosts for weeks. Before any result is believed, the benchmark itself gets audited and versioned.

Once the structured verdicts exist, the layered report costs no more to produce than the single number did.
