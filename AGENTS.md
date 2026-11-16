# GitHub

Organization profile and shared configuration for the shikanime-labs org:
public README, org-wide templates (issue, PR, discussion, CODEOWNERS),
Renovate config, and reusable workflow snippets under `.github/workflows`.

**Language:** Nix (flake-provided dev shell).

## Environment

Direnv loads the flake shell automatically (`.envrc`); without it,
`nix develop`. Run `nix fmt` before shipping — Markdown lines are wrapped
at 80 columns.

## Commit Style

- Plain-text capitalized title, no conventional-commit prefix
- Body labels: `Design:`, `Related:`, `Closes #`

## Landing

`main` is protected: one approving review, linear history, signed
commits, squash-merge only. Informational repo — changes are mostly to
the org profile README.

## Agent context

Before restructuring any repo's agent context (AGENTS.md placement, docs
pointers, skill seeding), read `docs/progressive-disclosure.md` — the org
standard for tiered context loading.
