---
name: create-spec
description: Create implementation-ready spec.md documents from rough project ideas, notes, briefs, design docs, GitHub issues, READMEs, prototypes, existing *.research.md files, or early codebases. Use when turning uncertain greenfield or near-greenfield project context into a decision-dense specification, first identifying open research and decision topics before drafting.
---

# Create Spec

Turn rough source material into a concise, opinionated, implementation-ready `spec.md`.

Use this for greenfield or near-greenfield projects: no production users, no stable public contracts, and little existing behavior that must be preserved unless the user says otherwise.

Act as a spec partner. Infer what is clear, surface what is not, and convert implementation-significant implied behavior into explicit requirements when safe to do so. Treat the spec as an agreement artifact: if two competent implementers could reasonably build different things from the current draft, either tighten the requirement or surface an open question.

## Workflow

1. Inspect source material.
2. Present a decision inventory before creating or editing `spec.md`.
3. Wait for the user to choose: draft, research, or answer decisions.
4. If researching, create or update a relevant `<slug>.research.md` file as lightweight research context.
5. If drafting, create or update one `spec.md`.
6. After drafting from research, include a temporary Research Coverage Check in the response.

Skip the decision inventory only when the user explicitly asks to skip questions/checkpoints and draft immediately.

## Inspect

Review relevant material before responding:

- User prompt and prior conversation context.
- Linked briefs, notes, issues, READMEs, design docs, or prototypes.
- Relevant `*.research.md` files, if present.
- Existing code, if relevant and reasonably scoped.
- `spec-template.md` unless the project provides a better template.

Extract:

- Purpose, users, workflows, goals, non-goals, and project boundary.
- Core domain entities, components, interfaces, integrations, persistence needs, and constraints.
- Decisions that appear settled.
- Behaviors that materially affect implementation, including behaviors that are implied rather than directly stated.
- Risks, ambiguities, and places where multiple reasonable implementations would diverge.

Do not ask the user to restate information that is already present or strongly implied.

When behavior is implied but reasonably clear from the source material, convert it into explicit spec language. When behavior would materially affect implementation but cannot be safely inferred, surface it as an open question or research topic.

## Decision Inventory

Before creating or editing `spec.md`, present:

Use the inventory to distinguish:
- settled decisions,
- implementation-significant behavior you can safely codify now,
- and implementation-significant uncertainty that still needs a decision or research.

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

## Research Documents

Use `<slug>.research.md` files when the user asks to research, save the decision inventory, document open questions, or preserve research context outside `spec.md`.

Treat research files as context, not as a stateful ledger. Read relevant `*.research.md` files before drafting or rewriting `spec.md`, but do not mutate them merely to mark research as incorporated.

When creating a new research file, name it `<slug>.research.md`, using a short lowercase kebab-case slug for the research area. Use `research-template.md` from the research skill if available. Otherwise create a simple `## Topics` structure with topic entries that capture:
- Question
- Context
- Findings
- Recommendation
- Rationale / Tradeoffs
- Assumptions
- Open Questions
- Sources when relevant

Preserve existing notes and user-written content. Do not reorganize unrelated content unless asked.

## Applying Research

When drafting or updating `spec.md`, inspect relevant `*.research.md` files for recommendations, tradeoffs, and unresolved questions.

For each relevant research topic:
- Infer which recommendations should affect the current spec.
- Infer which findings or recommendations should be mentioned as non-goals, deferred work, or future considerations.
- Ignore background-only research unless it clarifies the spec.
- Carry forward unresolved open questions that still affect implementation.

Do not track whether research has been incorporated into `spec.md`. Do not add `Status: Incorporated`, incorporated notes, lifecycle state, or build tracking fields to research files unless the user explicitly asks for that system.

If research conflicts with existing `spec.md`, call out the conflict before editing unless the user explicitly asked to rewrite the spec using current research.

## Research Coverage Check

After drafting or rewriting `spec.md` using research files, include a temporary coverage check in the response. This check is response output only; do not write it into research files unless the user asks.

Use this structure:

```md
## Research Coverage Check

Covered:
- <Research conclusion reflected in the spec>

Potentially missing:
- <Spec-relevant conclusion that may not be covered>

Deferred / background:
- <Research conclusion that does not need current spec coverage>

Open questions:
- <Unresolved research question that still affects the spec>
```

Keep the coverage check short. It should help the user see how research shaped the spec without creating a new tracking system.

## Drafting Threshold

A useful first `spec.md` can usually be drafted when the main project shape is clear and implementation-significant ambiguity is either resolved, recommended, or explicitly recorded as an open question.

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

## spec.md Requirements

The spec MUST be specific, decision-dense, concise, and normative. It MUST NOT become a build plan unless the user asks for one.

The spec MUST make implementation-significant behavior explicit. It is not enough to summarize goals and architecture if important behavior is only implied. When the source material strongly implies a behavior, the spec SHOULD state it normatively. When multiple reasonable implementations remain possible, the spec MUST either resolve the behavior or record it in `Open Questions`.

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
