# Contributing

Thanks for your interest in contributing! This organization publishes essays,
process documentation, and methodology writing, along with the automation that
supports them. Contributions of all sizes are welcome — typo fixes, docs, bug
fixes, and new ideas.

By participating, you agree to follow our [Code of Conduct](CODE_OF_CONDUCT.md).

## Ways to contribute

- **Ask a question or start a conversation** — use
  [GitHub Discussions](https://github.com/organvm/dot-github--logos/discussions)
  for community interaction, open-ended ideas, and feedback that is not yet a
  scoped change.
- **Report a bug or suggest an idea** — open an [issue](../../issues). For
  anything large (a new essay topic, a change to the publishing workflow, an
  editorial policy update), open an issue to discuss it before writing code.
- **Pick up existing work** — issues labeled `good first issue` are a great
  starting point.
- **Open a pull request** — see the workflow below.
- **Report a security vulnerability** — please follow [SECURITY.md](SECURITY.md)
  instead of opening a public issue.

## Pull request workflow

1. **Fork** the repository and create a branch from `main`.
2. **Make your change.** Match the style of the surrounding code or prose, and
   keep the change focused — smaller PRs are easier to review and merge.
3. **Run the repo's checks** (tests, lint, build) if it has them. Each repo's
   `README` lists its setup and validation commands.
4. **Open a pull request** with a clear description of what changed and why.
   Link any related issue.

A maintainer will review and may suggest changes before merging. We aim to give
an initial response within a few business days; please be patient if it takes a
little longer.

## Style guidelines

These are conventions, not gates — follow them where they apply, and ask if
you're unsure.

- **Commits** — write clear messages in the imperative mood ("Fix typo in
  intro"), with a title under ~72 characters.
- **TypeScript** — strict mode, named exports, `async/await`.
- **Python** — PEP 8, type hints, f-strings.
- **READMEs** — follow the [README standards](README_STANDARDS.md).
- **Essays** — include the YAML frontmatter described in the publishing guide
  (title, author, date, tags, category, excerpt, and the other fields listed
  there).
- **Tests** — if you change code that has tests, please keep them passing and
  add coverage for new behavior.

## Getting help

- Start a
  [GitHub Discussion](https://github.com/organvm/dot-github--logos/discussions)
  with questions, reception notes, or open-ended feedback.
- Open an [issue](../../issues) when the request is actionable and scoped.
- Check the relevant repo's `README` — it's the source of truth for that repo's
  setup and workflow.

---

*Part of the [organvm system](https://github.com/meta-organvm).*
