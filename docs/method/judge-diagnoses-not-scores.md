---
title: The judge does not score. The judge diagnoses.
description: Two competent LLM graders can disagree by 20+ points on the same answers. A layered evaluation that separates infrastructure, retrieval, generation, and stability failures, instead of collapsing them into one misleading number.
---

# The judge does not score. The judge diagnoses.

Here's the number that should worry anyone shipping enterprise search: on the *same set of answers*, two competent LLM graders can disagree by more than twenty percentage points on how many are "correct." If your quality metric is a single accuracy score from a single judge, you don't know whether you improved the system or just changed the grader.

Most retrieval evaluation is broken in a specific way: it collapses three different kinds of failure into one number. An answer can be wrong because retrieval missed the source document, because the model wrote badly from a good document, or because the request never completed at all. "62% correct" tells you none of that, and you can't fix what you can't separate.

The way I build evaluation rests on one decision: **the judge does not produce a score, it produces a diagnosis.** Instead of asking an LLM for a 0–1 rating, I ask it for a structured, fact-level decomposition: which required facts are present, which are missing, which extra facts were introduced, whether the central claim holds. Every aggregate number is *derived* from those structured verdicts. It is never the input. That means every headline percentage traces down to a specific machine-readable record, the same record the engineer reads to fix the system.

From there the measurement becomes layered, and each layer has a different epistemic status:

- **Infrastructure**: did the request even complete cleanly? Deterministic. No judge needed.
- **Retrieval**: was the correct source document actually in the retrieved set? Deterministic and judge-independent. This is the layer most teams skip, and it's the one that most often explains the failure.
- **Answer quality**: the structured, fact-level judge verdict described above.
- **Stability**: run the same question three times. A question that's right once and wrong twice is not "67% correct"; it's *unstable*, and that's a different problem with a different fix. Separating stable-correct from stable-wrong from these "flippers" tells you where the system is reliable versus merely lucky.
- **Capability ceiling**: best result across runs. The gap between the ceiling and what the system does *reliably* is your headroom, and it points at exactly where to invest.

One more thing that helps real evaluation: **audit the benchmark before you trust it.** In practice, a meaningful fraction of "failures" turn out to be defective test questions: no valid source mapping, a reference answer that contradicts the documents, a question the corpus genuinely can't answer. Reporting those as system failures is how teams chase ghosts for weeks. Before any result is believed, the benchmark itself gets audited and versioned.

None of this is more expensive than a single-number dashboard once it's built. It's just honest about what you actually know, which, in a domain where the search results carry professional and legal weight, is the difference between a demo and a system you can stand behind.
