# GitHub

Organization profile and metadata for X-Shikanime.
Contains the public README, shared GitHub configuration, and organizational assets.

**Language:** Nix

## Structure

- `README.md` — Organization profile README displayed on the GitHub org page
- `workflows/` — Shared or template workflow configurations

## Commit Style

- Plain-text capitalized title, no conventional-commit prefix
- Body with labels: `Design:`, `Related:`, `Closes #`
- Keep Markdown lines wrapped at 80 columns and run `nix fmt` before shipping

## Protect `main`

- Require 1 approving review
- Require linear history (no merge commits)
- Require signed commits
- Squash+rebase merge only

*Informational repo; changes are mostly to the org profile README*
