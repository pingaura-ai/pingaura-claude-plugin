---
name: site-health-triage
description: Triage website issues that stop AI assistants from crawling or citing a site, using PingAura site audits. Use when the user asks what to fix on their site, about crawlability, AI crawler access, structured data, a site audit, or wants to mark audit issues as fixed or run a new audit.
---

Turn the latest PingAura site audit into a short, prioritised fix list.

1. Pick the domain with `list-domains`.
2. Get the overview with `get-site-health-summary`.
3. Find the latest completed audit with `list-site-audits`. If there is none, or it is older than the user wants, offer to start one with `run-site-audit` and explain that it runs in the background and the results arrive later.
4. Pull the issues with `get-audit-issues` for that audit, starting with `critical` and then `high` severity. Use `list-site-pages` when you need to say which pages are affected.

Present a fix list, most important first:

- **Fix now**: critical and high-severity issues that block AI crawlers or citation, such as blocked crawlers, broken pages or missing structured data. For each, say what is wrong, which pages it affects, and how to fix it.
- **Fix next**: medium-severity issues, grouped by type.
- **Can wait**: low-severity issues, as a count by type.

Keep each fix to one or two sentences a developer or marketer can act on.

Updating issues:

- When the user says an issue is fixed, call `update-issue-status` with status `done` for that issue; use `open` to reopen it. Confirm before changing many issues at once.
- If pages are missing from the audit, offer `sync-sitemap` to refresh the page list before the next audit.
