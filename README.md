<p align="center">
  <img src="assets/hero.jpg" alt="Report Skills — 5 Claude Code and Codex skills for AI reports, decks and client sharing via the ReportRoom MCP" width="900" />
</p>

# Report Skills — Claude Code & Codex skills for AI reports, decks & client sharing

<p align="center">
  <img src="https://img.shields.io/badge/Claude_Code-Compatible-D97757?logo=anthropic&logoColor=white" alt="Claude Code Compatible">
  <img src="https://img.shields.io/badge/Codex-Compatible-111827" alt="Codex Compatible">
  <img src="https://img.shields.io/badge/Claude-Skills-8A63D2" alt="Claude Skills">
  <img src="https://img.shields.io/badge/License-MIT-22C55E.svg" alt="MIT License">
  <img src="https://img.shields.io/badge/PRs-welcome-F59E0B.svg" alt="PRs Welcome">
</p>

5 skills that turn what your agent just made — research, analysis, proposals, status updates — into beautiful live web reports and decks you can share with clients and your team. Published in one step via [ReportRoom](https://reportroom.io), with view analytics reported back to you ("your report picked up 42 views this week, peaking Tuesday"). No copy-pasting into Google Docs, no ugly PDF exports.

## What's inside

| Skill | What it does | Say things like |
|---|---|---|
| **report-publisher** | Any research or markdown → live, designed web report with a shareable URL | "publish this", "make this shareable", "turn this into a report" |
| **client-reporter** | Recurring client deliverables (SEO monthlies, status reports, audits) as branded pages | "monthly report for my client", "send this to the client" |
| **proposal-tracker** | Publish a proposal as a tracked link; know whether it's getting read | "send the proposal", "did they open it?" |
| **deck-publisher** | Content → responsive, presenter-friendly slide deck at a live URL | "make this a deck", "turn this into slides" |
| **report-designer** | Polish an existing page to the design bar: hierarchy, charts, dark mode, link previews | "make it beautiful", "improve the design" |

## Install

### Claude Code (CLI)

```bash
/plugin marketplace add dashaworks/report-skills
/plugin install report-skills@report-skills
```

### claude.ai (web)

1. Open https://claude.ai/code
2. Go to **Skills** in the sidebar
3. Click **Add from GitHub**
4. Paste: `dashaworks/report-skills`

### Claude Desktop (Mac / Windows)

1. Click **Customize** → **+** next to **Personal plugins** → **Add marketplace**
2. Choose **Add from a repository** and paste: `dashaworks/report-skills`
3. Install the plugin and start a new conversation

### Codex CLI

```bash
codex plugin marketplace add dashaworks/report-skills
codex plugin add report-skills@report-skills
```

## How it works

The skills publish through the **ReportRoom MCP server** — an agent-native publishing API (one call → live, tracked URL on your domain):

1. `get_design_system` — the agent fetches ReportRoom's design language
2. The agent authors a self-contained HTML report or deck following it
3. `lint_document` — automated quality check before anything goes live
4. `publish` — live URL back in seconds, analytics attached

No ReportRoom account yet? The skills self-provision one on first use — `create_account` issues an API key right in the conversation; verify your email (one click) and publish. Docs: https://docs.reportroom.io

## Why not just export a PDF?

- **Live pages beat attachments** — responsive, dark-mode, always the latest version, presentable from any device.
- **You learn what happens after you hit send** — view analytics come back to the agent as a signal it can act on, not a dashboard you have to remember to check.
- **Beautiful by default** — the design system supplies the taste; the agent supplies the content.

## Safety defaults

Every skill shows you a preview and waits for your approval before anything client-facing goes live. Published pages are public URLs — the skills warn you before publishing anything that looks sensitive.

## License

MIT — see [LICENSE](LICENSE). Contributions welcome.
