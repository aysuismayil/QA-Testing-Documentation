# 06 · Checklists

Checklists are short lists of checks you run again and again. They are faster than test cases and great for things that must never be forgotten.

## When QA uses them

| Checklist | When |
|---|---|
| [Smoke](smoke-testing-checklist.md) | Every new build, and right after a production deploy |
| [Regression](regression-checklist.md) | Before every release, after fixes, after big changes |
| [Release](release-checklist.md) | The last days before release and the first days after |

Each file has a **generic part** you can reuse and a **Demo Booking App example** showing it filled in.

## Checklist vs. test case

| Checklist item | Test case |
|---|---|
| "Customer can book one slot" | Exact steps, data and expected result for booking |
| For experienced testers, fast runs | For anyone, repeatable runs |
| Great for smoke and release | Great for detailed and regression testing |

## Common mistakes

- Checklist that grows forever. Remove items that no longer matter.
- Items that are too vague to check ("app works").
- Copying a checklist from another product without changing it.
- Ticking boxes without actually checking. If you skip something, say so.
