---
name: create-brief
description: Explore a rough project idea, notes, issue, design document, README, codebase context, or prior conversation and produce a concise BRIEF.md using the bundled brief-template.md. Use when the user wants an opinionated briefing conversation before writing a formal SPEC.md or build plan.
---

# Create Brief

Use this skill to turn rough source material and discussion into a concise `BRIEF.md`.

The brief is a handoff artifact for a later `SPEC.md`. It is not a formal spec, build plan, phase plan, milestone list, or task breakdown.

## Required Resource

Read `brief-template.md` before drafting. Use it as the required structure for `BRIEF.md` unless the user explicitly provides a different template.

## Workflow

1. Analyze the user's source material before asking questions.
2. Inspect referenced files or relevant code when available.
3. Infer what is already reasonably clear: intent, scope, users, features, system shape, core concepts, implementation direction, tradeoffs, non-goals, risks, and missing decisions.
4. Keep a running decision log for confirmed decisions, recommendations, open questions, deferred ideas, and assumptions.
5. Ask one concise question at a time, choosing the unresolved question that would most improve the brief or unblock the next decision.
6. Give an opinionated recommendation when enough context exists.
7. Draft `BRIEF.md` once the project shape is clear enough; put remaining ambiguity in `Open Questions`.

## Conversation Rules

- Do not ask the user to repeat information already present or reasonably implied.
- Do not run a rigid questionnaire.
- Prefer options for discrete decisions.
- Use open-ended questions only when tradeoff exploration is needed.
- Label recommended defaults as recommendations until confirmed.
- Distinguish user decisions, confirmed recommendations, unconfirmed recommendations, assumptions, deferred ideas, and open questions.

Useful question format:

```md
Question: <single focused question>

Options:
1. <Option>
2. <Option>
3. <Option>

My recommendation: <recommended answer and brief reason>
```

## Decision Handling

When something is ambiguous:

- Infer the likely answer and mark it as a recommendation when the risk is low.
- Ask one question when the ambiguity materially affects the brief or later spec.
- Record it as an open question when it should not block drafting.

Do not invent major requirements silently.

## Drafting Threshold

Draft the brief when the project intent, recommended direction, key features, non-goals, likely system shape, implementation direction, and important tradeoffs are clear enough to make a useful handoff.

Do not wait for every small detail to be resolved.

## Output Rules

When producing the brief:

- Output one complete `BRIEF.md`.
- Use `brief-template.md`.
- Keep it concise and decision-dense.
- Include decisions made during the conversation.
- Clearly separate confirmed decisions from open questions.
- Include notes that will help a later spec-writing agent.
- Do not write `SPEC.md`, a build plan, phases, milestones, or tasks unless explicitly asked.

## Anti-Patterns

Avoid broad question batches, generic best-practice filler, unnecessary neutrality, detailed task lists, implementation phases, and preserving ambiguity where a clear recommendation would help.
