---
name: proposal-tracker
description: Publish a proposal, offer, or pitch as a tracked link and report back whether it's getting read (view analytics after sending). Use when the user says "send the proposal", "did they open it", "track whether they read it", "share the offer". Not for recurring client reports (use client-reporter) or general research shares (use report-publisher).
---

# Proposal Tracker

The DocSend move, agent-native: publish the proposal as a live tracked page, then answer the question every sender actually has — "is it getting read?" — with view data instead of silence.

Follow the shared flow in the root `SKILL.md`. Proposals are maximally client-facing: approval gate always on, and double-check pricing numbers at the gate.

## When to use

- The user has a proposal, quote, offer, statement of work, or pitch to send to a specific recipient
- The user asks about engagement on something already sent ("did they open it?") → go straight to `get_analytics`

## Steps

1. **Confirm the essentials before authoring.** Recipient (company/person), the offer's core numbers (price, timeline, scope), and the desired next step (call booked? signature? reply?). A proposal without an explicit next step is a brochure.
2. **Structure for a skimming decision-maker.** One-line summary of the offer up top; the "why us / why now" in one short section; scope and pricing in scannable tables; the call to action visible without scrolling far. Long context goes in an appendix.
3. **Author + lint + approval gate.** At the gate, read back the price, timeline, and scope numbers explicitly — a typo in a published price is the worst failure mode this skill has. Note too that the page carries a small "Published with ReportRoom" footer credit the recipient will see.
4. **Publish** with a clean slug. Return the URL and remind the user the link is tracked. When a proposal is dead or superseded, offer to `unpublish` it — the link then returns 410 Gone and the plan slot frees up (`republish` brings it back if the deal reopens).
5. **The follow-up loop is the point.** Offer to check views (`get_analytics`) after a day or two and translate the signal into next actions: viewed-but-no-reply calls for a different follow-up than never-opened. Suggest the follow-up message to match. Be precise about what the data can say: it's view counts by day, not per-person opens — if one recipient got the link, views ≈ their opens; if it was shared around, it's aggregate.

## Hard rules

- Never publish a proposal without the user confirming the price and scope verbatim at the approval gate.
- Analytics are a signal for the *user*, not the recipient — never expose tracking detail on the page itself beyond what ReportRoom discloses.
- If the user wants access control ("only they should see it"), be straight: ReportRoom links are unlisted (hard-to-guess slug on your handle) but not password-protected today. If unlisted isn't enough for this proposal, say so and let the user choose another channel rather than publishing openly and hoping.
