---
name: create-spec
description: Create implementation-ready docs/spec.md specifications from rough project ideas, notes, briefs, design docs, GitHub issues, READMEs, prototypes, docs/research.md, or early codebases. Use when turning uncertain greenfield or near-greenfield project context into a decision-dense specification, first identifying open research and decision topics before drafting.
---

# Create Spec

Turn rough source material into a concise, opinionated, implementation-ready `docs/spec.md`.

Use this for greenfield or near-greenfield projects: no production users, no stable public contracts, and little existing behavior that must be preserved unless the user says otherwise.

Act as a spec partner. Infer what is clear, surface what is not, and convert implementation-significant implied behavior into explicit requirements when safe to do so. Treat the spec as an agreement artifact: if two competent implementers could reasonably build different things from the current draft, either tighten the requirement or surface an open question.

## Workflow

Use the git root as the project root when available; otherwise use the current working directory.

1. Inspect source material.
2. Present a decision inventory before creating or editing `docs/spec.md`.
3. Wait for the user to choose: draft, research, or answer decisions.
4. If researching, stay in research/decision mode until the direction is clear enough to draft.
5. If saving research, update only `docs/research.md`.
6. If drafting, create or update the top-level `docs/spec.md`, creating `docs/` if needed.

Skip the decision inventory only when the user explicitly asks to skip questions/checkpoints and draft immediately.

## Inspect

Review relevant material before responding:

- User prompt and prior conversation context.
- Linked briefs, notes, issues, READMEs, design docs, or prototypes.
- The top-level `docs/research.md`, if present.
- An existing `docs/spec.md`, if present.
- Existing code, if relevant and reasonably scoped.
- `spec-template.md` unless the project provides a better template.

Extract:

- Purpose, users, workflows, goals, non-goals, and project boundary.
- Core domain entities, components, interfaces, integrations, persistence needs, and constraints.
- Decisions that appear settled.
- Implementation-significant behavior, including behavior implied rather than directly stated.
- Risks, ambiguities, and places where multiple reasonable implementations would diverge.

Do not ask the user to restate information that is already present or strongly implied.

When implementation-significant behavior cannot be safely inferred, surface it as an open question or research topic.

## Decision Inventory

Before creating or editing `docs/spec.md`, present:

Use the inventory to distinguish:
- settled decisions,
- behavior you can safely codify now,
- uncertainty that still needs a decision or research,
- and assumptions you would make if drafting now.

```md
## What I Understand

- <Concrete fact or strong inference>

## Decisions Already Made

- <Decision> (Source: User-provided | Strongly implied | Agent-recommended default)

## Open Questions

- <Question> - <Blocking | Spec-shaping | Deferrable>
  - Why it matters: <brief reason, when useful>
  - Recommendation: <recommended default, when useful>

## Assumptions If Drafted Now

- <Assumption> (Consequence if wrong: <brief impact>)

I <do/do not> have enough information to draft a useful first `docs/spec.md`.
```

Blocking levels:

- `Blocking`: must be answered before a useful spec.
- `Spec-shaping`: draftable, but answer may significantly change the spec.
- `Deferrable`: safe to capture as an open question.

If enough information exists, offer to draft with assumptions and open questions. If not, say what research or decisions are needed first.

## Research

Use the top-level `docs/research.md` as the only persistent research artifact.

Read relevant `docs/research.md` content before drafting or rewriting `docs/spec.md`. Apply recommendations, tradeoffs, and unresolved questions that affect the spec; ignore background-only research unless it clarifies implementation behavior.

Only create or update `docs/research.md` when the user explicitly asks to save, summarize, document, write down, or add the research. Follow the research skill's simple dated section shape. Preserve useful existing notes; update an existing section when the new research clearly belongs there, otherwise append a new section.

Do not track whether research has been incorporated into `docs/spec.md`. Do not add status fields, lifecycle state, or build tracking fields to research files unless the user explicitly asks for that system.

If research conflicts with an existing spec, call out the conflict before editing unless the user explicitly asked to rewrite the spec using current research.

## Drafting Threshold

A useful first `docs/spec.md` can usually be drafted when the main project shape is clear and implementation-significant ambiguity is either resolved, recommended, or explicitly recorded as an open question.

This usually means these are clear, recommended, or intentionally left open:

- Purpose, boundary, goals, and non-goals.
- Main components and core domain entities, or a decision to omit them.
- Implementation profile.
- Important integrations and persistence needs.
- Acceptance criteria and verification expectations.

Do not wait for every small detail. Capture non-blocking unknowns in `Open Questions`.

Do not leave behavior implicit when it would materially change implementation. Either:
- turn it into an explicit requirement, or
- record it as an open question.

## docs/spec.md Requirements

The spec MUST be specific, decision-dense, concise, and normative. It MUST NOT become a build plan unless the user asks for one.

The spec MUST make implementation-significant behavior explicit. When the source material strongly implies behavior, state it normatively. When multiple reasonable implementations remain possible, resolve the behavior or record it in `Open Questions`.

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

Before returning a spec, verify that:

- Purpose, boundary, goals, non-goals, technology choices, components, domain names, responsibilities, acceptance criteria, verification, and definition of done are clear and consistent.
- Implementation-significant behavior is explicit enough that two competent implementers would be unlikely to build materially different versions.
- Remaining ambiguity is captured as open questions rather than left implicit.

When returning a draft, briefly summarize major assumptions, important open questions, and intentionally omitted sections outside the spec.
