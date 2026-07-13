---
name: brand-memory
description: Use during any design or visual work — building or styling web pages, components, slides, posters, social images, emails, documents, data visualizations — and whenever the user reacts to something visual (picks one option over another, rejects a direction, asks for a visual change like "warmer" or "less rounded", approves a result, or states a design rule). Loads the project's brand memory from brand/ before design choices are made, quietly records the user's design judgments as they naturally occur, and automatically distills repeated judgments into the brand files. The user never has to invoke anything — this layer rides along inside normal design work.
version: 0.1.0
user-invocable: true
license: MIT
---

# brand-memory — the layer that grows a brand while you design

Nobody writes their taste down in advance. It leaks out one small judgment at a time — "not this one", "warmer", "less rounded", "yes, that's it." Normally those judgments evaporate when the session ends. This skill catches them while the user works and grows them into a brand system the user never had to author.

**The loop: APPLY → CAPTURE → DISTILL.** All three happen inside normal design work. No practice routine, no review sessions, no rating ceremonies — the user just works.

## 0 · When this activates

- Any design/visual making, in any conversation — even one that didn't start as design work.
- Any user reaction to something visual you produced.
- **If the project has a `brand/` folder** (with `journal.md` in it): apply + capture, silently. (If `brand/` belonged to something else at init time, the folder is `growing-brand/` instead — check for `growing-brand/journal.md` too and use that folder throughout.)
- **If it doesn't:** the first time a real design judgment happens, offer once, in one line: *"Want me to remember your design taste as we go? I'll keep it in `brand/` — plain files, yours. (yes / no / `/brand-init` to seed it from your existing work)"*. If yes, create `brand/` from the `brand-init` skill's templates and continue. If no or no answer, drop it — don't ask again this session, work normally.

## 1 · APPLY — before making design choices

1. Read `brand/core.md`, `brand/tokens.md`, `brand/moves.md`, and the undistilled tail of `brand/journal.md` (entries after the `Last distilled` marker — the freshest signal, not yet promoted).
2. Precedence when they speak to the same choice: **core > tokens > moves > journal tail**.
3. Wear the brand by default. Don't ask permission to follow the user's own recorded taste, and don't recite the rules back — just make choices that obey them.
4. **On conflict** — the user asks for something a confirmed rule forbids — say it in one line: *"Your brand notes say [rule] — override here?"* Either answer is a judgment: an override is an exception worth journaling, or the first evidence the rule is wrong.
5. Lines marked `(observed)` or `(seeded)` are weaker than lines carrying journal evidence — bend those without asking.

## 2 · CAPTURE — record judgments as they happen

**What counts** (each becomes one journal line):

| Type | Looks like |
|---|---|
| `[picked]` | chose one option over another — "the second one" |
| `[rejected]` | turned a direction down — "no purple", "not this" |
| `[corrected]` | asked for a visual change — "warmer", "smaller", "less rounded" |
| `[approved]` | accepted a result — "yes", "ship it", "love this" |
| `[stated]` | declared a rule outright — "we never use stock icons" |

**How to record:** append to `brand/journal.md` under `## Entries`, numbered sequentially:

```
7. 2026-07-05 [corrected] buttons rounded-full → 4px — "we're not a toy" (job: pricing page)
```

- **Quote the user's actual words** whenever they gave a reason. Their words are the data — don't paraphrase them into blandness.
- One line per judgment; always name the job (what was being made).
- Write silently — don't interrupt the flow to announce a journal entry.
- A user hand-editing any `brand/` file is the strongest signal there is — treat the edit as `[stated]`.

**Signal discipline — do NOT record:** functional fixes (broken link, typo, bug), pure content/copy edits, indecision or thinking-out-loud, my own choices the user never reacted to, anything personal or sensitive. If one session produced a pile of judgments, keep the strongest ~8 — a journal padded with noise distills into a mushy brand.

## 3 · DISTILL — automatic summarize-upward

**Trigger — no permission, no ceremony:** after appending, if undistilled entries ≥ 10, distill in the same session. Also distill when loading a brand whose backlog is already ≥ 10.

1. Read all undistilled entries plus the three brand files.
2. Find repetition: the same preference or aversion appearing **≥ 2 times across different jobs**.
3. Promote each pattern to the level it belongs to:
   - a measurable (color, type, spacing, radius, density) → `tokens.md`
   - a recurring element, composition habit, or "never appears" → `moves.md`
   - an identity-level always/never, **≥ 3 consistent occurrences across ≥ 2 jobs** → `core.md` — and keep core small (~15 rules max; when in doubt, it's a token or a move, not core)

   Two shortcuts past the repetition bar: a **single entry that confirms an existing `(observed)`/`(seeded)` line** upgrades it — drop the marker, cite the entry. A **`[stated]` rule goes straight to its level** — the user said it outright; cite the entry.
4. **Provenance on every promoted or updated line:** `— evidence: entries 5, 11`. A rule that can't cite its entries doesn't get written.
5. **Contradictions are never resolved by fiat.** First try a context split ("4px radius on product UI, 12px on marketing pages" — different jobs, both true). If no clean split, put both sides in core.md's **Tensions** section with their entries and leave it open — later evidence settles it.
6. **Demotion works too:** if new entries contradict a confirmed rule ≥ 2 times, move it to Tensions and say so.
7. Update the journal marker: `Last distilled: <date> · through entry <N>`. Entries stay in the journal — they are the permanent record.
8. **Tell the user what changed in ≤ 3 short lines** — e.g. *"Noticed: you've rejected pure black twice on different jobs — added 'ink #1A1F1A, never #000' to your tokens."* If they push back, that pushback is a judgment: record it and revert the promotion.

## 4 · STATUS — when asked

"What do you know about my brand?" / `/brand-memory` → a short summary: what's in core / tokens / moves (counts + the newest rules), patterns currently forming (seen 2×, not yet promoted), open tensions. No advice, no ceremony.

## Boundaries

- `brand/` belongs to the user: plain markdown in their repo, theirs to edit or delete. Nothing is stored anywhere else; nothing leaves the project.
- Never write into `core.md` without an evidence trail — provenance always.
- One project = one brand. (Different brand → different project/folder.)
- This layer doesn't generate designs by itself — it makes whatever gets generated wear the user's accumulated taste, and gets sharper every time they react.
