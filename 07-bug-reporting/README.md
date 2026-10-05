# 07 · Bug Reporting

A bug is a difference between **expected** behavior and **actual** behavior.
A good bug report lets a developer reproduce the problem **without asking you a single question**.

## When QA writes one

- A test case fails.
- Exploratory testing finds something unexpected.
- A user or support team reports a problem and QA reproduces it.

If you're not sure it's a bug (the rule is unclear), ask first or file it as a question. That's a requirement gap, not a defect.

## Files in this folder

| File | Use it for |
|---|---|
| [bug-report-template.md](bug-report-template.md) | Template, title formula, checklist before submitting |
| [sample-bug-reports.md](sample-bug-reports.md) | 4 full bug reports (BUG-BOOK-001 to 004) linked to requirements and test cases |

## What the 4 samples show

| Bug | Lesson |
|---|---|
| BUG-BOOK-001 | Boundary bug: exactly 24:00 fails. Show the minute before and after as evidence. |
| BUG-BOOK-002 | Low severity but medium priority. Business context matters. |
| BUG-BOOK-003 | Only one screen and only mobile is wrong. Narrow it down before reporting. |
| BUG-BOOK-004 | Intermittent (2/5). Write the frequency and the conditions that make it happen. |

## Bug life cycle (typical)

New → Triaged → In Progress → Ready for Retest → **Verified / Closed**
or → Reopened (fix didn't work) · Deferred (accepted for later) · Won't Fix · Duplicate

## Common mistakes

- No build number or environment.
- Steps that only work if you saw the tester's screen.
- Expected result based on opinion with no reference.
- Closing a bug without retesting on the build that has the fix.
- Not checking nearby areas after a fix (regression around the fix).
