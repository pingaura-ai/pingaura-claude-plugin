---
name: prompt-tracking-setup
description: Set up or tidy the prompts PingAura tracks for a brand. Use when the user wants to track new questions people ask AI assistants, organise prompts into topics, archive or restore prompts, or asks which prompts they are tracking.
---

Help the user track the right questions in PingAura.

1. Pick the domain with `list-domains`, then see the current setup with `list-prompt-topics` and `get-prompt-scores` for the domain.
2. Suggest prompts the way a buyer would ask an AI assistant, not as keywords. For example "What are the best tools for X for small agencies?" rather than "X tools". Cover a mix of category questions, comparisons and problem questions, and avoid prompts that only name the user's own brand unless they ask for branded tracking.
3. Show the proposed prompts and topics and wait for the user to confirm before creating anything.
4. On confirmation:
   - Create missing topics with `create-prompt-topic`.
   - Add each prompt with `create-prompt`, in the right topic.
   - Move existing prompts with `move-prompt-to-topic`, and rename topics with `update-prompt-topic`.
5. To clean up, archive prompts the user no longer wants with `archive-prompt` (they can be brought back with `restore-prompt`). Delete a topic with `delete-prompt-topic` only when the user asks, and say what happens to its prompts first.

Tell the user that new prompts are included from the next visibility run, and check `get-quota-usage` if they are close to their plan's prompt limit.
