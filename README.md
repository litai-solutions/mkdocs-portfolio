# litai-solutions.com

Source of [litai-solutions.com](https://litai-solutions.com), the site of LITAI LLC: search and extraction systems for complex documents, built so teams can measure, trust and improve them.

The site holds case studies, method notes, services and a blog. It is built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

## Run locally

```bash
uv run mkdocs serve -a 127.0.0.1:8001
```

Open http://127.0.0.1:8001. Docker alternative: `./start_server.sh`.

## Build and publish

```bash
uv run mkdocs build --strict
uv run mkdocs gh-deploy
```

Pushing to `main` deploys nothing; the live site changes only after `gh-deploy`.

## Layout

| Path | Content |
|---|---|
| `docs/index.md` | Home page |
| `docs/services.md` | Engagements and pricing |
| `docs/case-studies/` | Case studies |
| `docs/method/` | Method notes |
| `docs/blog/posts/` | Blog posts |
| `mkdocs.yml` | Site configuration and navigation |

## License

See [LICENCE](LICENCE). Site built from the [mkdocs-website-template](https://github.com/data-freelancer-mastermind/mkdocs-website-template).
