# PingAura for Claude

Track and improve how your brand appears in AI answers, from a conversation with Claude.

[PingAura](https://www.pingaura.ai) measures how often AI assistants such as ChatGPT, Gemini, Perplexity, Claude, Copilot, Grok, DeepSeek and Google AI Overviews mention your brand, which competitors they recommend instead, and what on your site stops them from citing you. This plugin connects Claude to your PingAura workspace and adds skills that turn that data into reports and next steps.

## What's included

- **PingAura connector**: the remote MCP server at `https://www.pingaura.ai/api/mcp`, with tools for AI visibility scores and runs, competitors, tracked prompts and topics, site health audits, articles and hosted pages.
- **Skills**:
  - `ai-visibility-report`: a short AI visibility report with the score, the change since the last run, a breakdown by AI engine, and the prompts where your brand is missing.
  - `competitor-gap-analysis`: ranks your brand against competitors and finds the questions where they win.
  - `site-health-triage`: turns the latest site audit into a prioritised fix list, and marks issues as fixed when you say so.
  - `prompt-tracking-setup`: suggests and organises the questions PingAura tracks for you.
- **Command**: `/pingaura:visibility-report <domain>` writes the report for one domain.

## Use it

1. Install the plugin, then connect the PingAura connector from the plugin's Connectors tab.
2. Sign in with your PingAura account. On the consent screen, choose the workspace to connect and whether Claude may only read your data or also make changes.
3. Ask Claude things like "How is example.com doing in AI answers this month?", "Which competitors do AI assistants recommend instead of us?" or "What should we fix on our site so AI assistants cite us?"

You need a PingAura account. Sign up at [pingaura.ai](https://www.pingaura.ai). What you can see depends on your plan and the domains you track.

## Data

The plugin itself stores nothing and runs no code on your computer. The skills are instructions for Claude. All data goes through the PingAura connector to your PingAura workspace at `www.pingaura.ai`, over HTTPS, using the OAuth access you approve. Claude only changes data, such as adding a competitor or a prompt, when you ask, and you can choose read-only access when you connect. You can disconnect at any time from Claude's connector settings.

- Documentation: https://www.pingaura.ai/docs/mcp/mcp-server
- Privacy policy: https://www.pingaura.ai/privacy-policy
- Security: https://www.pingaura.ai/security
- Support: support@pingaura.ai

## License

MIT. See [LICENSE](LICENSE).
