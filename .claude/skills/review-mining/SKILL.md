---
name: review-mining
description: Mine Google Play Store reviews, Naver Cafe posts, DCInside posts, and similar public app-service feedback for product design work. Use when Codex needs to collect or analyze recent review/VOC text, preferably the last 12 months and UX-focused when not otherwise specified; cluster recurring complaints, usability issues, requests, emotions, and contexts; create a web-readable review mining report; preserve evidence quotes and a raw-results section with privacy redaction; and produce PRD-ready problem-definition inputs such as problem candidates, validation questions, solution-hypothesis candidates, exclusions, and follow-up research questions.
---

# Review Mining

## Purpose

Turn app-service feedback into evidence-grounded product design inputs. Unless the user specifies otherwise, focus on the most recent 12 months and prioritize UX-related signals: usability, information architecture, flow breaks, accessibility, performance, state feedback, onboarding, authentication, payments/deposits/withdrawals, notifications, customer-support touchpoints, and repeated task friction.

Prioritize repeated discomforts and complaints, but do not ignore positive reviews, minority signals, or contextual notes that change interpretation.

## Inputs

Accept Google Play reviews, Naver Cafe posts/comments, DCInside posts/comments, copied text, CSV/spreadsheet data, exported review tables, screenshots, links, search results, or mixed notes.

If the user asks to fetch current reviews or public posts, use available browsing or scraping tools only with permission and cite the source/time. Prefer official or stable sources when available. Respect site terms, robots restrictions, login/paywall boundaries, and rate limits; do not bypass authentication or private communities. If a source cannot be accessed safely, ask the user to provide exports, screenshots, or copied text.

When the user does not specify the period, collect or filter to the most recent 12 months. When the user asks for product design or UX insight, filter to UX-related signals before clustering, while keeping a note about excluded non-UX review types.

## Source Candidates

Use these source types when relevant to an app-service review mining task:

- `Google Play Store`: app reviews, ratings, dates, developer replies when available.
- `Naver Cafe`: app/service community posts and comments, especially troubleshooting, complaints, update reactions, usage tips, and recurring questions.
- `DCInside`: gallery posts and comments discussing app/service issues, community sentiment, workarounds, bugs, and feature requests.
- `App Store`: iOS reviews when requested or useful for cross-platform contrast.
- `Public web search results`: blog/forum posts, support community threads, and social mentions when they include concrete app-service experience.
- `Owned VOC`: customer center tickets, FAQ comments, survey free text, and interview notes when the user provides them.

Record source type, URL or query when available, collection date, access limitations, and whether content is review, post, or comment.

## Normalize Fields

Normalize each item into:

- `source`: Google Play, Naver Cafe, DCInside, App Store, public web, owned VOC, or another explicit source
- `source_type`: review, post, comment, VOC, FAQ, interview note, screenshot, or mixed
- `url_or_location`: URL, query, file name, screenshot name, or export name when available
- `review_id`: stable row number or source id when available
- `date`: if available
- `rating`: if available
- `text`: original text after privacy redaction
- `language`: if relevant
- `app_version/device`: if available
- `ux_relevance`: high / medium / low / non-UX
- `raw_inclusion_note`: why it was included, excluded, or marked non-UX

Redact names, phone numbers, emails, order numbers, addresses, account ids, and any other personal or sensitive data before quoting. Preserve the rest of the original wording as much as possible.

## Workflow

1. Parse and clean the review set.
   - Keep original wording after privacy redaction.
   - Deduplicate exact or near-exact repeated spam only when it would distort the analysis.
   - Keep positive reviews and low-frequency reviews in the dataset.
   - Preserve a raw-results table before summarizing or clustering.
   - If collecting sources directly, save enough metadata for audit: source, date, URL/location, rating when present, and collection time.

2. Apply period and UX filters.
   - Default to the most recent 12 months unless the user specifies another period.
   - Mark UX-related items as high/medium/low relevance.
   - Exclude pure price movement, investment outcome, marketing dislike, or policy anger from UX clusters unless the review also mentions a concrete app/service interaction.
   - Keep excluded categories summarized in the appendix so the filter is auditable.

3. Label review signals.
   - Tag discomforts/complaints first.
   - Also tag requests, emotions, context of use, affected task, suspected journey step, praise, and minority signals.
   - Separate what the user explicitly said from inference.
   - For UX-focused runs, tag by UX surface: onboarding/authentication, search/navigation, chart/data display, transaction flow, notification, performance/stability, accessibility, support/recovery, account/security, and cross-device behavior.

4. Create complaint-first clusters.
   - Group by repeated user pain or product problem, not by feature area alone.
   - Prefer 5-9 useful clusters unless the dataset clearly needs fewer or more.
   - Include a cluster for meaningful minority issues when the issue is severe, specific, or strategically important.

5. Rate each cluster.
   - `frequency`: high / medium / low based on relative occurrence in the provided dataset.
   - `severity`: high / medium / low based on user impact, blocked task, loss of trust, anger, repeated failure, or workaround burden.
   - Avoid pretending these ratings are statistically representative unless the dataset and sampling method support it.

6. Produce a web-readable report first.
   - Create a clean HTML report when a local deliverable is appropriate, or provide a structured Markdown report when the user only needs chat output.
   - Use the report structure in `references/report-structure.md`.
   - Make the report easy to scan: overview, source/method summary, UX filter summary, cluster cards/table, evidence quotes, user-type notes, raw-results section, PRD handoff.

7. Produce a PRD-ready summary.
   - End with exactly the handoff items listed in "PRD Handoff".
   - Keep solution ideas framed as hypotheses, not decisions.

8. Produce raw-results output when requested or when a web report is created.
   - Include one dedicated `Raw Results` section in the web report.
   - For large datasets, include a compact raw-results preview in HTML and provide a separate CSV with all raw rows.
   - Raw rows must be privacy-redacted but otherwise minimally transformed.

## Cluster Fields

Each review cluster must include:

- `cluster_name`: plain-language name for the repeated pain
- `summary`: concise description of what users are struggling with
- `frequency`: high / medium / low
- `severity`: high / medium / low
- `representative_quotes`: up to 15 privacy-redacted original quotes
- `recurring_pattern`: what repeats across reviews
- `affected_users`: user types or situations grounded in review evidence
- `suspected_cause`: clearly marked inference from review evidence
- `caution`: what not to overclaim, what may need verification, or what minority/positive signals complicate the cluster

## Raw Results Fields

When producing raw results, include:

- `raw_row_id`: stable row number used across report and CSV
- `source`
- `source_type`
- `url_or_location`
- `date`
- `rating`
- `title_or_context`: post title, review title, screenshot label, or brief context when available
- `raw_text_redacted`: original text with personal/sensitive data removed
- `ux_relevance`: high / medium / low / non-UX
- `assigned_cluster`: blank if excluded or not clustered
- `tags`: comma-separated signal tags
- `inclusion_note`: why this row was included, excluded, or treated as context

Do not put unredacted personal information in raw results. For very long posts, keep a redacted excerpt in the main CSV and optionally preserve a separate redacted full-text file only if the user needs it.

## User-Type Notes

Do not invent personas before reading the reviews. Derive lightweight user-type notes only from evidence, such as:

- new users confused during first setup
- returning users blocked by changed behavior
- power users hitting workflow limits
- users in urgent or mobile contexts
- users comparing against a competitor or previous version

Mark weakly supported types as tentative. Do not give fictional names, demographic traits, or motivations unless reviews explicitly support them.

## PRD Handoff

End every full review-mining result with:

1. `Problem definition candidates`: exactly 3 candidate problem statements grounded in clusters.
2. `Validation questions`: questions that would confirm, reject, or size the problem.
3. `Solution hypothesis candidates`: possible directions written as hypotheses.
4. `Problems to exclude for now`: issues that are unsupported, out of scope, too rare, or not design-actionable yet.
5. `Additional research questions`: what to ask in interviews, surveys, analytics checks, or usability tests.

## Do Not Claim

- Do not claim Google Play, Naver Cafe, DCInside, or any public review source represents all users.
- Do not overstate frequency beyond the provided review set.
- Do not jump to final solutions before the problem pattern is clear.
- Do not erase positive reviews or minority complaints.
- Do not convert inferred user types into full personas.
- Do not treat review sentiment as proof of root cause.
- Do not quote personal or sensitive information.
- Do not treat anonymous community posts as verified facts; treat them as reported experiences.
- Do not bypass private communities, login walls, paywalls, or site restrictions to collect data.

## Output Discipline

Use direct evidence before interpretation. When making an inference, label it as `inference`. When confidence is limited by sample size, source bias, missing dates, missing ratings, anonymous sources, or inaccessible comments, say so briefly in the caution notes.

For web reports, keep the design functional and information-dense. The first screen should show the dataset summary, UX filter summary, top complaint clusters, and PRD handoff entry points rather than a marketing-style hero.

For detailed report structure, read `references/report-structure.md`.
