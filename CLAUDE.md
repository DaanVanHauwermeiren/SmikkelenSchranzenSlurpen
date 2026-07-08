# CLAUDE.md

## What this is

Personal recipe site - "Smikkelen Schranzen Slurpen". Static MkDocs site
of cooking recipes, built with the `terminal` theme (gruvbox_dark palette)
and deployed to GitHub Pages. Content is a mix of Dutch/Flemish and English
(language follows the source material). Not a Python application - the
`pyproject.toml` exists only to manage the MkDocs toolchain with `uv`.

## Layout

- `docs/` - site content (Markdown). This is where recipes live.
  - `docs/index.md` - home page.
  - `docs/recipes/*.md` - one file per recipe.
  - `docs/recipes/template.md` - copy this to start a new recipe.
- `mkdocs.yml` - site config. **The `nav:` section is manual** - adding a
  recipe file does NOT publish it; you must also add a `nav` entry (grouped
  by cuisine, e.g. Italian / Vlaamsch).
- `.github/workflows/ci.yml` - on push to `main`, runs
  `uv sync --frozen` + `mkdocs build --strict` and deploys `./site` to
  GitHub Pages. Strict build fails on broken links / bad nav paths.
- `pyproject.toml` / `uv.lock` - deps managed with `uv`.
- `site/` - build output. Generated; do not edit by hand.
- `NOTES.md` - scratch. Ignore.

## Commands

```bash
uv sync            # install deps
uv run mkdocs serve  # local preview at http://127.0.0.1:8000 (live reload)
uv run mkdocs build  # build static site into ./site
```

## Adding a recipe

1. Copy `docs/recipes/template.md` to `docs/recipes/<name>.md`.
2. Write the recipe. Section convention: `Ingredients`, `Instructions`
   (numbered), optional `Variations`, `Trouble Shoot`. Prep/Cook/Servings
   header block at top. Two trailing spaces after Prep/Cook lines force line
   breaks - keep them.
3. Add a `nav:` entry in `mkdocs.yml` under the right cuisine group.
4. Preview with `mkdocs serve`, then push to `main` to deploy.

## Conventions

- Write in the source recipe's language; don't translate for its own sake.
- Reference/link the original source when known.
- `markdown_extensions: footnotes` is enabled - footnotes available.
