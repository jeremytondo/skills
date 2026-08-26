---
name: implement
description: Implement a Linear issue from a URL or issue ID — picks a foundation or standard track, then runs it through coding, review, pull-request creation, an implementation summary on the issue, and moving the ticket to In Review.
disable-model-invocation: true
argument-hint: "[linear-url-or-id] [foundation|standard]"
---

# Implement a Linear Issue

Implement $ARGUMENTS.

The process is the same either way; the **track** decides who writes the code and how hard it gets reviewed.

## Step 1 — Pick the track

If the arguments already name a track, use it. Otherwise launch one `Explore` subagent to read the issue and the relevant parts of the codebase and return a track plus a short rationale:

> Read this Linear issue and the code it touches. Decide whether the work is **foundation** or **standard**, and explain why in two or three sentences.
>
> **Foundation** — any of these are true: there is no existing pattern in the codebase to follow and this work establishes one; future work will build on top of it; it is complex or cross-cutting; it is expensive to unwind (schema, API surface, auth, data migration). When it is a genuine toss-up, choose foundation.
>
> **Standard** — the work follows patterns that already exist in the codebase, is contained to a few well-understood areas, and a mistake is cheap to fix.

Tell the user the track and the one-line reason, then keep going without waiting for a reply.

## Step 2 — Implement

1. Set the issue status to In Progress.
2. Review the issue. If the architecture and technical design are ready, continue. If not, define them.
3. Create an implementation plan.
4. **Write the code.**
   - *Foundation*: do the coding yourself, at your current model and reasoning level.
   - *Standard*: shell out to Codex to do the coding work.
5. **Review the code.**
   - *Foundation*: run two adversarial Codex reviews in parallel — one for correctness, one for simplicity. Decide which feedback is worth acting on, make those changes yourself, then do one final full review of your own and make any changes you see fit.
   - *Standard*: fully review Codex's work yourself. Codex tends to over-engineer and write too much code, so pay close attention to that, and make any changes you see fit.
6. When you are satisfied with the code, create a pull request.
7. Use the `pr-watch` skill on the new pull request. Wait until it completes or reaches its bound. Do not restart it automatically after a bounded stop.
8. Comment on the Linear issue with a summary of the implementation, including any key decisions made along the way.
9. Set the ticket status to In Review.

Use this configuration for every Codex run, coding or review:

```text
codex exec --model gpt-5.6-sol --config 'model_reasoning_effort="high"'
```

## Implementations with multiple PRs

Prefer a single PR. When the issue calls for more than one, or you determine more than one is needed, create a sub-issue per PR and run Step 2 for each on the same track. Once every PR exists, have a subagent (your current model and reasoning level) review the whole set together, and make any changes you agree with. Include the order and process for merging the PRs in the final Linear comment.

