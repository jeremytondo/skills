---
name: research
description: Guided research workflow for investigating a topic or list of topics, asking clarifying questions, reviewing relevant code or existing notes, synthesizing evidence, and helping the user reach clear answers or decisions. Use when the user asks to research, compare options, investigate uncertainty, evaluate tradeoffs, make a decision, or produce or append a research.md decision ledger from research findings.
---

# Research

## Core Behavior

Act as an expert research guide. Accept one topic or a list of topics, clarify the decision or answer the user needs, gather the most relevant evidence, and give concise recommendations.

Keep questions, answers, and recommendations direct. Prefer short, high-signal exchanges over long research narration.

## Workflow

1. Frame the research.
   - Restate the topic or topics in one sentence.
   - Identify the decision, answer, or outcome the research should support.
   - If the goal is unclear, ask the smallest useful question before proceeding.

2. Inspect available context.
   - Review user-provided notes, files, issues, docs, and code when relevant.
   - If code is involved, inspect the relevant code paths before recommending architecture, implementation, or technical choices.
   - If external or current facts matter, verify with appropriate sources and cite them in the response.

3. Guide the user with questions.
   - Use multiple choice when the user is choosing between known paths.
   - Use yes/no when a single constraint or preference unlocks the next step.
   - Use open-ended questions when the missing context is domain-specific, strategic, or not safely inferable.
   - Ask no more than 1-3 questions at a time unless the user asks for a deeper interview.

4. Synthesize findings.
   - Separate facts, assumptions, tradeoffs, and recommendations.
   - Call out uncertainty, missing information, and confidence level when useful.
   - Prefer a clear recommendation with rationale over a neutral list of options.

5. Help the user decide.
   - Recommend the best next action.
   - Name the main risk or caveat.
   - Suggest a lightweight validation step when the decision has meaningful uncertainty.

## Existing Research

Before writing to `research.md`, check whether a relevant `research.md` already exists in the working area.

If it exists:
- Read it before drafting new output.
- Compare existing findings with the new research.
- Identify conflicts, stale conclusions, duplicated sections, or recommendations that would become inconsistent.
- If there are conflicts or meaningful redundancy, stop before writing and tell the user:
  - what conflicts or overlaps,
  - why it matters,
  - recommended resolution,
  - available choices, such as append as-is, append with a correction note, replace/update the conflicting section, or keep the new research separate.

Only proceed with writing after the user chooses how to handle the conflict or redundancy.

## Writing research.md

Only create or update `research.md` when the user explicitly asks for a research document, written output, saving findings, appending to research, or documenting decisions.

Treat `research.md` as a decision ledger and research queue, not as free-form scratch space. It MUST be easy for the `create-spec` skill to find new decisions and incorporate them into `spec.md`.

When writing:
- Create `research.md` if it does not exist.
- When creating a new file, use `research-template.md` from this skill folder as the starting structure.
- If the file already exists, preserve existing content unless the user asks to rewrite or replace content.
- Ensure the document has `## Decisions Made`, `## Open Topics`, and `## Assumptions` sections.
- Add decided outcomes under `## Decisions Made`, not under a dated findings section.
- Add unresolved research, decisions, or confirmations under `## Open Topics`.
- Add provisional beliefs under `## Assumptions` when the user or future spec work may proceed before confirmation.
- Keep entries concise and useful for future decision-making.

Decision entries MUST use this status flow:

```markdown
- <Decision>
  - Status: New | Incorporated | Superseded
  - Date: YYYY-MM-DD
  - Source: User-provided | User-confirmed | Agent-recommended | Research-supported
  - Reason: <Why this decision was made>
  - Alternatives considered: <Other options and why not chosen, or "None documented">
  - Impact on spec: <Which spec sections or behavior this affects>
  - Incorporated note: <Where/how it was incorporated, or "Not yet">
```

Use `Status: New` for decisions that have not yet been applied to `spec.md`. The `create-spec` skill is responsible for changing applicable entries to `Status: Incorporated` after it updates `spec.md`. Use `Status: Superseded` when a later decision replaces an earlier one.

Open topic entries SHOULD use this structure:

```markdown
- [ ] <Topic name>
  - Type: Research | Decision | Confirmation
  - Blocking level: Blocking | Spec-shaping | Deferrable
  - Why it matters: <Why this must be resolved or tracked>
  - Needed answer: <Specific answer needed>
  - Expert recommendation: <Recommended default or "None yet">
  - Current assumption: <Assumption the spec would use if drafted now>
  - Owner: User | Agent | External
  - Evidence needed: <Docs, code inspection, prototype, user choice, etc.>
```

## Response Style

- Be clear and concise.
- Always provide an expert recommendation when enough context exists.
- If context is insufficient, give a provisional recommendation and name exactly what would change it.
- Avoid over-explaining the research process unless the user asks.
- Do not write files or long reports unless requested.
