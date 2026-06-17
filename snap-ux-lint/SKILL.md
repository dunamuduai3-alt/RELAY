---
name: snap-ux-lint
description: Inspect Figma captures, app/web screenshots, HTML screens, final design images, or multi-screen flows for UX issues. Use when Codex needs to create a web-readable Flow Snapshot, flow-level UX Lint, Screen UX Lint Report, fix list, and final annotated UX snapshot. Before analysis, ask for the flow's user goal and whether PRD, policy, product UX guide, business rules, or other context exists; use those answers to guide the lint. Use Nielsen's 10 usability heuristics and provided product context. Focus on usability, information architecture, system status, CTA priority, and visual hierarchy without claiming real user validation.
---

# Snap & UX Lint

## Purpose

Inspect final design screens and screenshots for UX risks before validation or implementation. Treat this as heuristic linting, not as proof from real users.

## Inputs

Accept:

- Figma captures
- app or web screenshots
- HTML screens or local web pages
- final design images
- multi-screen user flows
- product UX guide criteria when the user provides them

If the input is a local or running web page, inspect it visually and interactively when possible. If the input is an image, analyze only visible UI and any context the user provides.

For multi-screen flow images, read screens left-to-right by default. Treat the leftmost screen as `Screen 1` unless the user provides numbered labels, arrows, or another explicit order. If screens wrap into multiple rows, read row-by-row from top-left to bottom-right unless the flow arrows indicate otherwise.

## Context Intake

Before running a full lint, start with a short context intake unless the request already answers these points or the user explicitly asks to skip questions.

Ask these two questions together:

1. What is the user's goal or intended task in this flow?
2. Is there any additional context I should use, such as a PRD, policy document, product UX guide, business rule, target user, success metric, or known constraint?

Use the answers as the analysis frame:

- Translate the user goal into the flow success criteria.
- Use provided PRD/policy/UX guide/business rules alongside Nielsen's heuristics.
- Distinguish between visible UX issues and constraints that may be required by policy or business rules.
- Cite the provided context in the report header and method note.
- If no additional context is provided, say `Additional context: none provided` and rely only on visible evidence plus Nielsen's heuristics.

If the user asks for an immediate pass, does not answer, or provides only a screenshot, continue with visible-screen inference. Mark the inferred goal and missing documents as `needs confirmation`. Do not overclaim confidence for findings that depend on unavailable PRD, policy, business rules, or target-user context.

## Standards

Use Nielsen's 10 usability heuristics as the default standard:

1. Visibility of system status
2. Match between system and the real world
3. User control and freedom
4. Consistency and standards
5. Error prevention
6. Recognition rather than recall
7. Flexibility and efficiency of use
8. Aesthetic and minimalist design
9. Help users recognize, diagnose, and recover from errors
10. Help and documentation

When a product UX guide is provided, use it alongside Nielsen's heuristics. Do not invent design-system rules or brand requirements that were not provided.

## Inspection Focus

Prioritize:

- usability
- information architecture
- flow continuity and transition clarity
- system status and feedback
- CTA priority
- visual hierarchy

Consider copy clarity, accessibility, error prevention, and consistency when they directly affect the prioritized axes.

## Workflow

1. Run the context intake first.
   - Ask the two questions in "Context Intake" before producing the final report unless the user already provided the user goal and supporting context.
   - If the user gives a PRD, policy document, product UX guide, business rule, target user, or success metric, extract the UX-relevant constraints before diagnosing issues.
   - Use the stated user goal to judge flow continuity, CTA priority, completion, error recovery, and whether screens support the intended task.
   - If the user asks to proceed without answering, infer from visible evidence and label the inferred flow goal and missing context as `needs confirmation`.

2. Identify the input structure.
   - Decide whether the input is a single screen, multiple unrelated screens, or one connected user flow.
   - For multi-screen inputs, number screens in the observed order. Default order is left-to-right, with the leftmost screen as `Screen 1`.
   - Note unknown transitions or missing intermediate states as `needs confirmation`.

3. Capture the flow snapshot first.
   - Summarize the user goal or likely task.
   - Map each screen to a flow step.
   - List expected user actions between screens.
   - Identify transition/state feedback between steps.
   - Mark flow-level risk points without diagnosing every screen detail yet.

4. Lint the overall flow.
   - Check whether the sequence has a clear start, middle, and end.
   - Check whether each next action is visible and logically follows from the previous screen.
   - Check whether state changes, confirmations, loading, errors, and completion are visible.
   - Check whether users can recover, go back, cancel, or change their choice at reasonable points.
   - Ground each flow issue in visible evidence from the screen order or explicit context.

5. Inspect each screen in detail.
   - For each screen, summarize its purpose, major UI elements, CTA hierarchy, state feedback, and visible risk points.
   - Compare visible issues against Nielsen's heuristics.
   - Add product UX guide criteria only when supplied.
   - Keep screen-level findings separate from flow-level findings.

6. Assign severity and priority.
   - Use `high`, `medium`, or `low` for severity.
   - Prioritize by task blockage, user confusion, risk of error, CTA ambiguity, and recovery burden.
   - For flow issues, prioritize by whether the user can complete the task across screens.
   - Do not inflate severity for aesthetic preference alone.

7. Produce a web report.
   - Create a clean HTML report when a local deliverable is appropriate, or a structured Markdown report when the user only needs chat output.
   - Use `references/report-structure.md` for the expected report layout.
   - Include Flow Snapshot, Flow UX Lint, Screen-by-Screen Snapshot, Screen UX Lint Report, fix list, handoff sections, and a final Annotated UX Snapshot as separate sections.

8. Create the annotated UX snapshot for web reports.
   - Add this as the final major section of the web report.
   - Show the inspected screen or flow image with visible callouts pointing to the exact problem areas.
   - Use reference-image style callouts as the default: center the inspected screen, place short polished annotation labels around it, and connect labels to the exact UI point with curved arrows.
   - Keep the visual style refined and legible. Avoid childish handwritten fonts, oversized strokes, heavy arrows, or labels that make the report look informal or messy.
   - Draw arrows like review markup, not diagram pointers: use soft gray curved strokes with round line caps and open V-shaped arrowheads, not filled triangle arrowheads.
   - Use numbered pins plus a clean legend when the user asks for a tidy legend-style result, when arrow callouts feel messy, or when matching many issues across a multi-screen flow.
   - Do not force exactly one numbered issue per screen. Place multiple pins on the same screen when multiple visible issues matter, and skip screens that do not have a high-priority visual issue.
   - For numbered multi-screen annotations, mark the exact target area with a visible translucent region box, not only a floating number. Put the number as a small solid badge attached to the region's corner.
   - Make target regions explicit enough that the viewer can identify the matched UI area without reading the legend first. Prefer a 1-2px solid outline, subtle translucent fill, and a small number badge.
   - Keep region annotations visually minimal. Avoid decorative white outlines, duplicate borders, heavy shadows, large stickers, or extra rings around the target region.
   - Keep numbered pins visually light and precise: small solid badges, white numbers, subtle border/shadow, and no oversized stickers that obscure the UI.
   - Do not place the number far from the target. The number must be attached to, or immediately adjacent to, the highlighted UI region.
   - Prefer one consistent color for all numbered pins. Do not encode severity with pin color unless the user explicitly asks for color-coded severity and the legend explains the meaning.
   - Do not use numbered pins or a separate legend when the user asks for a visual like an attached reference image. In that case, use arrow callouts unless the user later asks to simplify back to a legend.
   - Keep callout labels short and issue-specific. Write the actual observed problem, such as `위험 행동이 primary CTA처럼 보임`, not generic labels or placeholder wording.
   - Prefer 1-2 arrow callouts per screen card for multi-screen flows. If there are more findings, show only the highest-priority visual findings in the annotated snapshot and keep the rest in tables/cards.
   - Do not add callouts for issues that are not visible in the image.
   - Do not make aesthetic comments unless tied to task clarity, feedback, hierarchy, accessibility, or error prevention.
   - If image editing tools are available, generate a separate annotated PNG and embed it in the web report. If not, build the annotation directly in HTML/CSS/SVG over the screenshot.
   - Ensure annotations remain readable on desktop and mobile. On narrow screens, scale or stack the annotated image and callout labels so text does not overlap the screenshot.
   - For multi-screen flows, switch to per-screen annotated cards when a whole-flow view is crowded: crop or isolate each important screen, show one screen per card, and place 1-2 arrow callouts around that screen.
   - In per-screen cards, do not require a separate legend lookup. Each card should be understandable by itself.

9. End with handoff sections.
   - Prioritized fix list
   - Quick improvement ideas
   - Additional validation questions
   - Items to confirm in user testing
   - Pre-launch checklist
   - Annotated UX Snapshot as the final visual summary

## Flow Issue Fields

Every flow-level issue must include:

- `issue_name`: clear, non-judgmental title
- `flow_location`: transition, step range, or overall flow area
- `violated_principle`: Nielsen heuristic and/or provided UX guide criterion
- `evidence`: what is visible across the screen sequence
- `user_impact`: likely impact on task completion or comprehension
- `suggested_fix`: principle-level recommendation only
- `severity`: high / medium / low
- `priority`: high / medium / low
- `confidence`: high / medium / low

## Issue Fields

Every screen-level lint issue must include:

- `issue_name`: clear, non-judgmental title
- `screen_location`: where the issue appears
- `violated_principle`: Nielsen heuristic and/or provided UX guide criterion
- `evidence`: what is visible or stated in the input
- `user_impact`: likely impact on task completion or comprehension
- `suggested_fix`: principle-level recommendation only
- `severity`: high / medium / low
- `priority`: high / medium / low

Keep suggested fixes at principle level unless the user explicitly asks for detailed copy, layout, or component alternatives.

## Flow Snapshot Fields

For multi-screen flows, include:

- `flow_summary`: what task or user goal the flow appears to support
- `screen_order`: numbered screen list, left-to-right by default
- `flow_steps`: each screen's likely purpose in the sequence
- `expected_user_actions`: what the user likely does to move forward
- `transition_feedback`: what changes between screens, including loading, success, failure, confirmation, or missing state
- `flow_risk_points`: places where the sequence may confuse, block, distract, or mislead users

## Screen Snapshot Fields

Each screen or flow snapshot must include:

- `screen_summary`: what the screen is for
- `major_ui_elements`: visible navigation, forms, controls, content, CTAs, feedback states
- `flow_step`: likely user journey step
- `visible_risk_points`: places that may confuse, block, distract, or mislead users

For multi-screen flows, include the Flow Snapshot and Flow UX Lint before individual screen details.

## Annotated UX Snapshot Fields

Every web report must end with an annotated visual summary when the input includes screenshots, Figma captures, final design images, or renderable HTML screens.

Include:

- `annotation_id`: short id such as A1, A2, A3
- `linked_issue`: matching issue name or issue id from the report
- `screen_reference`: screen name, screen number, or flow step
- `target_area`: concrete visible UI area being pointed to
- `callout_text`: short note displayed on the annotated image
- `reason`: why this visible area is risky
- `severity`: high / medium / low

Annotation style requirements:

- Place the screen or flow image at the center.
- Use numbered region boxes by default for multi-screen flow images, not long text labels on top of the screens.
- Put explanations in a legend/table below or beside the image, using the same number as the region box.
- Put each number on the highlighted problem region itself, avoiding important UI text and controls when possible.
- If a region box would cover important UI text, use a thin outline and low-opacity fill, or place the badge on the closest corner of the region.
- Use leader lines only when a pin needs to sit away from the target.
- Keep the visual snapshot scannable at a glance; the image should not become a wall of text.
- Match the user's requested style when provided. If the user says the text-heavy annotation is unreadable, switch to numbered pins and a legend.
- For multi-screen flows, either annotate the whole flow image or provide one annotated panel per important screen. Do not overcrowd a single image.
- When a whole-flow annotation becomes crowded or hard to read, prefer one annotated card per important screen.
- In per-screen cards, each card should contain the screen image, the issue title, one short problem explanation, severity/priority, and an optional pointer line or small marker.
- The annotated snapshot is a visual index of the most important issues, not a replacement for the issue details.

## Do Not Claim

- Do not claim actual user validation is complete.
- Do not present heuristic findings as proven user behavior.
- Do not make taste-based critique without usability evidence.
- Do not invent product UX guide or design-system rules.
- Do not label every imperfection as a problem.
- Do not overfit to visual style when task clarity, feedback, and hierarchy are more relevant.
- Do not recommend final solutions before the issue and principle are clear.
- Do not inspect screens as isolated static images before checking whether the overall flow works.

## Output Discipline

Use visible evidence first, then state the heuristic interpretation. If a finding depends on missing context, mark it as `needs confirmation`.

For web reports, keep the design functional, scannable, and screen-focused. The first screen should show the inspected flow summary, top flow risks, top screen-level risks, and fix-list entry points.

The final report section must be `Annotated UX Snapshot`. It should let the user understand the highest-priority issues by looking at the image alone.

For detailed report structure, read `references/report-structure.md`.
