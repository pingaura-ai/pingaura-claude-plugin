---
name: competitor-gap-analysis
description: Compare a brand with its competitors in AI answers using PingAura. Use when the user asks who AI assistants recommend instead of them, how they rank against competitors, which competitors are gaining, or wants to add, rename or stop tracking a competitor.
---

Show where competitors win AI answers and what the brand can do about it.

1. Pick the domain with `list-domains`, then list tracked competitors with `list-competitors`.
2. Pick the runs. Call `list-visibility-runs` with `one_per_day` set and take the two most recent days. If an engine has `answered` 0 in either run's `engine_shortfall`, say that the comparison excludes it or compare per engine.
3. Rank the field. Call `compare-visibility-runs` for those runs with a `non_branded` slice and `include_competitors` set, so each competitor gets a Rank, Mention Rate and Share of Voice next to the brand.
4. Find the gaps. Call `get-prompt-scores` with `order` set to `score_asc` to list the prompts where the brand scores lowest. Group them by topic with `list-prompt-topics` when topics exist. To see which competitors lead a topic, add a slice with that `topic_id` to `compare-visibility-runs`.
5. Spot brands that aren't tracked. `get-visibility-summary` for the latest run lists the brands and sites AI answers mention most. Some are not competitors but cited sources such as search engines, forums or blogs, often with a `mention_count` of 0. Only suggest tracking a brand that sells a competing product and is mentioned in answers.

Present:

- A ranking table: brand and competitors with Rank, Mention Rate and Share of Voice, and the change since the previous run.
- The three biggest gaps: prompts or topics where the brand scores lowest, with the competitors that lead those topics.
- Suggested actions: content or pages that would answer those prompts.

Changing the tracked list:

- To start tracking a brand, call `add-competitor` after the user confirms the name and domain.
- To rename one, call `update-competitor`. To stop tracking one, call `delete-competitor`, and confirm with the user first, because it removes the competitor from future reports.
- Never add, rename or remove competitors without the user asking for it.
