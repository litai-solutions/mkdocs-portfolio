# Auth notes for pushing to litai-solutions org

> Written 2026-06-09 during laptop migration. Both lestarr and litus initially failed to push from this directory — this is what finally worked.

## Why default `git push` fails

```bash
git push
# remote: Permission to litai-solutions/mkdocs-portfolio.git denied to lestarr.
# fatal: ...The requested URL returned error: 403
```

**Reason:** `gh auth` provides an OAuth token scoped to **lestarr's personal repos**. lestarr is **not a member** of the `litai-solutions` org. The token works for cloning (public read) but not pushing.

Verify any time:
```bash
gh api user/memberships/orgs/litai-solutions
# {"message":"Not Found",...,"status":"404"}  ← lestarr is not a member
```

## What works

Use an **org-scoped classic Personal Access Token** for `litai-solutions`. Embed it in the remote URL or use it via a credential helper.

```bash
# One-time: set remote URL with org PAT
git remote set-url origin "https://<ORG_PAT>@github.com/litai-solutions/mkdocs-portfolio.git"
# Then normal push works:
git push
```

The same `<ORG_PAT>` also works for `litai-solutions/trivi-bot`. Get it from 1Password under "litai-solutions org PAT".

## On a fresh clone (new Mac)

`gh repo clone litai-solutions/mkdocs-portfolio` will give you a remote like
`https://github.com/litai-solutions/mkdocs-portfolio.git` — no auth in URL. Pushes will fail with 403 until you do the `set-url` step above.

## Cleaner long-term fix

Ask the litai-solutions org owner (yourself? or another admin) to add lestarr as a **Member** (or as outside collaborator on specific repos). Then `gh repo clone` is enough — no PAT needed in URLs.

Until that's done, the org-PAT workaround is the only way.
