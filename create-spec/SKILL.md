---
name: create-spec
description: Create implementation-ready spec.md documents from rough project ideas, notes, briefs, design docs, GitHub issues, READMEs, prototypes, existing research.md files, or early codebases. Use when turning uncertain greenfield or near-greenfield project context into a decision-dense specification, first identifying open research and decision topics before drafting.
---

# Create Spec

Turn rough source material into a concise, opinionated, implementation-ready `spec.md`.

Use this for greenfield or near-greenfield projects: no production users, no stable public contracts, and little existing behavior that must be preserved unless the user says otherwise.

Act as a spec partner. Infer what is clear, surface what is not, recommend defaults when appropriate, and treat the spec as an agreement artifact.

## Workflow

1. Inspect source material.
2. Present a decision inventory before creating or editing `spec.md`.
3. Wait for the user to choose: draft, research, or answer decisions.
4. If researching, create or update `research.md`.
5. If drafting, create or update one `spec.md`.
6. If applying research decisions, update `spec.md` and mark incorporated decisions in `research.md`.

Skip the decision inventory only when the user explicitly asks to skip questions/checkpoints and draft immediately.

## Inspect

Review relevant material before responding:

- User prompt and prior conversation context.
- Linked briefs, notes, issues, READMEs, design docs, or prototypes.
- Existing `research.md`, if present.
- Existing code, if relevant and reasonably scoped.
- `spec-template.md` unless the project provides a better template.

Extract purpose, users, workflows, goals, non-goals, boundary, implementation preferences, domain entities, components, integrations, persistence needs, risks, ambiguities, and missing decisions.

Do not ask the user to restate information that is already present or strongly implied.

## Decision Inventory

Before creating or editing `spec.md`, present:

```md
## What I Understand

- <Concrete fact or strong inference>

## Decisions Already Made

- <Decision>
  - Source: User-provided | Strongly implied | Agent-recommended default
  - Why it appears settled: <brief reason>

## Open Questions

- <Question>
  - Type: Blocking | Spec-shaping | Deferrable
  - Why it matters: <brief reason>
  - Needed answer: <specific outcome needed>
  - Expert recommendation: <recommended default or "None yet">

## Assumptions If Drafted Now

- <Assumption>
  - Consequence if wrong: <brief impact>

I <do/do not> have enough information to draft a useful first `spec.md`.
```

Blocking levels:

- `Blocking`: must be answered before a useful spec.
- `Spec-shaping`: draftable, but answer may significantly change the spec.
- `Deferrable`: safe to capture as an open question.

If enough information exists, offer to draft with assumptions and open questions. If not, say what research or decisions are needed first.

## research.md

Use `research.md` only when the user asks to research, save the decision inventory, document open questions, or preserve decisions outside `spec.md`.

When creating a new `research.md`, use `research-template.md` from the research skill if available. Otherwise create `## Decisions Made`, `## Open Topics`, and `## Assumptions`.

Decision format:

```md
- <Decision>
  - Status: New | Incorporated | Superseded
  - Date: YYYY-MM-DD
  - Source: User-provided | User-confirmed | Agent-recommended | Research-supported
  - Reason: <Why this decision was made>
  - Alternatives considered: <Other options and why not chosen, or "None documented">
  - Impact on spec: <Which spec sections or behavior this affects>
  - Incorporated note: <Where/how it was incorporated, or "Not yet">
```

Open topic format:

```md
- [ ] <Topic name>
  - Type: Research | Decision | Confirmation
  - Blocking level: Blocking | Spec-shaping | Deferrable
  - Why it matters: <brief reason>
  - Needed answer: <specific answer needed>
  - Expert recommendation: <recommendation or "None yet">
  - Current assumption: <assumption or "None yet">
  - Owner: User | Agent | External
  - Evidence needed: <Docs, code inspection, prototype, user choice, etc.>
```

Preserve existing notes and user-written content. Do not reorganize unrelated content unless asked.

## Applying Decisions

When drafting or updating `spec.md`, inspect `research.md` for `Status: New` decisions.

For each applicable `Status: New` decision:

- Incorporate it into `spec.md`.
- Change `Status: New` to `Status: Incorporated`.
- Set `Incorporated note` to the affected spec section or a brief explanation.

If a new decision conflicts with existing `spec.md`, call out the conflict before editing unless the user explicitly asked to apply it. If a later decision replaces an older one, mark the older entry `Status: Superseded`.

## Drafting Threshold

A useful first `spec.md` can usually be drafted when these are clear, recommended, or explicitly left open:

- Purpose, boundary, goals, and non-goals.
- Main components and core domain entities, or a decision to omit them.
- Implementation profile.
- Important integrations and persistence needs.
- Acceptance criteria and verification expectations.

Do not wait for every small detail. Capture non-blocking unknowns in `Open Questions`.

## spec.md Requirements

The spec MUST be specific, decision-dense, concise, and normative. It MUST NOT become a build plan unless the user asks for one.

Use the project template when provided. Otherwise use `spec-template.md` and omit irrelevant sections.

Include relevant sections for purpose, problem, goals/non-goals, boundary, Implementation Profile, system overview, domain model, components, interfaces, cross-cutting requirements, acceptance criteria, verification, definition of done, and open questions.

Implementation Profile is normative. Capture language/version, dependencies, storage, testing, target platform, project type, performance goals, constraints, scale/scope, repository layout, dependency policy, and implementation rules.

Use `Reference Algorithms` only when prose is likely to be implemented incorrectly without pseudocode.

## Style

Use RFC 2119 terms: `MUST`, `MUST NOT`, `REQUIRED`, `SHOULD`, `SHOULD NOT`, `RECOMMENDED`, `MAY`, and `OPTIONAL`.

Prefer compact bullets, concrete contracts, explicit boundaries, concrete data models, failure behavior, and specific open questions.

Avoid marketing language, generic filler, implementation phases, milestones, file-by-file task plans, repeated requirements, and abstract architecture that does not map to implementation behavior.

Distinguish user-provided decisions, user-confirmed recommendations, agent-recommended defaults, open questions, assumptions, and deferred decisions.

## Final Checks

Before returning a spec, verify that purpose, boundary, goals, non-goals, technology choices, components, domain names, responsibilities, open questions, acceptance criteria, verification, and definition of done are clear and consistent.

When returning a draft, briefly summarize major assumptions, important open questions, and intentionally omitted sections outside the spec.
