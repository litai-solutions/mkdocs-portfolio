# mkdocs-portfolio — litai-solutions.com

Everything under `docs/` is published at `https://litai-solutions.com` under
lestarr's name. It is **creative / professional / published text**, so the
anti-AI-writing guide applies to all of it, in full.

## Writing rules — load before touching `docs/`

@/Users/halyna/pai/lestarr/Config/anti-ai-writing.md

The HARD rules bind here without exception. The ones this repo has actually
violated: §3F negative parallelisms (rated FATAL), §3C dead transitions,
§3E hype language, §4M-bis marketing summary closers, and §2's ban on em dashes.

Check any page you write or edit:

```bash
python3 Plans/Cassian/aiwriting_check.py            # all of docs/
python3 Plans/Cassian/aiwriting_check.py docs/index.md
python3 Plans/Cassian/aiwriting_check.py --review   # + judgment-call greps
```

Report-only, never edits. Exit 1 when it finds hits. It catches the named
patterns, not the guide's catch-all ("ANY sentence that negates one framing then
asserts a corrected one") — a clean run is a floor, not a pass.

Grepping is not a substitute for reading. A flagged line can be the argument
itself; `docs/blog/posts/AI-and-productivity.md` is the voice reference for what
earned contrast looks like.

## Repo invariants

- **Never call lestarr a consultant.** She is a **builder architect**. Or name
  the work: extraction architect, evaluation designer, engineer, computational
  linguist. The site currently contains zero occurrences — keep it that way.
- **Sell artifacts, not outcomes.** "Audit-ready evidence," never "ensures
  compliance."
- **"I", not "we".** Method essays use "I"; three blog posts still say "we".
  New writing uses "I".
- **Pushing to `main` deploys nothing.** No GitHub Action. A visitor sees
  nothing until `uv run mkdocs gh-deploy` runs, and that needs lestarr's
  approval. Verify with `curl` against the live URL, never against `site/`.
- `uv run mkdocs build --strict` must be warning-free before any deploy.
- `docs/case-studies/ai-shop-assistant.md` is disabled via `exclude_docs:` in
  `mkdocs.yml`, not deleted.

## Where the context lives

`Plans/Cassian/` is the site's knowledge base — `STATUS.md` (current numbers),
`KNOWLEDGE.md` (how the site and its instruments work), `DECISIONS.md`,
`PLAYBOOK.md`. Read it before answering questions about this site.
