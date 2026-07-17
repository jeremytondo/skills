---
name: grill-me
description: Grilling session that develops a shared understanding of a plan by exploring its design branches, dependencies, assumptions, terminology, and edge cases one question at a time. Use when the user wants to work a plan through rigorously, ground it in the existing domain model and codebase, resolve contradictions, and capture the conclusions in a requested handoff artifact.
---

<what-to-do>

Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one-by-one. For each question, provide your recommended answer.

Ask the questions one at a time, waiting for feedback on each question before continuing.

If a question can be answered by exploring the codebase, explore the codebase instead.

Do not modify repository files, tickets, or other external systems during the interview. Keep a conversational decision ledger of accepted terminology, rejected alternatives, unresolved questions, and potential ADR candidates.

When the user ends the session by requesting a document, ticket update, or other handoff, capture the accepted decisions in that requested artifact. Write only the artifact or external update the user requested. Do not also update `.memory/CONTEXT.md`, create ADRs, or modify additional documentation unless the user explicitly requests those changes.

</what-to-do>

<supporting-info>

## Domain awareness

During codebase exploration, also look for existing documentation:

### File structure

Keep the project glossary and ADRs in the top-level `.memory/` directory:

```
/
├── .memory/
│   ├── CONTEXT.md
│   └── adr/
│       ├── 0001-event-sourced-orders.md
│       └── 0002-postgres-for-write-model.md
└── src/
```

Treat `.memory/CONTEXT.md` and existing ADRs as domain evidence during the interview. Their absence does not authorize creating them.

## During the session

### Challenge against the glossary

When the user uses a term that conflicts with the existing language in `.memory/CONTEXT.md`, call it out immediately. "Your glossary defines 'cancellation' as X, but you seem to mean Y — which is it?"

### Sharpen fuzzy language

When the user uses vague or overloaded terms, propose a precise canonical term. "You're saying 'account' — do you mean the Customer or the User? Those are different things."

### Discuss concrete scenarios

When domain relationships are being discussed, stress-test them with specific scenarios. Invent scenarios that probe edge cases and force the user to be precise about the boundaries between concepts.

### Cross-reference with code

When the user states how something works, check whether the code agrees. If you find a contradiction, surface it: "Your code cancels entire Orders, but you just said partial cancellation is possible — which is right?"

### Track glossary implications

When a term is resolved, record it in the conversational decision ledger and use it consistently for the rest of the interview. Include it in the requested handoff when relevant.

`.memory/CONTEXT.md` should be totally devoid of implementation details. Do not treat it as a spec, a scratch pad, or a repository for implementation decisions. It is a glossary and nothing else.

Only update `.memory/CONTEXT.md` when the user explicitly asks. If asked, use the format in [CONTEXT-FORMAT.md](./CONTEXT-FORMAT.md) and include only stable glossary terms.

### Track ADR candidates sparingly

Treat a decision as a potential ADR only when all three are true:

1. **Hard to reverse** — the cost of changing your mind later is meaningful
2. **Surprising without context** — a future reader will wonder "why did they do it this way?"
3. **The result of a real trade-off** — there were genuine alternatives and you picked one for specific reasons

If any of the three is missing, skip the ADR. Otherwise, note it as a candidate in the decision ledger or requested handoff. Create an ADR only when the user explicitly asks; when asked, use the format in [ADR-FORMAT.md](./ADR-FORMAT.md).

</supporting-info>
