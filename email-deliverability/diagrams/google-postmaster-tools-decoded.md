# Diagram: Google Postmaster Tools Decoded

**Type:** Structured reference card — eight dashboard panels with version badges, thresholds, and action guidance

**Purpose:** Be the single canonical reference for "what does each Google Postmaster Tools dashboard mean, what should I look for, and what do I do when something is wrong?" — the question every email sender asks after setting up GPT and seeing data they don't know how to interpret.

**Strategic intent:** Google's own documentation explains each dashboard but doesn't give practitioners a visual decision framework for acting on them. Every other GPT guide either parrots the docs or is built on outdated v1 assumptions without acknowledging the v2 transition. This diagram fills both gaps — it's accurate to the current state (v1 still emitting data, v2 as the default going forward) and it adds the interpretation layer Google doesn't provide: what "good" looks like, what the traps are, and what to do when metrics are unhealthy.

**Data constraint:** Every metric, threshold, definition, and caveat comes exclusively from Google Workspace Admin Help documentation — four specific pages. No third-party interpretation, no estimated benchmarks, no anecdotal thresholds.

## What makes this unique — three features nobody else has:

1. **Version badges on every panel.** Each of the eight dashboards carries a badge — V1+V2, V2 ONLY, or V1 ONLY. No other reference tells practitioners which dashboards exist in which interface. Someone still on v1 instantly knows they don't have Compliance Status. Someone on v2 knows Reputation dashboards are going away. This is the single most useful piece of orientation for anyone navigating the transition.

2. **"What Postmaster Tools Does NOT Show" panel.** Explicitly listing what GPT cannot tell you — open rates, click rates, inbox placement rate, automatic spam filtering decisions, real-time data, individual recipient data, Google Workspace accounts, third-party spam reports. This section builds trust by preventing the misinterpretations that plague every other GPT guide. Most practitioners overestimate what GPT shows them.

3. **Spam rate nuances.** Four specific traps most people fall into, all documented in Google's own help pages: the denominator is inbox-delivered messages only (not total sent), only DKIM-authenticated messages are counted, a rate of 0% after high history doesn't mean you're clean (it means Gmail is pre-filtering everything so recipients never see it to report), and exceeding 0.3% locks you out of Gmail's mitigation support for 7 consecutive days.

## Eight dashboard panels:

1. **Compliance Status (V2 ONLY)** — Binary pass/fail checklist. All senders: SPF/DKIM auth, DNS records, message formatting, encryption, spam rate. Bulk senders add: DMARC, one-click unsubscribe, honor-unsubscribe. Two states only — Compliant or Needs Work. No score, no gradient. Uses rolling average so changes take up to 7 days. Primary domain only, subdomains roll up.

2. **Spam Rate (V1+V2)** — Percentage of inbox-delivered messages manually marked spam by recipients. Target: below 0.1%. Maximum: below 0.3%. Above 0.3% is a policy violation and triggers enforcement. Key nuances: denominator is inbox-delivered only, DKIM-authenticated messages only, does not include messages Gmail auto-filters to spam, 0% after high history means Gmail is pre-filtering everything. V2 added visual threshold lines to the graph.

3. **Feedback Loop (V1+V2)** — Campaign-level spam reports identified by Feedback-ID header. Requires header setup that most senders skip. Use to pinpoint which specific campaign caused a spam rate spike. More granular identifiers available in v2. The bridge between "my spam rate spiked" and "here's which send caused it."

4. **Domain Reputation (V1 ONLY, announced for retirement)** — Quality rating: High, Medium, Low, Bad. Domain reputation follows you across ESP changes — you can't escape it by switching providers. DKIM or SPF authenticated messages, exact domain match only.

5. **IP Reputation (V1 ONLY, announced for retirement)** — Quality rating: High, Medium, Low, Bad. IP reputation resets when you switch ESPs. Shared IPs mean other senders on that IP affect your rating.

6. **Authentication (V1+V2)** — SPF, DKIM, and DMARC pass rates as percentages. Target: 100% on all three. Any drop indicates a configuration issue — check DNS records, sending infrastructure, and From: domain alignment.

7. **Encryption (V1+V2)** — Percentage of email sent over TLS-encrypted connections. Target: 100%. Required since December 2023. Most modern ESPs enforce TLS by default. A drop below 100% indicates SMTP configuration issues.

8. **Delivery Errors (V1+V2)** — Percentage of authenticated messages rejected or temporarily failed. Error codes: 421 for temporary failures (rate limiting, policy), 550 for permanent rejections (authentication, compliance). Target: 0%. Any spike means check Authentication and Compliance Status dashboards first.

## Additional sections:

- **What Postmaster Tools Does NOT Show** — open rates, click rates, inbox placement rate, automatic spam filtering decisions, real-time data, individual recipient data, Google Workspace (B2B) accounts, third-party spam reports
- **Data Caveats** — updated within 24 hours (not real-time), low-volume days (~100–200 emails) may show no data, uses UTC, Compliance Status uses slightly different datasets than other dashboards, forwarded messages may be included
- **V1 → V2 Transition Note** — v1 deprecated September 2025, v2 is default going forward, IP and Domain Reputation dashboards announced for retirement and will not exist in v2

## Key visual choices:

- Compliance Status panel spans full width because it's the most important dashboard and contains the most items (eight requirements split into all-senders and bulk-senders columns)
- Spam Rate and Feedback Loop paired side by side because they work together — Spam Rate tells you there's a problem, Feedback Loop tells you which campaign caused it
- Domain Reputation and IP Reputation paired side by side to reinforce the comparison your existing Domain vs IP Reputation diagram teaches
- Authentication and Encryption paired side by side as the two "should be 100%" dashboards
- Delivery Errors spans full width because it's the action-oriented dashboard practitioners check after Nov 2025 enforcement
- "Does NOT Show" panel uses red dashed border and red text to visually distinguish it from the dashboard panels — it's a warning, not a feature
- Version badges use three colors: blue for V1+V2, dark for V2 ONLY, amber for V1 ONLY — amber signals "this is going away"

## Sources (all official Google documentation):

- support.google.com/a/answer/14668346 — Postmaster Tools dashboards
- support.google.com/a/answer/81126 — Email sender guidelines
- support.google.com/mail/answer/16594218 — Deprecation of old Postmaster Tools interface
- support.google.com/a/answer/14229414 — Email sender guidelines FAQ

## Update cadence

This diagram must be updated when Google completes the v2 transition, retires the Reputation dashboards, or introduces the new dashboards they've promised to replace them. A "Last updated" indicator on the embedding page signals freshness to crawlers.
