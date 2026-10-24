---
name: competitor-gap-analysis
description: Compare a brand with its competitors in AI answers using PingAura. Use when the user asks who AI assistants recommend instead of them, how they rank against competitors, which competitors are gaining, or wants to add, rename or stop tracking a competitor.
---

Show where competitors win AI answers and what the brand can do about it.

1. Pick the domain with `list-domains`, then list tracked competitors with `list-competitors`.
2. Rank the field. Call `compare-visibility-runs` for the two most recent runs with `include_competitors` set, so each competitor gets a Rank, Mention Rate and Share of Voice next to the brand.
3. Find the gaps. Call `get-prompt-scores` for the domain with `order` set to `score_asc` and collect the low-scoring prompts where competitors are mentioned and the brand is not. Group them by topic with `list-prompt-topics` when topics exist.
4. Spot newcomers. If `get-visibility-summary` for the latest run shows brands that are not in the tracked list but appear often, mention them and offer to track them.

Present:

- A ranking table: brand and competitors with Rank, Mention Rate and Share of Voice, and the change since the previous run.
- The three biggest gaps: prompts or topics where competitors appear and the brand does not, with the competitors named.
- Suggested actions: content or pages that would answer those prompts.

Changing the tracked list:

- To start tracking a brand, call `add-competitor` after the user confirms the name and domain.
- To rename one, call `update-competitor`. To stop tracking one, call `delete-competitor`, and confirm with the user first, because it removes the competitor from future reports.
- Never add, rename or remove competitors without the user asking for it.
