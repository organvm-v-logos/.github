# Quick Start

A newcomer's entry point to **ORGAN-V: Logos** — the public-process layer of the
[organvm system](https://github.com/meta-organvm). This guide answers the two
questions people ask first: **which repository do I clone?** and **how do I run
it locally?**

> New to the organ itself? Read the [organization profile](profile/README.md)
> for what ORGAN-V is and why it exists. This guide is purely operational.

---

## 1. Which repository do I clone first?

There is no single "main" repo to clone — ORGAN-V is a small constellation of
repositories, each with one job. Pick the one that matches your goal:

| I want to… | Clone this repo | Stack |
|:-----------|:----------------|:------|
| **Read or edit the essays** (the flagship content) | [`public-process`](https://github.com/organvm-v-logos/public-process) | Jekyll static site |
| **Work on essay automation** (monitor, narrator, validator, indexer) | [`essay-pipeline`](https://github.com/organvm-v-logos/essay-pipeline) | Code/automation |
| **Work on engagement analytics** (GoatCounter, metrics, dashboards) | [`analytics-engine`](https://github.com/organvm-v-logos/analytics-engine) | Code/automation |
| **Update voice guide, rubrics, or frontmatter schema** | [`editorial-standards`](https://github.com/organvm-v-logos/editorial-standards) | Docs + schemas |
| **Curate reading lists / RSS feeds** | [`reading-observatory`](https://github.com/organvm-v-logos/reading-observatory) | Code/automation |
| **Change org-wide governance** (templates, this guide) | [`.github`](https://github.com/organvm-v-logos/.github) | Governance |

**If you're just exploring and don't know where to start, clone
[`public-process`](https://github.com/organvm-v-logos/public-process).** It is
the flagship repository — the live essay site — and it gives you the clearest
picture of what this organ produces. The published site is at
**[organvm-v-logos.github.io/public-process](https://organvm-v-logos.github.io/public-process/)**.

---

## 2. How do I run it locally?

Every repository documents its own exact setup and validation commands in its
`README.md`. **The repo README is always the source of truth** — start there
after cloning. The patterns below get you moving.

### General pattern (any repo)

```bash
# 1. Clone
git clone https://github.com/organvm-v-logos/<repo-name>.git
cd <repo-name>

# 2. Read the README first — it lists the real setup + validation commands
#    Look for an `## Setup`, `## Getting Started`, or `## Development` section.

# 3. Install dependencies (whichever the repo uses)
npm install        # for TypeScript/Node repos
# or
pip install -r requirements.txt   # for Python repos

# 4. Run the repo's validation commands (tests / lint) before changing anything
```

### The essay site (`public-process`)

`public-process` is a Jekyll site. To preview essays locally:

```bash
git clone https://github.com/organvm-v-logos/public-process.git
cd public-process
bundle install
bundle exec jekyll serve   # → http://localhost:4000
```

Then open the local URL in a browser. Confirm the exact command in that repo's
README — it is authoritative if it differs from the above.

### Code / automation repos

`essay-pipeline`, `analytics-engine`, and `reading-observatory` are code
repositories. Per the [contribution standards](CONTRIBUTING.md) they use:

- **TypeScript** — strict mode, named exports, `async/await`
- **Python** — PEP 8, type hints, f-strings

After installing dependencies, run the repo's test command (listed in its
README) to confirm a working local setup before making changes.

---

## 3. First contribution

Once you can run things locally:

1. Pick an issue labeled **`good first issue`**.
2. Confirm scope, validation commands, and acceptance criteria before coding.
3. Fork → branch (`feature/your-feature` or `fix/your-fix`) → keep changes focused.
4. Run the repo's local validation commands.
5. Open a PR with a clear description.

Full details — accepted change types, review SLAs, development standards — are in
**[CONTRIBUTING.md](CONTRIBUTING.md)**.

---

## Where to go next

- **[Organization profile](profile/README.md)** — what ORGAN-V is and how it fits the eight-organ system
- **[CONTRIBUTING.md](CONTRIBUTING.md)** — full contribution workflow and standards
- **[CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)** — community expectations
- **[SECURITY.md](SECURITY.md)** — reporting vulnerabilities
- **[README standards](README_STANDARDS.md)** — README structure each repo follows

---

*Part of the [organvm eight-organ system](https://github.com/meta-organvm) · ORGAN-V: Logos*
