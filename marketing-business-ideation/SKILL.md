---
name: marketing-business-ideation
description: Generate a batch of marketing or business ideas and rank them against a consistent scoring rubric. Use when the user wants to brainstorm business ideas, product angles, marketing campaigns, launch tactics, or growth strategies and wants the output structured, comparable, and prioritized rather than a loose list. Triggers on requests like "give me some business ideas for X", "brainstorm marketing campaigns for Y", "how could we grow Z", or "help me pick between these ideas".
---

# Marketing & Business Ideation

Produce a batch of distinct, concrete ideas in a consistent format, score them
against the same rubric, and hand back a ranked shortlist — not a loose
brainstorm dump.

## When to use this

Any time the ask is "give me ideas for growing/launching/marketing/monetizing
X" or "help me choose between these directions." Skip it for single-answer
questions ("what's a good tagline for X") — this skill is for comparing
multiple options, not producing one deliverable.

## Process

1. **Clarify scope before generating, only if genuinely missing:**
   - What is being ideated on (a new business, a product feature, a
     marketing campaign, a growth/acquisition tactic, a pricing model, etc.)
   - The audience/market and any hard constraints (budget, team size,
     timeline, channels already in use, things explicitly off the table)
   - How many ideas they want (default to 6 if unstated — enough to compare,
     not so many the ranking becomes noise)
   Don't stall on this — if the request already gives enough to work with,
   proceed and state the assumptions you made instead of asking.

2. **Generate ideas as idea blocks.** Write each idea using the template in
   `idea-block.md`. Keep ideas genuinely distinct from each other — different
   mechanisms or angles, not the same idea with a different adjective. Favor
   specificity (a named channel, a concrete mechanic, a real audience
   segment) over generic advice ("improve your social media presence" is not
   an idea).

3. **Score every idea with the same rubric.** Apply the criteria in
   `scoring.md` to each idea and show the per-criterion scores, not just a
   final number — the breakdown is what lets the user disagree with one
   dimension without discarding the whole score.

4. **Rank and present:**
   - A summary table: idea name, total score, one-line verdict.
   - Full idea blocks with scores, ordered highest to lowest.
   - Call out the top 1-2 picks explicitly with a one-sentence "why this
     one" — don't make the user re-derive the recommendation from a table.
   - Note any idea that scores well but has a specific blocker worth flagging
     (e.g., high score but depends on a channel the user said is off-limits).

5. **Offer to go deeper** on any specific idea (a fleshed-out launch plan, a
   sample campaign asset, a first-week action list) rather than expanding all
   of them unprompted — that's usually more than the user needs on the first
   pass.

## Ground rules

- Never pad the count with filler ideas just to hit a target number; fewer
  strong, distinct ideas beat a longer list with duplicates.
- Don't rescue a weak idea with a high score to make the list feel balanced —
  a low score is useful signal, leave it low.
- If the user pushes back on a score, treat it as new information about their
  actual constraints (e.g., they know their audience won't respond to a
  channel you rated highly) and re-score rather than defending the original
  number.
