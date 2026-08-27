---
name: create-spec
description: Turn a completed grilling session for a Linear brief into an implementation-ready specification by replacing the brief on the same ticket. Use after the grill has reached confirmed shared understanding.
---

# Create Spec

Turn a completed grilling session into a concise, implementation-ready specification on the same Linear ticket. This is a synthesis step: do not interview the user or reopen settled decisions.

Read `spec-template.md` before writing. Use only the sections that help define the work.

## Preconditions

- The Linear issue is identified in the request or current conversation.
- The issue is labeled `brief`.
- The grill for that issue is complete and the user has confirmed shared understanding.

If the target issue is missing, ask only for the issue identifier. If the issue is not a brief or the grill is not complete, explain what is missing and stop without modifying Linear.

## Process

1. Retrieve the Linear brief and read the completed grilling conversation.
2. Reuse repository understanding established during the grill. If needed, inspect narrowly relevant code, domain glossaries, tests, and ADRs to verify facts. Use the project's existing vocabulary and architectural constraints throughout the spec.
3. Synthesize the brief and grill conclusions into one complete specification using the template.
4. Check that the specification contains no silent implementation-significant ambiguity. If the sources contain a genuine contradiction or blocking decision, stop and identify it rather than inventing an answer. Keep only safely deferrable questions in `Open Questions`.
5. Replace the Linear issue description with the specification. Preserve the issue title, comments, project, status, and other unrelated fields. Add the `spec` label and remove the `brief` label.
6. Return the ticket identifier and link.

Do not create a new issue, create `docs/spec.md`, produce a decision inventory, begin a research workflow, or turn the spec into phases, milestones, or implementation tasks.

## Writing

Treat the brief as the starting shape and the grill as the source of resolved design decisions:

- Turn the brief's idea into the problem and agreed solution.
- Turn its scope into user stories, behavioral requirements, and acceptance criteria.
- Turn its direction and the grill's conclusions into implementation decisions.
- Expand system shape into responsibilities, boundaries, interfaces, state, and data contracts when relevant.
- Turn deferred ideas into explicit out-of-scope statements.
- Incorporate confirmed decisions where they apply instead of preserving a detached decision log.

Make implementation-significant behavior explicit. If two competent implementers could reasonably produce materially different behavior, state the contract supported by the resolved decisions. If the difference is unresolved, stop when it blocks implementation; otherwise preserve it as an open question.

- Use simple, direct language and the project's canonical domain terms.
- Use `MUST`, `MUST NOT`, and `SHOULD` when a requirement needs normative force.
- Keep user stories broad enough to cover distinct actors, workflows, permissions, and important edge cases, but do not make them exhaustive for their own sake.
- Describe observable behavior, validation, failure handling, permissions, and state transitions when they affect implementation.
- Record architectural areas, responsibilities, interfaces, schema changes, API contracts, and technical constraints decided during the grill.
- Do not include specific file paths or ordinary code snippets; they become stale quickly. A short schema, type shape, state machine, reducer, or reference algorithm is acceptable when it captures a confirmed decision more precisely than prose.
- Omit empty, repetitive, speculative, or irrelevant sections.
- Do not invent requirements to make the spec appear complete.

## Testing Decisions

Record how the important behavior will be verified. Prefer an existing test seam to a new one and the highest practical seam that observes the contract, such as a user workflow, public interface, or API boundary rather than private implementation details.

Include relevant existing test precedent, success paths, failure paths, and edge cases. Do not ask for a separate testing-seam confirmation unless the completed grill left a blocking conflict about how the behavior can be verified.

## Final Check

Before updating Linear, verify that:

- The problem, solution, boundaries, and terminology are consistent.
- Every grill conclusion that affects implementation appears in the relevant requirement or decision.
- Acceptance criteria describe independently observable outcomes.
- Testing decisions verify external behavior rather than internal structure.
- Remaining open questions are safe to defer.
- The document is a specification, not a transcript, decision log, or build plan.
