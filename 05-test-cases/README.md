# 05 · Test Cases

A test case is a check that **anyone on the team can run the same way** and get a clear Pass or Fail.
Good test cases are what make regression possible: the same checks, run again on every release.

## When QA writes them

- After scenarios are reviewed and requirements are clear.
- For high-risk or tricky rules (money, boundaries, permissions) that must be checked exactly.
- For anything that goes into the regression suite.

## Files in this folder

| File | Use it for |
|---|---|
| [test-case-template.md](test-case-template.md) | Full and compact templates + writing rules |
| [sample-test-cases.md](sample-test-cases.md) | 19 test cases for the booking feature (TC-BOOK-001 to 019), linked to requirements and bugs |

## What makes a test case good

- Title explains what is checked and the expected outcome
- Linked to a requirement ID
- Exact test data
- Expected result you can verify (a number, a status, a message)
- Reusable next release without rewriting

## Quick example

> **TC-BOOK-014 · Cancel exactly 24 hours before start → no fee**
> Precondition: booking starts in 24h 00m
> Steps: My Bookings → Cancel → Confirm cancel
> Expected: dialog says "Free cancellation", status Cancelled, fee $0.00

## Common mistakes

- "Verify it works" as the expected result.
- One huge test case that checks ten things.
- Only happy-path cases. The boundaries are where bugs are.
- Writing a case per field/label instead of per user goal.
- Test data that only works today (hard-coded dates).
