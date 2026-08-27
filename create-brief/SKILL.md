---
name: create-brief
description: Turn an explored idea, notes, or prior discussion into a short, plain-language brief and publish it to Linear. Use when the idea is focused enough to capture but not ready for a specification.
---

# Create Brief

Turn the available context into a concise brief. The brief should help someone quickly understand the idea and continue exploring it later.

Read `brief-template.md` before writing. Use only the sections that help explain the idea.

## Process

1. Read the source material and relevant discussion.
2. Identify the idea's clearest current shape: the problem, intended users, desired outcome, recommended direction, likely scope, and important unknowns.
3. Write one complete brief using the template.
4. Publish it to Linear:
   - If the exploration started from a Linear ticket, replace that ticket's description with the brief. Tag it `brief` and remove the `idea` tag if present.
   - Otherwise, create a new Linear ticket using the brief as its description. Tag it `brief`.
5. Return the ticket identifier and link.

## Writing

- Use simple, concise language.
- Prefer short paragraphs and bullets.
- State the idea directly. Do not narrate or refer back to the source material.
- Include concrete examples only when they make the idea easier to understand.
- Give a recommended direction when the context supports one.
- Keep meaningful alternatives, deferred decisions, assumptions, and open questions visible.
- Treat directions and decisions as provisional unless the user explicitly confirmed them.
- Omit sections that would be empty, repetitive, or speculative.
- Do not invent requirements to make the brief look complete.

The brief is a starting point for later exploration or grilling. It is not a spec, implementation plan, roadmap, or task list.
