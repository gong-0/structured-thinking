---
name: structured-thinking
description: >-
  Structure any problem with three moves: group it MECE (sideways), lay it out as a process from start to
  end (time), and stack it as a hierarchy tree (top-down). Use when planning a feature, screen, menu or
  settings system; designing a classification (statuses, categories, cause buckets, filters, tabs); running a
  full audit or consistency check ("is anything missing or inconsistent?"); tracing why numbers don't match;
  writing a report, proposal or plan; or splitting work across people or agents without overlap. Triggers:
  "MECE", "structure this", "organize", "audit everything", "anything missing?", "as a tree", "end to end",
  "plan this", "구조화", "정리해줘", "전수조사", "빠진 거 없나", "트리로", "처음부터 끝까지", "기획해봐", "MECE 해?".
  Skip for typo fixes, one-line questions, or executing work that is already decided.
---

# Structured Thinking

Three moves. Each looks at the problem along a different axis, and they work together:

| Move | Axis | Question it answers | Strongest in |
|---|---|---|---|
| 1. Grouping (MECE) | Sideways — items on the same level | Did I split this so nothing is missing and nothing overlaps? | Classifications, splitting work, checking that parts sum to the total |
| 2. Process (start to end) | Time — what happens first, next, last | Is every step connected, from the first input to the final output? | Audits, tracing a wrong number, release and rollout order |
| 3. Hierarchy (tree) | Top-down — big to small | Does each level hold only things of the same size, under one parent? | Planning (goal → sub-goals → tasks), menu and screen structure, "why" hypothesis trees, reports |

The numbers are names, not an order. On a real problem, usually walk the **process** first to see the whole, drop into a **tree** at each step, and split every level of the tree **MECE**. For a pure classification task, start with MECE.

## 1. Grouping — MECE

Mutually Exclusive, Collectively Exhaustive.

- **One axis per list.** Don't mix "by region" and "by size" in one list. If two axes show up, make two lists.
- **Exhaustive.** The parts add up to the whole. Keep an explicit bucket for what doesn't fit yet (`Other`, `Undetermined`) rather than dropping it.
- **Exclusive.** Every item lands in exactly one bucket. If an item could go in two, the axis is wrong.
- **Check with numbers when you can.** Sum of parts = total, to the unit. If it doesn't add up, name the remainder (e.g. "not attributable to any contract") as its own line instead of hiding it.

Example: margin = commission margin + bonus margin is MECE if every received and paid amount belongs to exactly one side. If per-contract margins don't sum to total margin, something sits outside contracts. Show it as a line.

## 2. Process — start to end

Lay the work out in the order it actually happens. For each step, write what comes in, what goes out, and who or what owns it.

- **No broken links.** Each step's output is the next step's input. Look for steps that read something stale or never produced.
- **Walk the whole chain.** When auditing, follow the flow end to end instead of jumping between screens or modules.
- **Watch the seams.** Problems cluster where one step is re-run and the next step doesn't know (e.g. step B recalculated, step C still uses old B).
- **Verify each seam against the actual state, not the plan.** At every hand-off, check that the previous step's output really exists, comes from the current run, and is in the shape the next step expects (the schema migrated, the file uploaded, the job finished). A plan that says "B then C" is not evidence that B's output is there.

Example: upload → parse → reconcile → calculate → deduct → close → publish. A later step built on an earlier step's stale output is a process break, even if every step is correct on its own.

## 3. Hierarchy — tree

Go from the conclusion or largest group down to details.

- **Same level, same size.** "Billing" and "a rounding bug" cannot be siblings.
- **Each parent is the sum of its children** (this is MECE applied at every level).
- **Conclusion first.** In writing, the top of the tree is the answer; the branches are the grouped reasons; the leaves are the evidence.

Example: Revenue → profitability analysis → by product / by rep / by contract → per period / lifetime / per unit.

Two uses beyond writing:
- **Planning.** Break the goal into sub-goals, then into tasks. Missing features show up as empty branches.
- **Why-trees.** For "why is this wrong?", branch the possible causes MECE (e.g. bad input / code change / stale step), then rule branches out with evidence one at a time.

## How to apply

**Planning or design**
1. Write the end-to-end process the user or system goes through.
2. Under each step, build the tree of what's needed.
3. Check each level is MECE. Add the `Other` / `Undetermined` bucket.

**Designing a classification**
1. Name the single axis.
2. List the buckets, including the leftover bucket.
3. Test: can any real item fall into two buckets, or none? Can the buckets be summed to the total?

**Audit or consistency check**
0. **Fix the scope first.** "Check it" means every layer unless the user narrows it. Write the layers as a MECE list, map what has already been checked onto it, and name the gaps before starting. For a software product, a good default is one axis, product layer top to bottom:
   design (structure as a tree, classifications MECE, flows end to end) · logic (one source per concept, preview = real) · data (right population, no silent defaults, parts sum to total) · access (roles, tenants) · presentation (wording, leftover dev traces) · operations (deploys, running servers, environments, tests touching shared data) · other.
1. Split the system MECE into areas (and give each area to one person or agent, so work does not overlap).
2. Within each area, walk the process end to end.
3. For each concept, find every place that computes or decides it. Two places with two formulas is a finding.
4. Report as a tree: severity groups → findings → evidence.

**Tracing a number that doesn't match**
1. Walk the process backwards from the wrong number.
2. At each step, check its input is from the same run and time as its output.
3. The first step where the input is wrong or stale is the break.

**Splitting work across people or agents**
1. Split the work MECE by one axis (area, file set, or process step) so no two owners touch the same thing.
2. Order the pieces by the process: what must finish before what can start.
3. At each hand-off, state what the next owner receives and how they can check it exists (see "Verify each seam").

**Writing a report or proposal**
1. Answer first (top of the tree).
2. Group the support MECE, each group with one heading.
3. Order items within a group by the process (or by severity when there is no process).

**Anything else**
Pick the move that matches the question: "is anything missing or overlapping?" → MECE; "in what order, and where does it break?" → process; "what is the big picture and what sits under it?" → tree. Then run the self-check.

## Self-check before you answer

- [ ] Each list uses one axis only.
- [ ] Parts sum to the whole, or the remainder is named.
- [ ] No item fits in two places.
- [ ] The flow has no gap from first input to final output.
- [ ] Every seam was checked against the actual state (output exists, current run, expected shape), not assumed from the plan.
- [ ] Siblings in the tree are the same size; the answer is at the top.
- [ ] One name means one thing, and one thing has one name (trees don't catch this; keep a small name table).
