# Development notes

## How publishing works

Every push to `main` runs [`workflows/publish.yml`](workflows/publish.yml), which renders the site and deploys it to GitHub Pages. The build does not run any Python: it reuses the code results saved in `_freeze/`. Those results are only updated when a page is rendered locally, so they must be committed along with any change to a page that has code.

## Setup on a new machine

Requires Git, [Quarto](https://quarto.org/docs/get-started/) 1.10+, and Python 3.14.

```sh
git clone https://github.com/ericgxzhao/ericgxzhao.github.io.git
cd ericgxzhao.github.io

# Python environment for the posts' code
python -m venv .venv
.venv/Scripts/python -m pip install -r requirements.txt   # macOS/Linux: .venv/bin/python

# Tell Quarto to use it (this file is git-ignored)
# Windows PowerShell:
Set-Content _environment.local "QUARTO_PYTHON=.venv/Scripts/python.exe" -Encoding ascii
# macOS/Linux:
echo "QUARTO_PYTHON=.venv/bin/python" > _environment.local

# Enable the pre-commit check
git config core.hooksPath .githooks
```

## Everyday workflow

```sh
git pull
quarto preview          # live preview while editing
```

- **Page without code** (About, Resume, styling): edit, commit, push.
- **Page with code** (most blog posts), including prose-only edits: run `quarto render <file>`, then commit the page together with the updated `_freeze/`.

The pre-commit hook blocks a commit whose saved results are out of date and prints the exact command to run.

## Layout

| Path | Contents |
|---|---|
| `index.qmd`, `resume.qmd`, `about.qmd` | Top-level pages |
| `blog/posts/<slug>/index.qmd` | Blog posts |
| `hw/` | Course assignments and the data some posts read |
| `files/` | Profile photo, resume PDF, images |
| `_freeze/` | Saved code results (commit these) |
| `_site/` | Local build output (git-ignored) |

Markdown files in the project are published as site pages (except `README.md` and anything in a folder starting with `.` or `_`), which is why these notes live in `.github/`.
