# Snap & UX Lint Report Structure

Use this structure for HTML or Markdown deliverables.

## 1. Header

- Product or screen name if known
- Input type: Figma capture, screenshot, HTML screen, final design image, or flow
- Inspection standard: Nielsen 10, or Nielsen 10 + provided product UX guide
- User goal or intended task, as provided by the user or marked as inferred / needs confirmation
- Additional context used: PRD, policy document, product UX guide, business rule, or none provided
- Context intake status: answered, partially answered, skipped by user, or inferred from visible screens
- Method note: this is heuristic UX linting, not real user validation

If context was provided, state how it affected the analysis, for example:

- PRD changed the success criteria
- policy/business rule explains why a step is required
- product UX guide added additional criteria
- target user or success metric changed issue priority

If context was not provided, explicitly say that findings are based only on visible UI and Nielsen heuristics.

## 2. Snapshot

For multi-screen inputs, start with the flow before screen details.

### Flow Snapshot

- flow summary
- screen order, numbered left-to-right by default
- user goal or likely task
- success criteria derived from the stated or inferred user goal
- provided constraints or assumptions that shape the lint
- step-by-step flow map
- expected user action between screens
- visible transition or state feedback
- flow-level risk points

For single-screen inputs, use only the screen snapshot.

### Screen Snapshot

For each screen:

- screen summary
- major UI elements
- user flow step
- visible risk points

For multi-screen flows, include a compact flow map before individual screen snapshots:

- step number
- screen name
- expected user action
- visible transition or state feedback
- risk note

## 3. Flow UX Lint

Create a table with:

- Rank
- Flow issue name
- Flow location: step, transition, or whole flow
- Violated principle
- Severity: high / medium / low
- Priority: high / medium / low
- User impact
- Short suggested fix

Evaluate flow-level issues before screen-level issues. Prioritize task completion, transition clarity, recovery, state feedback, and whether the next action logically follows from the previous screen.

## 4. Screen UX Lint Overview

Create a table with:

- Rank
- Issue name
- Screen location
- Violated principle
- Severity: high / medium / low
- Priority: high / medium / low
- User impact
- Short suggested fix

Rank by priority first, severity second, and flow dependency third.

## 5. Issue Detail Cards

Separate flow-level and screen-level issue cards.

For each flow-level issue include:

- issue name
- flow location
- violated principle
- evidence across the screen sequence
- user impact
- suggested fix at principle level
- severity
- priority
- confidence: high / medium / low
- needs confirmation, if applicable

For each screen-level issue include:

- issue name
- screen location
- violated principle
- evidence from the screen
- user impact
- suggested fix at principle level
- severity
- priority
- confidence: high / medium / low
- needs confirmation, if applicable

## 6. Fix List

Group fixes by:

- fix now: high-priority issues that may block or mislead users
- improve soon: medium-priority issues that reduce clarity or efficiency
- monitor or validate: low-priority, context-dependent, or uncertain issues

Keep fixes principle-level unless the user asks for detailed design changes.

## 7. Quick Improvement Ideas

List small, low-risk improvements that clarify hierarchy, CTA priority, state feedback, or information architecture.

## 8. Additional Validation Questions

List questions that would test whether the heuristic findings are true for users.

## 9. User Testing Confirmation Items

List tasks, observations, or success criteria to confirm in usability testing.

## 10. Pre-Launch Checklist

Include a concise checklist:

- primary CTA is visually and semantically clear
- secondary actions do not compete with the primary task
- system status is visible after user action
- transitions between screens are understandable
- users can recover, go back, cancel, or change choices at reasonable points
- error prevention and recovery are present where needed
- labels match user language
- important information is visible before decision points
- flow transitions are understandable
- accessibility basics are checked

## 11. Annotated UX Snapshot

This must be the final section of every web report when the input includes a screenshot, Figma capture, final design image, or renderable HTML screen.

Purpose:

- Let the user understand the most important issues by looking at one annotated image.
- Point directly to visible problem areas using short polished callout labels and curved arrows by default.
- Use a refined annotation-board style: calm gray labels, thin curved arrows, open V-shaped arrowheads, readable spacing, and no childish handwritten font effects.
- Do not use filled triangle arrowheads for reference-image style annotations.
- Keep callout text outside or around the UI whenever possible so the screenshot remains inspectable.
- Match the user's requested style when provided. If the user provides a reference image with arrows and handwritten notes, follow that structure and do not replace it with numbered pins.

Include:

- the original screen or flow image, centered
- 1-3 highest-priority arrow callouts for a single screen
- 1-2 arrow callouts per screen card for multi-screen flows
- for legend-style numbered snapshots, do not force one issue per screen; place pins where the visible issues actually are
- keep numbered pins visually light and compact: small solid badges with white numbers, placed precisely on the relevant UI point
- use one consistent numbered-pin color by default; do not encode severity with pin color unless explicitly requested and explained
- short issue-specific labels that describe the actual visible problem
- curved leader lines or arrows from each label to the exact UI point
- issue ids or short issue names that map back to the UX Lint tables
- a compact summary below the image for mobile or accessibility
- when the full-flow image is too crowded, one card per important screen instead of one combined annotation image

Do not:

- overcrowd the image
- cover the UI being diagnosed
- put long callout sentences over the screenshot
- use numbered pins when the user asked for reference-image style arrows
- introduce new issues that are not in the report
- annotate non-visible assumptions
- use this visual summary as a replacement for issue detail cards
