---
name: ai-visibility-report
description: Write an AI visibility report for a brand tracked in PingAura. Use when the user asks how their brand is doing in AI answers, for a weekly or monthly AI visibility update, for their AI AuraScore, mention rate or share of voice, or what changed since the last run.
---

Produce a short, decision-ready AI visibility report from the PingAura connector.

1. Find the domain. Call `list-domains` and match the brand or domain the user named. If they named none and there is more than one domain, ask which one.
2. Pick the runs. Call `list-visibility-runs` with `one_per_day` set, and take the two most recent days (or the days the user gave). Check each run's `engine_shortfall`: an engine with `answered` 0 did not run that day.
3. Get the headline numbers. Call `get-visibility-score` for the domain, using its `range` option for the period the user asked for. Report AI AuraScore (0-100), Mention Rate and Share of Voice.
4. Compare the runs. Call `compare-visibility-runs` with the two runs and a `non_branded` slice, plus one slice per engine (`engine` set) for the engine breakdown. If an engine ran on one day and not the other, say so and do not count its change as a real gain or loss.
5. Find the competitors. Call `get-visibility-summary` for the latest run. `competitor_scores` lists the brands AI answers mention most, with their score and share of voice.
6. Find the weak and strong prompts. Call `get-prompt-scores` with `order` set to `score_asc` for the prompts where the brand scores lowest or is missing, and `score_desc` for where it is strongest. These rows carry the brand's own score per prompt, not which competitors appeared.

Write the report in this order, in plain language:

- **Headline**: one sentence with the score and the change since the previous run.
- **By engine**: a small table of engines with their score, marking any engine that did not run.
- **Where we are missing**: up to five prompts where the brand scores 0, and the competitors leading the run overall.
- **What to do next**: two or three concrete actions, such as content to write for the missing prompts or site issues to fix (use the site-health-triage skill for those).

Rules:

- Treat a null score as "no data for this slice", never as 0.
- If a slice is flagged as too small, say the sample is too small rather than quoting a number.
- Quote numbers as PingAura returns them; don't recompute scores.
- Don't paste raw tool output.
