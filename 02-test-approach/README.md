# 02 · Testing Approach

A testing approach answers one question: **"How will you test this feature, and why that way?"**
It's the thinking behind the test cases. Interviewers ask it all the time ("How would you test a booking app?") and real teams need it before a release.

## When QA uses it

- After the requirements review, before writing test cases.
- When a feature is risky or new and the team wants to know what QA will cover.
- To explain why some things are tested deeply and some not at all.

## How it's different from a test plan

| Testing approach | Test plan |
|---|---|
| One feature, how you think | One release or project, how the work is organized |
| Risks, test ideas, test types | Scope, schedule, people, environments, entry/exit criteria |
| 1–2 pages | Longer, often needs sign-off |

More detail: [test-plan-vs-test-approach.md](../12-qa-reference/test-plan-vs-test-approach.md)

## Files in this folder

| File | Use it for |
|---|---|
| [testing-approach-template.md](testing-approach-template.md) | Empty template with hints |
| [sample-testing-approach.md](sample-testing-approach.md) | Filled-in example for the Demo Booking App booking feature |

## The thinking in short

1. Why does this feature matter? (business goal)
2. What do I know, what am I assuming? (requirements + questions)
3. Where would a bug hurt most? (risk map)
4. What must work first? (smoke + main happy path)
5. How can it break? (negative, boundary, edge cases, two users, interruptions)
6. What else matters for **this** feature? (only the relevant non-functional checks)
7. What am I **not** testing, and why?

## Common mistakes

- Listing every test type that exists instead of the ones that fit.
- Starting from the UI instead of from the business goal.
- Treating all areas the same. Money and data deserve more time than a label color.
