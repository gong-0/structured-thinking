# structured-thinking

A Claude Code skill for structuring problems with three moves:

1. **Grouping (MECE)**: split sideways so nothing is missing and nothing overlaps.
2. **Process (start to end)**: lay the work out in the order it happens, with no broken links.
3. **Hierarchy (tree)**: stack big to small, conclusion on top, same-size items as siblings.

Claude uses it when you plan a feature, design a classification, audit a system for consistency, trace a number that doesn't add up, write a report, or split work across agents.

## Install

As a plugin (gets updates):

```
/plugin marketplace add gong-0/structured-thinking
/plugin install structured-thinking@structured-thinking
```

To pull a new version: `/plugin marketplace update structured-thinking`, or turn on auto-update for this marketplace in `/plugin`.

Or copy the skill once (no updates):

```bash
git clone https://github.com/gong-0/structured-thinking /tmp/st && cp -r /tmp/st/skills/structured-thinking ~/.claude/skills/
```

## Examples

**MECE.** Order statuses `pending / paid / shipped / delayed` are not MECE: `delayed` uses a different axis (timeliness) and overlaps with `pending` and `shipped`. Split them into two lists: status `pending / paid / shipped / other` and timeliness `on time / delayed`.

**Process.** A monthly report total looks wrong. Walk it end to end: import, validate, calculate, approve, publish. You find that "calculate" was re-run, but "approve" still holds the old result. No step is wrong on its own; the break is at the seam between them.

**Tree.** Put the answer at the top: "Q3 margin fell 4 points." Under it, the causes grouped MECE: price, volume, cost. Under each cause, the evidence.

See [`skills/structured-thinking/SKILL.md`](skills/structured-thinking/SKILL.md) for the full method and self-check.

## License

MIT
