---
name: explore
description: Review and focus an early product or engineering idea through a short, guided discussion before turning it into a brief. Use when the idea needs clarified or expanded on, not an exhaustive grilling session or specification.
---

# Explore

Help the user understand and explain an idea in plain language. Explore only far enough to make a useful brief possible.

## Process

1. Read the supplied context. Inspect relevant code or documents when they can answer an important factual question.
2. Identify the smallest set of topics needed to focus this idea. Share them with the user in a sensible order.
3. Discuss one topic at a time. For each topic:
   - explain what appears to be true;
   - expore industry best practices and review other relvant projects and code. Offer up examples form them when relevant.
   - offer concrete examples or plausible approaches;
   - give a recommendation and its reasoning;
   - summarize meaningful pros, cons, and tradeoffs; and
   - ask focused questions when the user's input would materially improve the direction.
4. Briefly summarize the outcome before moving to the next topic.
5. End with a concise synthesis suitable as input to a brief.

Adapt the topics to the idea. Common topics include the problem, intended users, desired outcome, core experience, scope, constraints, and possible directions. Do not use these as a fixed questionnaire.

## Boundaries

- Keep the discussion short, practical, and focused on the few choices that shape the idea.
- Prefer plain language and concrete scenarios over implementation detail.
- Do not ask the user for facts available in the supplied context or environment.
- It is fine to preserve multiple options or defer a decision.
- Treat decisions and recommendations as provisional unless the user says otherwise.
- Record important assumptions and open questions instead of forcing closure.
- Do not exhaust every branch, resolve edge cases, create a spec, or turn the session into a grill.
- Do not create or update an artifact unless the user asks.

When useful, recommend `create-brief` as the next step.
