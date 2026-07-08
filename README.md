# Smikkelen Schranzen Slurpen

A personal collection of food recipes, descriptions, and mildly incoherent
ramblings. Some pages are in English, some in Dutch/Flemish - it depends on
the source material.

Built with [MkDocs](https://www.mkdocs.org/) and the
[terminal](https://github.com/ntno/mkdocs-terminal) theme, deployed to
GitHub Pages.

## Local development

Requires [uv](https://docs.astral.sh/uv/).

```bash
uv sync                 # install dependencies
uv run mkdocs serve     # live preview at http://127.0.0.1:8000
uv run mkdocs build     # build the static site into ./site
```

## Adding a recipe

1. Copy `docs/recipes/template.md` to `docs/recipes/<name>.md`.
2. Fill it in.
3. Add a `nav:` entry for it in `mkdocs.yml` under the right cuisine group
   (a recipe file is not published until it appears in the nav).
4. Preview with `mkdocs serve`, then push to `main`.

## Deployment

Pushing to `main` triggers the GitHub Actions workflow
(`.github/workflows/ci.yml`), which builds the site and deploys it to
GitHub Pages.

## License

See [LICENSE](LICENSE).

## Inspired by

(The best website, ever)[https://thebestmotherfucking.website/]
