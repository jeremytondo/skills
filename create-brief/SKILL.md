---
name: create-brief
description: Explore a rough project idea, notes, issue, design document, README, codebase context, or prior conversation and produce a concise brief.md using the bundled brief-template.md. Use when the user wants an opinionated briefing conversation before writing a formal SPEC.md or build plan.
---

# Create Brief

Use this skill to turn rough source material and discussion into a concise `brief.md`.

The brief is a sharp synthesis artifact. It should clarify what the idea is, why it matters, what shape it appears to have, and what remains unresolved. It is not a formal spec, build plan, phase plan, milestone list, task breakdown, or spec-authoring guide.

## Required Resource

Read `brief-template.md` before drafting. Use it as the default structure for `brief.md` unless the user explicitly provides a different template.

Treat the template as a menu of allowed sections, not a mandatory checklist. Omit any section that would duplicate another section, require filler, or imply certainty the source material does not support.

## Workflow

1. Analyze the user's source material before asking questions.
2. Inspect referenced files or relevant code when available.
3. Infer what is already reasonably clear: intent, scope, users, key capabilities, system shape, useful vocabulary, implementation direction, non-goals, risks, and missing decisions.
4. Keep a running decision log for confirmed decisions, recommendations, open questions, deferred ideas, and assumptions.
5. Ask one concise question at a time, choosing the unresolved question that would most improve the brief or unblock the next decision.
6. Give an opinionated recommendation when enough context exists.
7. Draft `brief.md` once the purpose, recommended direction, key features, non-goals, likely system shape, and open questions are clear enough for a useful handoff.

Do not wait for every small detail to be resolved.

## Conversation and Decisions

- Do not ask the user to repeat information already present or reasonably implied.
- Do not run a rigid questionnaire.
- Prefer options for discrete decisions.
- Use open-ended questions only when tradeoff exploration is needed.
- Infer low-risk answers and label them as recommendations.
- Ask one question when the ambiguity materially affects the brief or later spec.
- Record ambiguity as an open question when it should not block drafting.
- Label recommended defaults as recommendations until confirmed.
- Distinguish user decisions, confirmed recommendations, unconfirmed recommendations, assumptions, deferred ideas, and open questions.
- When drafting from source material without Q&A, treat source statements as idea definition, assumptions, constraints, or recommended direction, not confirmed decisions.
- Use `Confirmed Decisions` only for decisions explicitly made during the briefing conversation or when the user explicitly asks to preserve decisions from a prior artifact.
- Do not invent major requirements silently.

Useful question format:

```md
Question: <single focused question>

Options:
1. <Option>
2. <Option>
3. <Option>

My recommendation: <recommended answer and brief reason>
```

## Drafting Rules

Keep the brief scannable, decision-dense, and direct.

- Prefer short paragraphs or bullets over long prose.
- Use bullets when a section contains multiple distinct claims, recommendations, capabilities, constraints, or open questions.
- Write the brief as the new source of truth for the idea, not as commentary on the source material.
- Avoid source-referential phrasing such as "the source idea describes," "the notes say," "the original file mentions," or "the user wants" unless provenance itself is important.
- Convert source material into direct project statements: say what the project is, should do, or should avoid.
- **Purpose**: A concise statement of what the project is meant to become and why it should exist. This replaces any separate intent section.
- **Idea Definition**: A factual definition of what the project is and what it needs to do, without interpretation or references back to the source material.
- **Recommended Direction**: Opinionated synthesis of the product and technical direction. Include implementation choices here only when they are central to the idea.
- **Key Features**: The likely capabilities the first useful version needs.
- **Non-Goals / Deferred Ideas**: Scope boundaries and later ideas.
- **System Shape**: Main components or areas and their responsibilities.
- **Core Concepts**: Shared vocabulary and domain terms only. Omit this section if the concepts merely repeat System Shape.
- **Confirmed Decisions**: Only decisions explicitly made during the briefing conversation, or source decisions the user explicitly asks to preserve. Omit this section by default.
- **Open Questions**: Important unresolved questions that should not be silently decided.

Never include a section only to satisfy the template.

- Output one complete `brief.md`.
- Err toward bullets when a section would otherwise become a long paragraph or multiple paragraphs.
- Clearly separate confirmed decisions from open questions.
- Do not write `SPEC.md`, a build plan, phases, milestones, or tasks unless explicitly asked.
