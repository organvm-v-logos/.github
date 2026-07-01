# Changelog

All notable changes to the organvm-v-logos org-level community health files.

## [Unreleased]

### Added
- Quick Start guide for issue #20, clarifying which Logos repository to clone
  first and how to run local checks for this governance repo.
- Activation audit (`docs/activation-audit-2026.md`) for issue #15 — verdict actually-live, ship now
- 2026 distribution/conversion experiment synthesis for issue #5
- Initial community health files (README, CONTRIBUTING, CODE_OF_CONDUCT, templates)
- Organization-level CI workflow templates
- organ-aesthetic.yaml visual identity cascade

### Changed
- `README_STANDARDS.md` enforcement section now references the real mechanisms (`.githooks/pre-commit`, `ci-minimal.yml`) instead of a non-existent audit script

### Removed
- Dead duplicate `workflows/stale.yml` (outside `.github/workflows/`, never executed; pinned `actions/stale@v9`). The live `.github/workflows/stale.yml` on `@v10` is the single stale sweep.
