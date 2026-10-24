---
name: dz-interview
description: Skill describing how to interview the user with quick, proper questions. Use when a request is ambiguous, a decision is missing, or before planning and implementing a feature.
---

# dz-interview

Interview replaces assumptions with decisions. Ask few questions, ask them once, ask them short.

## When to use

Use before planning and implementation, when:

- the request is ambiguous or has missing details,
- two or more valid solutions exist,
- the change is medium or large (GLOSSARY in dz-skills),
- a wrong assumption would cost real work to undo.

Do not interview about facts you can read in code, docs or config.

## Instructions

1. Read first. Search the codebase, docs and config before asking.
2. List unknowns. Note what blocks the task: goal, scope, constraints, tech, data, UX, edge cases.
3. Rank by impact. Ask what changes the most work first. If an answer depends on an earlier one, ask sequentially; otherwise batch.
4. Ask. One decision per question. Give options A/B and a recommended default. Keep each to one or two lines.
5. Record. Note each decision as it is made.

## Question rules

1. One decision per question. Split "where and how" into two.
2. Concrete options beat open text. "A) local file, B) SQLite, C) Postgres. Recommend B." Free text always allowed.
3. Mark the default. If the user says "whatever", that is an answer - take the recommendation.
4. Short. No preamble, no ceremony, no restating the task. See Communication in dz-skills.
5. Reason only when non-obvious. One clause: why the decision matters.
6. Never assume. If the user did not state X, ask or leave X out. NARUTO.
7. Never ask twice. Do not confirm what was answered, do not re-ask to be polite.
8. Never interrogate. No question walls. Ask only what the task needs.

## Sizing

Question count follows feature size (GLOSSARY in dz-skills):

- Small - 0-2 questions, only if truly blocking.
- Medium - 2-4 questions, batch independent ones.
- Big - ask in rounds, one topic per round, record decisions between rounds.

## Example

Bad:

> Hi! I'd be happy to help you build this. Before I start, could you tell me a bit more about how you envision the storage layer, authentication, deployment target, and UI framework? Also, what are your long-term goals?

Good:

> Storage: A) local JSON, B) SQLite, C) Postgres. Recommend B since this fits your usecase.
> Auth needed for v1? A) none, B) single user. Recommend A.

## Flow with other skills

Interview is step 2 of dz-new-feature. Plan determines scope, interview resolves the decisions, read gathers facts, implement follows the recorded decisions.

**CRITICAL:** If the user answers with a new request, do not assume - fold it into the interview or restart it. Never implement on top of an unanswered decision.
