# Evals: the point where AI stops being a vibe

## Two types of evals

There are two questions behind most eval work.

Benchmarking asks:
Which option is better?

You compare models, prompts, retrieval strategies, parsing logic, tool flows. The goal is selection.

Regression testing asks:
Did this change make anything worse?

You compare the new version to a trusted baseline. The goal is protection.

Same family, different purpose:

benchmarking helps you choose

regression testing helps you ship without breaking things

2) One dataset can serve both

This is the part people often overcomplicate.

You do not necessarily need one dataset for benchmarking and another for regression testing. The same task bank can serve both.

Say you have 100 fixed extraction tasks or 75 fixed RAG questions.

You run:

Model A

Model B

Prompt v12

Prompt v13

If you use the results to decide which setup is strongest overall, that is benchmarking.

If you use the same results to compare the new version against the current baseline and check for correct-to-wrong flips, latency increases, or schema breakage, that is regression testing.

Same harness. Same tasks. Same scorer.

What changes is the question:

“Which should we adopt?”

“Is it still safe after the change?”

Over time, teams often split the sets:

a broader set for benchmarking

a smaller, stable, high-value set for regression gates

But you do not need that on day one.

3) Core, plus the part people forget

At the core, evals measure answer quality.

For extraction, that may be:

exact match

field-level precision / recall

partial match

JSON validity

For RAG, it may be:

answer correctness

grounding

citation quality

hallucination rate

That is the obvious part.

The less obvious part is that once the eval harness exists, you also get a clean way to track operational behavior on a static bank of tasks:

latency

token usage

cost per task

failure rate

malformed JSON

retries

That is where evals become useful beyond model ranking.

A change can improve quality and still be the wrong decision if it slows the system down too much or doubles cost. Another change may keep quality almost flat but cut failures sharply. Both matter.

4) “Feels better” vs actual numbers

Without evals, teams say:

“It feels better.”

“The new model seems smarter.”

“I think it is faster.”

With evals, they can say:

“Accuracy improved by 2 points.”

“Latency regressed by 29%.”

“Cost per task rose by 42%.”

“JSON failures dropped from 5 to 1.”

That is the shift.

Not from bad engineering to perfect engineering.
From impressions to measurable comparisons.

And that changes the conversation completely.

A prompt change is no longer “I liked the answer better.”
It becomes: worth it or not?

A model upgrade is no longer “this one sounds more intelligent.”
It becomes: what did we gain, what did we pay, what broke?

That is why evals matter. They give you a memory. Without them, every change starts from opinion again.

5) Things worth stealing

Here are a few pieces you can lift directly into your own setup.

A minimal eval starter pack

You need four things:

A static task bank
Start with 30–100 realistic tasks. Include common cases, important edge cases, and known failure patterns.

Expected outcomes
Depending on the system: exact JSON, reference answers, field checks, or pass/fail rubric.

A repeatable run harness
Same tasks, same scoring, same logging.

Structured logging
For each run, capture:

task ID

system version

prompt/model version

score

latency

token usage

cost estimate

output format failures

A useful review format after every change

Change introduced
Switched from Prompt v12 to Prompt v13

Quality delta
+2.1 accuracy points

Operational delta
+29% latency
+42% cost per task

Reliability delta
JSON failures: 5 → 1

Case movement
7 wrong → correct
3 correct → wrong

Decision
Accept / reject / limit to certain workflow

That one template already forces a better conversation.

A few release gates worth having

Even basic thresholds help:

no more than 2 critical correct-to-wrong flips

latency increase must stay under 15%

JSON validity must stay above 98%

cost increase must be justified by measured quality gain

One practical rule

Do not compare a new run to memory.
Compare it to a baseline.

Memory says: “I think this got better.”
A baseline says: “Here is where it improved, here is where it regressed.”

Closing

Evals do not make systems good by themselves.

What they do is simpler and more important: they make change visible.

They let one dataset serve two jobs:

help you choose the stronger system

help you catch damage before it ships

And they replace this:

“It feels better.”

with this:

“Accuracy improved by 2 points. Latency regressed by 29%. Cost per task rose by 42%. JSON failures dropped from 5 to 1.”

That is usually the moment an AI project starts becoming an engineering system.