---
name: report-skills
description: Shared setup and rules for the report-skills bundle (report-publisher, client-reporter, proposal-tracker, deck-publisher, report-designer). Loaded by the individual skills for the common ReportRoom MCP publish flow, account bootstrap, and safety gates. Not invoked directly — pick the specific skill for the job.
---

# Report Skills — shared flow and rules

All five skills publish through the **ReportRoom MCP server**. This file holds what they share; each skill's SKILL.md holds only what differs.

## The publish flow (every skill follows this)

1. **Check access.** Call `account_status`. If no account/API key exists, call `create_account` — it issues a key in-flow; never ask the user to leave the conversation to sign up. Note: publishing is blocked until the user clicks the email-verification link (`create_account` sends it), and unverified accounts serve from a preview/noindex domain — tell the user this upfront so the first publish isn't a surprise.
2. **Fetch the design language.** Call `get_design_system` and follow it exactly when authoring. The design system supplies the taste; you supply content and assembly. Do not improvise your own CSS framework.
3. **Author a self-contained HTML document.** Semantic HTML, responsive, dark-mode aware, no external dependencies beyond what the design system allows.
4. **Lint before publish.** Call `lint_document` and fix every issue it reports. Never skip this step.
5. **Approval gate.** Show the user: title, a one-paragraph summary of what the page contains, section list, and who it's for. **Wait for explicit approval before calling `publish` on anything client-facing.** For personal/internal shares the user may pre-approve ("just publish it").
6. **Publish.** Call `publish`. Return the live URL prominently.
7. **Close the loop.** Tell the user view analytics are attached: they can ask any time "how is my report doing?" (→ `get_analytics`, which returns 7-day views by day plus a summary). For tracked deliverables, offer to check back. Do not promise per-viewer or per-section detail — current analytics are aggregate view counts.

## Safety rules (all skills, non-negotiable)

- **Published pages are public URLs.** Before publishing, scan the content for secrets, API keys, internal hostnames, personal data of third parties, or anything marked confidential. If found, stop and ask.
- Never fabricate data, metrics, or client results in a report. If a number is estimated, label it.
- Never publish without the approval gate for client-facing content, even if the user seems in a hurry.
- If `lint_document` or `publish` fails, show the actual error and fix the document — do not silently retry with degraded content.

## Which skill for which job

| The user wants | Use |
|---|---|
| Share research/analysis they just produced | `report-publisher` |
| A recurring, branded deliverable for a client | `client-reporter` |
| A proposal/offer where knowing "did they open it" matters | `proposal-tracker` |
| Slides, not a document | `deck-publisher` |
| An existing page made better-looking | `report-designer` |
