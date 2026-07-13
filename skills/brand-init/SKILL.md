---
name: brand-init
description: Use when the user wants to set up, initialize, or start brand memory in a project ("/brand-init", "start remembering my brand", "set up growing-brand"), or accepts the brand-memory skill's first-run offer. Creates the brand/ folder, seeds it by scanning the project's existing design work (CSS, tokens, components, style guides) when there is any, asks up to three one-line identity questions, and hands off to the ambient brand-memory skill. Cold start with empty files is fully supported.
version: 0.1.0
user-invocable: true
license: MIT
---

# /brand-init — start brand memory in this project

One-time setup. Everything after this is ambient (see the `brand-memory` skill): the user just works, the brand grows.

## 1 · Check

If `brand/journal.md` already exists → this project is already growing. Give the short status summary (brand-memory §4) and stop. If a `brand/` folder exists but isn't ours (no journal, different content), use `growing-brand/` as the folder name instead and say so in one line.

## 2 · Create

Copy the four templates from this skill's `templates/` directory into `brand/`:
`core.md` · `tokens.md` · `moves.md` · `journal.md`. (If the templates aren't available at that path, recreate them from the structure shown in each — header comment + empty sections.)

## 3 · Seed from existing work (only if there is any)

Scan whatever design surface the project already has — stylesheets, tailwind/theme configs, token files, components, an existing site, a style guide:

- **Colors by frequency** → the recurring palette, not every hex that appears once.
- **Type**: families in use, the weights and sizes that repeat.
- **Space & shape**: spacing steps, radius values, border/shadow habits.
- **Moves**: recurring patterns visible in the code or pages (how heroes are built, imagery style, what never appears).

Write these into `tokens.md` and `moves.md`, **every seeded line marked `(observed — unconfirmed)`**. Restraint: seed only what repeats — 12 lines the files can defend beat 40 lines of inventory. These lines harden into confirmed rules (or fall away) as journal evidence arrives.

## 4 · Three questions (optional, one at a time)

Ask up to three, each answerable in one line, each skippable — stop early if the user is brief or busy:

1. *"Name one piece of design — yours or anyone's — you'd be proud to have made. What's the one thing that makes it good?"*
2. *"What's the look you never want — the thing that would make you say 'that's not us'?"*
3. *"Three words your design should feel like — and one it must never feel like?"*

Write the answers into `core.md` as rules **marked `(seeded)`**, phrased in the user's own words as much as possible. Skipped questions cost nothing: core grows from the journal either way.

## 5 · Done — say only this much

Three lines max: where the files live, that from now on it grows by itself while they work (no routine, nothing to run), and that the files are theirs to edit — hand edits are the strongest signal.

**Cold start is fine.** No existing work + all questions skipped = empty templates, and that's a valid start: the tool is designed to begin knowing nothing.
