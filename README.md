# growing-brand

**Brand memory that grows while you design.**

You already have taste — it shows up every time you tell an AI *"not this one"*, *"warmer"*, *"less rounded"*, *"yes, that's it."* Then the session ends and all of it evaporates. Next session, the AI starts from zero and you correct the same things again.

growing-brand is a thin layer for AI-assisted design work (built for [Claude Code](https://claude.com/claude-code); it's all plain markdown, so any agent that reads skills can use it). It rides along inside your normal work, catches those judgments as they happen, and grows them into a brand system you never had to sit down and write.

**No routine. No ratings. Nothing to run.** You just work — and the work stops forgetting.

## How it works

Three things happen automatically, inside whatever you were already doing:

1. **Apply** — before making design choices, the AI loads your `brand/` files and wears them. The more you've worked, the less generic everything gets.
2. **Capture** — when you pick, reject, correct, approve, or declare a rule, that judgment lands as one line in `brand/journal.md`, in your own words: `7. 2026-07-05 [corrected] buttons rounded-full → 4px — "we're not a toy" (job: pricing page)`.
3. **Distill** — when enough judgments pile up (~10), they're automatically summarized upward. Repeated judgments become rules at the right level; every rule cites the journal entries that earned it. You get a two-line note about what was promoted — and pushing back on a promotion is itself a judgment.

## What you end up with

Four plain markdown files in your repo — yours to read, edit, or delete. Hand edits are treated as the strongest signal you can give.

| File | Holds | Changes |
|---|---|---|
| `brand/core.md` | Identity — what we always do, what we refuse | rarely — only rules proven ≥3 times across jobs |
| `brand/tokens.md` | The measurables — color, type, spacing, shape | sometimes |
| `brand/moves.md` | Recurring patterns — how things tend to be done here | as habits emerge |
| `brand/journal.md` | Every judgment, raw and numbered | every session |

Contradictory evidence is never resolved by fiat: it either splits by context ("4px on product UI, 12px on marketing") or sits openly in core's **Tensions** section until more evidence settles it. Rules can be demoted too.

See [`example/`](example/) for a fictional brand after three jobs — including which rules got promoted and why.

## Install

**As a Claude Code plugin:**

```
claude plugin marketplace add vivian-chi/growing-brand
claude plugin install growing-brand@growing-brand
```

(Or from a local clone: `claude plugin marketplace add /path/to/growing-brand`, then the same install.)

**Or just copy the skills** (no plugin system needed):

```
cp -r skills/* your-project/.claude/skills/        # this project only
cp -r skills/* ~/.claude/skills/                   # every project (one brand/ per project)
```

For the most reliable auto-triggering, add one line to your project's `CLAUDE.md`:

> Use the brand-memory skill for all design and visual work.

## Start

Run **`/brand-init`** in your project. If you already have design work there (CSS, tokens, components, a live site), it seeds the measurables from what exists — marked unconfirmed until real use proves them. It asks at most three one-line questions about identity; all skippable. **Cold start is fine** — empty files plus the journal will grow everything.

Or don't even init: the first time you make a design judgment, the layer offers once to start remembering. Say yes and keep working.

## FAQ

**Where does my data go?** Nowhere. Everything is local markdown in your repo. Nothing is sent, synced, or stored anywhere else.

**Can I edit the files by hand?** Please do — they're yours. A hand edit counts as the strongest kind of judgment.

**Does it generate designs?** No. It's a memory layer that sits under whatever generates — it makes the output wear *your* accumulated taste instead of the model's defaults, and it gets sharper every time you react.

**Teams?** v0 is one brand per project, grown by whoever works in it. Shared/team flows are on the roadmap.

**Why files and not a database?** So the brand is portable, diffable, reviewable, and still yours if you stop using the tool.

## Status

v0.1 — young and honest about it. The loop (apply → capture → distill) is fully specified and tested end-to-end; the file format may still evolve. Issues and picks-over-flattery feedback welcome.

MIT © Vivian Chi
