# Review Mining Report Structure

Use this structure for HTML or Markdown review-mining deliverables.

## 1. Header

- Product or app name if known
- Sources: Google Play Store, Naver Cafe, DCInside, App Store, public web, or owned VOC as applicable
- Dataset scope: total collected count, UX-selected count when relevant, date range, ratings range, languages, source mix, and missing-data notes
- Default period note: use the most recent 12 months unless the user specifies another period
- Method note: reviews/posts are evidence from the collected set, not a representative sample of all users

## 2. Source and Filter Summary

- Collection date/time
- Source list with URL/query/location when available
- Access limitations or sampling constraints
- Period filter used
- UX relevance filter used
- Counts by source
- Counts by UX relevance: high / medium / low / non-UX
- Excluded non-UX categories, such as pure price movement, investment result, policy anger without app interaction, spam, or duplicate content

## 3. Executive Summary

- 3-5 bullets on the strongest repeated discomforts/complaints
- 1 bullet on positive or trust-building signals
- 1 bullet on important minority or high-severity signals
- 1 bullet on the biggest uncertainty or data limitation

## 4. Cluster Overview

Create a table with:

- Rank
- Cluster name
- Frequency: high / medium / low
- Severity: high / medium / low
- Review/post count or approximate share when available
- Affected users
- Short summary

Rank clusters by severity first, then frequency, then strategic relevance.

## 5. Cluster Detail Cards

For each cluster include:

- Cluster name
- Summary
- Frequency and severity
- Recurring pattern
- Affected users
- Suspected cause, labeled as inference
- Representative quotes, up to 15, privacy-redacted
- Caution notes

## 6. Positive and Counter-Signals

Summarize praise, successful use cases, or reviews/posts that contradict the main complaint pattern. Explain how these signals should temper the problem definition.

## 7. User-Type Notes

List only evidence-grounded user types or use contexts. Keep each note short:

- user type or context
- supporting review evidence
- related clusters
- confidence: high / medium / low

## 8. Raw Results

Include one dedicated raw-results area. For small datasets, show the full table in the report. For large datasets, show a preview and link or attach a CSV containing all rows.

Required columns:

- raw row id
- source
- source type
- URL or location
- date
- rating
- title or context
- raw text, privacy-redacted
- UX relevance
- assigned cluster
- tags
- inclusion note

Raw results should be minimally transformed. Redact personal/sensitive data, but do not rewrite the user wording for clarity.

## 9. PRD-Ready Summary

Include these exact sections:

- Problem definition candidates: 3 items
- Validation questions
- Solution hypothesis candidates
- Problems to exclude for now
- Additional research questions

Keep this section concise enough to paste into a PRD.

## 10. Appendix

When useful, include:

- cleaned review list
- tag glossary
- excluded/spam duplicate notes
- privacy redaction note
- source-specific caveats, such as community anonymity, missing ratings, missing dates, or inaccessible deleted posts
