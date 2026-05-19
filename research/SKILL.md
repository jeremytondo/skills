---
name: research
description: Guided research workflow for investigating a topic or list of topics, asking clarifying questions, reviewing relevant code or existing notes, synthesizing evidence, and helping the user reach clear answers or decisions. Use when the user asks to research, compare options, investigate uncertainty, evaluate tradeoffs, make a decision, or produce or append a lightweight research.md context document from research findings.
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

Only create or update `research.md` when the user explicitly asks for a research document, written output, saving findings, appending to research, or documenting research conclusions.

Treat `research.md` as readable research context, not as a stateful incorporation ledger. It should capture what was researched, why it mattered, important notes and tradeoffs, the conclusion reached if any, and unresolved questions.

`research.md` owns research context. It does not own spec incorporation, build lifecycle, or implementation tracking state. Do not track whether research has been incorporated into `spec.md`, and do not maintain lifecycle/status fields unless the user explicitly asks for that.

When writing:
- Create `research.md` if it does not exist.
- When creating a new file, use `research-template.md` from this skill folder as the starting structure.
- If the file already exists, preserve existing content unless the user asks to rewrite or replace content.
- Ensure the document has a `## Topics` section.
- For each topic, capture the question, context, notes, conclusion, and open questions.
- Preserve useful research even when the conclusion is not ready for the current spec.
- It is fine for conclusions to say something is future work, deferred, background context, not part of the initial build, or still unresolved.
- Keep entries concise and useful for future decision-making.
- Avoid heavy decision-database fields such as status, owner, incorporated notes, impact mappings, or lifecycle state unless the user requests them.

Topic entries SHOULD use this structure:

```markdown
### <Topic Name>

Question:
<What were we trying to answer?>

Context:
<Why this came up / what project decision it affects.>

Notes:
- <Important finding>
- <Important tradeoff>
- <Useful source, code observation, or reasoning>

Conclusion:
<The conclusion reached, if any. Say naturally whether this affects v1, should be deferred, is background context, or is not ready for the spec.>

Open Questions:
- <Question still unresolved>
```

## Response Style

- Be clear and concise.
- Always provide an expert recommendation when enough context exists.
- If context is insufficient, give a provisional recommendation and name exactly what would change it.
- Avoid over-explaining the research process unless the user asks.
- Do not write files or long reports unless requested.
