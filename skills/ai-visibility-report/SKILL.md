---
name: ai-visibility-report
description: Write an AI visibility report for a brand tracked in PingAura. Use when the user asks how their brand is doing in AI answers, for a weekly or monthly AI visibility update, for their AI AuraScore, mention rate or share of voice, or what changed since the last run.
---

Produce a short, decision-ready AI visibility report from the PingAura connector.

1. Find the domain. Call `list-domains` and match the brand or domain the user named. If they named none and there is more than one domain, ask which one.
2. Get the headline numbers. Call `get-visibility-score` for the domain, using its `range` option for the period the user asked for. Report AI AuraScore (0-100), Mention Rate and Share of Voice.
3. Compare runs. Call `compare-visibility-runs` with the two most recent completed runs (or the dates the user gave). Use the default non-branded slice unless the user asks about branded prompts. Add `include_competitors` when the user cares about competitors.
4. Break it down by engine. Call `list-visibility-runs` for the latest run id, then `get-visibility-summary` for that run, and note which AI engines mention the brand most and least.
5. Find the weak and strong prompts. Call `get-prompt-scores` for the domain with `order` set to `score_asc` to list the prompts where the brand scores lowest or is missing, and with `score_desc` for where it is strongest.

Write the report in this order, in plain language:

- **Headline**: one sentence with the score and the change since the previous run.
- **By engine**: a small table of engines with their score.
- **Where we are missing**: up to five prompts with no brand mention, and which competitors appear instead.
- **What to do next**: two or three concrete actions, such as content to write for missing prompts or site issues to fix (use the site-health-triage skill for those).

Rules:

- Treat a null score as "no data for this slice", never as 0.
- If a slice is flagged as too small, say the sample is too small rather than quoting a number.
- Quote numbers as PingAura returns them; don't recompute scores.
- Don't paste raw tool output.
