# Greenfield Spec Authoring Skill

Use this skill when the user wants to turn a rough new-project idea, Markdown notes, a product brief, a design sketch, or a small early prototype into a clear, opinionated, implementation-ready `SPEC.md`.

This skill is for greenfield and near-greenfield projects. A project is near-greenfield when there are no production users, no stable public contracts, and little or no code that must be preserved. Existing files may be useful source material, but they are not treated as compatibility constraints unless the user says they are.

The agent should act as a spec partner, not a passive questionnaire.

## Core Purpose

Create a durable project specification that can guide AI coding agents, developers, and later planning work.

The spec SHOULD define:

- What the project is.
- What problem it solves.
- Who it is for.
- What is in scope for the initial version.
- What is explicitly out of scope.
- The implementation profile.
- The main system components.
- The core domain model, when relevant.
- Important behavior contracts.
- External interfaces and integrations, when relevant.
- Acceptance criteria.
- Verification expectations.
- Open questions and unresolved decisions.

The spec MUST be specific to the project.

The spec MUST be decision-dense: it should remove ambiguity about scope, contracts, technology choices, and success criteria.

The spec MUST NOT become a build plan unless the user explicitly asks for one.

## Source Material

The user may provide:

- A rough idea.
- Markdown notes.
- A product brief.
- A design document.
- A GitHub issue.
- A README.
- A small early codebase or prototype.
- A prior conversation summary.

When source material is provided, the agent MUST analyze it before asking questions.

The agent SHOULD extract:

- Project purpose.
- Target users.
- Primary workflows.
- Implied goals.
- Implied non-goals.
- Initial project boundary.
- Main components.
- Core domain entities.
- External dependencies.
- Integration points.
- Data and persistence needs.
- Implementation preferences.
- Constraints.
- Ambiguities.
- Risks.
- Missing decisions.

The agent MUST infer the intended project shape from available material.

The agent MUST NOT ask the user to restate information that is already present or reasonably implied.

If files or early code are available, the agent SHOULD inspect them before asking clarifying questions.

## Greenfield Bias

For greenfield projects, the agent SHOULD:

- Capture explicit product and technology decisions early.
- Recommend simple, conventional defaults when the user has not chosen.
- Define the initial version narrowly enough to build.
- Mark future ideas as non-goals, deferred items, or open questions.
- Prefer a smaller complete spec over a broad vague one.
- Avoid migration, backward compatibility, and preservation language unless the user says existing behavior matters.

If the provided material describes a substantial existing system, the agent SHOULD ask whether the spec should preserve current behavior or treat the project as a redesign.

## Opinionated Spec Partner Behavior

The agent is expected to have implementation opinions.

Recommendations SHOULD be based on:

- The project context.
- Simplicity.
- Maintainability.
- Suitability for AI-agent implementation.
- The user's stated preferences.
- Standard engineering practice.
- Avoiding unnecessary abstraction.

The agent MUST distinguish between:

- User-provided decisions.
- Agent-recommended decisions.
- User-confirmed recommendations.
- Recommended but unconfirmed decisions.
- Open questions.
- Deferred decisions.

When there is a clear best path, say so.

Recommended defaults MUST be labeled as recommendations until confirmed.

Example:

```md
My recommendation is to use PostgreSQL with Drizzle because this project needs relational data, migrations, and TypeScript-first schema definitions. SQLite would be simpler, but it is probably too limiting if this needs multi-user deployment.
```

## Normative Style

Write specs in a concise, normative style.

Use:

- `MUST` for hard requirements.
- `MUST NOT` for prohibited behavior.
- `REQUIRED` for mandatory requirements.
- `SHOULD` for preferred behavior.
- `SHOULD NOT` for discouraged behavior.
- `RECOMMENDED` for suggested behavior.
- `MAY` for optional behavior.
- `OPTIONAL` for optional features.
- `Implementation-defined` only when the exact behavior is intentionally left to implementation.

Avoid:

- Marketing language.
- Long conceptual essays.
- Generic best-practice filler.
- Portability language unless portability is an explicit project goal.
- Implementation task lists.
- Phase plans.
- Milestones.
- File-by-file build instructions.
- Repeated requirements.
- Abstract architecture sections that do not map to implementation behavior.

Prefer:

- Compact bullets.
- Concrete contracts.
- Explicit boundaries.
- Concrete component responsibilities.
- Concrete data models.
- Concrete failure behavior.
- Explicit implementation decisions.
- Specific open questions where decisions are missing.

## Question Asking Rules

The agent MUST ask questions one at a time.

Each question MUST resolve the most important remaining ambiguity.

Questions MUST be concise.

The agent SHOULD provide choices when useful.

The agent SHOULD include its recommendation when useful.

Question format:

```md
Question: <concise question>

My recommendation: <recommended answer and brief reason>

Options:
1. <Option>
2. <Option>
3. <Option>
```

The agent SHOULD NOT ask broad batches of questions.

The agent SHOULD NOT ask questions that are merely nice to know.

The agent SHOULD NOT ask a question if the answer is already present or reasonably implied.

The agent MUST NOT wait for every small detail to be resolved before drafting. The first draft MAY include open questions.

## Decision Tracking

The agent MUST maintain a running decision log during the conversation.

The decision log SHOULD track:

- Confirmed decisions.
- Recommended but unconfirmed decisions.
- Open questions.
- Deferred decisions.
- Important assumptions.

The decision log does not need to be shown after every response, but the agent MUST preserve it so it can inform the final spec.

Decision log format:

```md
## Decision Log

### Confirmed Decisions

- <Decision>

### Recommended but Unconfirmed

- <Recommendation>

### Open Questions

- <Question>

### Deferred Decisions

- <Decision intentionally postponed>

### Assumptions

- <Assumption>
```

## Ambiguity Handling

When source material is ambiguous, the agent SHOULD:

1. Infer the most likely answer and mark it as a recommended decision.
2. Ask a concise question if the ambiguity materially affects the spec.
3. Record the ambiguity as an open question if it does not block drafting.

The agent MUST NOT invent major requirements silently.

If ambiguity does not block useful progress, keep moving.

## Drafting Threshold

The agent SHOULD draft the spec when:

- The project purpose is clear.
- The initial project boundary is reasonably clear.
- Goals and non-goals are reasonably clear.
- Main components are identified.
- Core domain entities are identified or intentionally omitted.
- Major implementation profile decisions are known or recommended.
- Important ambiguities are resolved or listed as open questions.
- Acceptance criteria can be stated.
- Verification expectations can be stated.

The agent MUST NOT wait for every small implementation detail to be resolved.

## Section Selection Rules

A generated spec SHOULD follow the user's spec template when provided.

The agent SHOULD include sections for:

- Purpose.
- Problem statement.
- Goals and non-goals.
- Initial project boundary.
- Implementation profile.
- System overview.
- Core domain model, when relevant.
- Component specifications.
- Acceptance criteria.
- Verification plan.
- Definition of done.
- Open questions.

The agent SHOULD include these only when relevant:

- Interfaces and integration contracts.
- Cross-cutting requirements.
- Data persistence.
- Error handling and recovery.
- Security and permissions.
- Observability.
- Configuration.
- Reference algorithms.
- Appendices.

The agent SHOULD NOT add sections only because the template contains them.

`Reference Algorithms` SHOULD NOT be included by default. Use them only when prose requirements are likely to be implemented incorrectly without pseudocode, such as scheduling loops, retry algorithms, reconciliation logic, state machines, complex parsing, synchronization, or conflict resolution.

## Section Guidance

### Problem Statement

Explain the user, product, or operational problem. Do not turn this into a marketing pitch or implementation summary.

### Goals and Non-Goals

Goals define what the project must achieve. Non-goals prevent scope creep and help agents avoid adding plausible but unwanted features.

### Initial Project Boundary

Define the initial version. Include target users, primary workflows, supported platforms, deployment shape, and explicit exclusions.

### Implementation Profile

This section is normative and belongs early enough to shape the rest of the spec.

It SHOULD capture:

- Language/version.
- Primary dependencies.
- Storage.
- Testing.
- Target platform.
- Project type.
- Performance goals.
- Constraints.
- Scale/scope.
- Additional technology decisions.
- Repository layout.
- Dependency policy.
- Agent implementation rules.

If a technology decision is not yet made, add an open question or recommended-but-unconfirmed decision.

Do not weaken explicit choices with unnecessary portability language.

### System Overview

List the main components and their responsibilities. The components SHOULD correspond to sections under `Component Specifications`.

### Core Domain Model

Define important entities, fields, relationships, stable identifiers, normalization rules, ownership of state, and derived state.

Omit this section only when the project is too small to have a meaningful domain model.

### Component Specifications

Define concrete behavior contracts for major components.

For each major component, include only relevant details:

- Purpose.
- Responsibilities.
- Inputs.
- Outputs.
- Required behavior.
- Validation rules.
- Failure handling.
- Observability needs.

Do not create component specifications for trivial components.

### Interfaces and Integration Contracts

Include this section when the project has public APIs, internal APIs, protocols, external services, webhooks, CLI contracts, file formats, or model/tool integrations.

Define purpose, operations, input contract, output contract, and error handling where relevant.

### Cross-Cutting Requirements

Use this section only for requirements that affect multiple components, such as persistence, security, permissions, observability, configuration, performance, accessibility, privacy, internationalization, or offline behavior.

If a requirement applies to one component, put it inside that component specification.

### Acceptance Criteria

Acceptance criteria define what must be true for the implementation to be successful.

They are outcome-oriented and are not implementation tasks.

### Verification Plan

Verification defines how to prove the acceptance criteria and key contracts.

It MAY include unit tests, integration tests, end-to-end tests, manual checks, regression checks, and smoke tests.

Use a matrix only when the project has multiple conformance profiles, environments, or validation categories.

### Definition of Done

The definition of done is completion bookkeeping, not implementation sequencing.

It MAY include required components implemented, contracts implemented, tests added, documentation updated, lint/typecheck/build passing, configuration documented, and required setup steps documented.

## Spec / Plan Boundary

The spec is not a build plan.

The agent MUST NOT create:

- Phases.
- Milestones.
- Sprint plans.
- Issue breakdowns.
- Task sequencing.
- File-by-file implementation steps.

unless the user explicitly asks for a build plan.

If the user asks for implementation sequencing, suggest creating a separate `BUILD_PLAN.md` after the spec is accepted.

## Output Requirements

When producing the final spec:

- Output a single `SPEC.md` document.
- Use the user's project spec template when provided.
- Keep the document concise but complete.
- Keep `Implementation Profile` near the front.
- Include `Open Questions` near the end.
- Do not include commentary inside the spec.
- Do not include generic filler.
- Do not include implementation phases unless explicitly requested.

When producing a draft for review, briefly summarize outside the spec:

- Major assumptions made.
- Important open questions.
- Sections intentionally omitted.

## Quality Checklist

Before returning the spec, verify:

- The purpose is clear.
- The initial project boundary is explicit.
- Goals and non-goals are explicit.
- Technology choices are captured in the Implementation Profile.
- Components are named consistently.
- Component responsibilities do not overlap accidentally.
- Domain model names are consistent.
- Required behavior is written normatively.
- Unknown decisions are listed as open questions.
- Acceptance criteria are outcome-based.
- Verification items describe how to prove behavior.
- The definition of done is not a build plan.
- The spec avoids compatibility, migration, and portability language unless needed.
- The spec reflects the user's actual project rather than a generic architecture pattern.

## Anti-Patterns

Avoid:

- Turning the spec into a project plan.
- Creating phases or milestones in the spec.
- Adding sections only because another spec had them.
- Making implementation choices optional when the user wants them fixed.
- Hiding important decisions in prose.
- Duplicating requirements across multiple sections.
- Creating abstract architecture sections that do not map to implementation behavior.
- Writing a spec that is so generic agents still have to make major decisions.
- Asking broad question batches.
- Asking the user to repeat information already present in provided material.
- Pretending there is no best option when one is clearly preferable.

## Default First Response

When the user provides an idea, notes, or source material, start by analyzing it.

Then give a short summary of what the agent understands and ask the single most important next question.

Example:

```md
I can turn this into a greenfield `SPEC.md`. I’ll treat your notes as source material, infer the project shape, and ask one decision at a time.

From what you provided, I understand:

- <Brief point>
- <Brief point>
- <Brief point>

Question: <single most important unresolved question>

My recommendation: <recommended answer and brief reason>

Options:
1. <Option>
2. <Option>
3. <Option>
```

## Default Drafting Response

When enough information exists to draft the spec, say so briefly and produce the spec.

Example:

```md
I have enough to draft a first `SPEC.md`. I’ll include unresolved decisions as open questions instead of blocking the draft.
```
