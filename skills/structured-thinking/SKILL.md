---
name: structured-thinking
description: >-
  Structure a multi-part problem: group it MECE, walk the process end to end, stack it as a tree, and verify
  every hand-off against the actual state. Use for planning or design, full audits and consistency checks,
  tracing numbers that don't add up, and splitting work across people or agents. Strong triggers: "MECE",
  "end to end", "audit everything", "anything missing?", "plan this", "전수조사", "빠진 거 없나", "처음부터
  끝까지", "점검", "설계", "기획". Not for quick questions, lookups, or executing decided work.
---

# Structured Thinking

Three moves, each along a different axis:

| Move | Axis | Strongest in |
|---|---|---|
| 1. Grouping (MECE) | Sideways: items on one level | Classifications, splitting work, parts that must sum to a total |
| 2. Process (start to end) | Time: first, next, last | Audits, tracing a wrong number, rollout order |
| 3. Hierarchy (tree) | Top-down: big to small | Planning (goal → sub-goals → tasks), menu and document structure, "why" trees |

The numbers are names, not an order. Usually walk the process first, drop into a tree at each step, and split each level MECE. For a pure classification task, start with MECE.

You already know what MECE, "answer first" and "siblings the same size" mean. This skill adds five things that are easy to skip: **seam checks, number checks, a name table, a default audit scope, and stopping rules.**

## Scale the effort

| Task | Do | Show |
|---|---|---|
| Small: one question or judgment | Run the self-check in your head | A normal short answer |
| Medium: a few parts or steps | Use the one move that fits | One compact list or table |
| Large: many steps, areas or owners | Full method below | Answer first, then the structure |

When in doubt, go one size smaller in the output and keep the full check internal.

**Medium task, good:**
> Three of the five order statuses are fine. `delayed` is on a different axis (timing), so it overlaps `pending` and `shipped`. Split it out: status `pending / paid / shipped / other`, timing `on time / delayed`.

**Same task, over-structured (don't):**
> ## 1. Scope ## 2. Process map ## 3. Issue tree ## 4. MECE analysis … (a page of headings before the one-line answer)

## Seam checks (the most useful part)

Most real defects sit between steps, not inside them. At every hand-off, check against the actual state, not the plan:

- **Exists:** the previous step's output is really there (the file uploaded, the migration applied, the job finished, the approval recorded).
- **Same run:** it comes from the current run. Compare timestamps, run ids, or input fingerprints on both sides.
- **Expected shape:** the next step can read it (same format, same units, same version).
- **Re-run awareness:** if step B is re-run, does step C know? A later step built on stale output is a break, even if every step is right on its own.
- **Clock and source:** when comparing times, make sure both sides use the same clock and time zone.

A plan that says "B then C" is not evidence that B's output exists. If you can't check a seam (no access, blocked), list it as an explicit gap rather than assuming it.

## Number checks

Whenever parts should add up, add them up to the unit.

- Sum of parts = total. If not, the difference is a finding: name the remainder ("costs not assigned to any project", "orders from before the cutover") and show it as its own line.
- Check the same total in every place that shows it (dashboard = report = export).
- A total that looks accurate can hide offsetting errors (one region +30%, another −30%). Break it down one level before trusting it.

## Name table

Keep a small table while you work: one concept, one name, and where each variant appears.

| Concept | Names in use | Pick |
|---|---|---|
| A person who buys | customer / client / user / account | customer |
| "Needs recalculation" | stale / outdated / refreshing / old result | needs recalculation |

Two failure modes, both invisible to MECE and trees: one thing with several names, and one name meaning several things (e.g. "report" for both the weekly email and the export file). Resolve each to one name; if a name must keep two meanings, qualify it.

## MECE, with boundary rules and a cap on "Other"

- One axis per list. If two axes appear, make two lists.
- If an item fits two buckets, either the axis is wrong **or** you need a boundary rule. Often a rule is enough: "if both apply, use the larger amount" or "the first matching rule wins". Write the rule down.
- Keep an `Other` / `Undetermined` bucket so nothing is dropped, but cap it: if it holds more than about 10% of the items or amount, split it again.

## Default audit scope

"Check it" means every layer unless the user narrows it. Before starting, write the layers as one MECE list, map what has already been checked, and name the gaps. Then give each layer or area to one owner.

For a software product, layers top to bottom:
design (structure, classifications, flows) · logic (one source per concept, preview = real calculation) · data (right population, no silent defaults, totals add up) · access (roles, tenants) · presentation (wording, leftover dev traces) · operations (deploys, running servers, environments, tests touching shared data) · other.

For a business plan or proposal: market · customer · offer · economics (unit costs, margins, totals add up) · operations · risks · assumptions not yet checked · other.

For each concept, find every place that computes or decides it. Two places with two formulas is a finding.

## Stopping rules and priority

- Go only as deep as the next action needs. Stop a branch when you know what to do about it.
- Branches that don't change the conclusion collapse into one line.
- Order findings and work by impact: money or security first, then blocked flows, then wording.
- In a large audit, report the top items fully and list the rest briefly. Don't let completeness delay the answer.

## How to apply

**Planning:** write the end-to-end process, build the tree of what each step needs, check each level is MECE with an `Other` bucket. Empty branches are missing features.

**Why-trees:** for "why is this wrong?", branch the possible causes (bad input / logic change / stale step), then rule them out with evidence one at a time.

**Tracing a wrong number:** walk the process backwards; at each step run the seam checks. The first step whose input is wrong or stale is the break.

**Splitting work:** split MECE by one axis (area, file set, or step) so owners never touch the same thing; order pieces by the process; at each hand-off say what the next owner receives and how they can check it exists.

**Reporting:** answer first, support grouped MECE under one heading each, items ordered by process or impact.

## Self-check before you answer

- [ ] Each list uses one axis; overlaps have a boundary rule.
- [ ] Parts sum to the whole, or the remainder is named. `Other` is small.
- [ ] Every seam was checked against the actual state, or listed as unchecked.
- [ ] One name means one thing (name table).
- [ ] Depth stopped where the next action is clear; highest impact first.
- [ ] Output size matches task size.
