# Progressive disclosure for repo agent context

How agent context is placed into loading tiers across shikanime repos. The
principle: the agent pays token cost only for what the current task needs.
Each tier loads by a different mechanism — place content by when it is
needed, not by topic.

## Tiers

| Tier | Mechanism | Loads when | Who pays |
|---|---|---|---|
| Root AGENTS.md | full read at session start | always | every session |
| Nested AGENTS.md | read when the agent touches that directory | per touch | sessions in that area |
| Skill (SKILL.md) | name and description always, body on trigger | on trigger | sessions that invoke it |
| Plain docs/ file | only when followed via a pointer | on demand | the reading session |

Import-splitting a root file saves nothing: imports load at launch too.
Splitting organizes; only tier moves gate loading.

## Placement

Root keeps what every task needs: build/test/lint commands, critical
gotchas, rules every task obeys. Move out: framework docs, copy-pasted
templates, file inventories, linter-enforced rules, anything needed in
fewer than ~30% of tasks. Delete outright: generic advice the model
already knows, facts a grep recovers, rules CI already enforces.

Budget: target under 60 lines, ceiling 300. Per-line test: would removing
this line change agent behavior? If not, cut it.

## Pointers

Every pointer names trigger and path: "Before changing billing pages,
read docs/billing-review.md" — not "more docs are in docs/". Moving a
referenced file updates its pointers in the same change. A missing
referenced doc is missing guidance: the agent reports it, never
improvises the procedure.

## Stability

Document capabilities and domain concepts, not file paths — paths drift,
concepts survive. An unverified path in an always-loaded file poisons
every session until someone notices.

## Skills

Seed `.agents/skills/` only with procedures extracted from real runs,
never written in anticipation. Descriptions are the routing surface:
short, trigger-oriented, what the skill does plus when to use it.

## Nested files

A nested `AGENTS.md` earns its place when one directory carries
conventions the rest of the repo does not share — per-package conventions
in a monorepo are the canonical case. Nested files load on touch, so they
are the cheapest correct home for scoped rules.
