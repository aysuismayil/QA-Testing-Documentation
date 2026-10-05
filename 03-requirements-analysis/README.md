# 03 · Requirements Analysis

Requirements review is where QA finds problems **before any code is written**. This is the Shift-Left part of testing: a question in refinement costs one message, the same problem found after release costs a bug report, a fix, a retest and sometimes an unhappy customer.

## When QA does it

- When a user story is added to the backlog or comes up in refinement / grooming.
- When a design (mockup) is shared.
- Before writing test cases. Unclear requirements = unclear expected results.

## What you get out of it

- A list of **clarification questions** (with answers written back into the ticket).
- **Testable acceptance criteria** with IDs you can trace later.
- Early ideas for **boundary, negative and edge-case** tests.
- A first idea of **where the risk is**.

## Files in this folder

| File | Use it for |
|---|---|
| [requirements-review-checklist.md](requirements-review-checklist.md) | A checklist to review any story in 10–15 minutes |
| [acceptance-criteria-review-example.md](acceptance-criteria-review-example.md) | A full example: vague story → questions → revised requirements (REQ-BOOK-001 to 007) |

## Quick example

| Original AC | Problem | Testable version |
|---|---|---|
| "Customer can cancel for free up to 24 hours before." | Is exactly 24:00 free? What happens after? | "Cancel is free at 24h 00m or more before start. Under 24h, a 50% fee is shown before the user confirms." |

## Common mistakes

- Waiting for the build to ask questions.
- Writing "looks good" on a story that has no error cases.
- Keeping the answers in your notes instead of in the ticket.
- Mixing up a **requirement gap** (missing rule) with a **bug** (rule exists, app breaks it).
