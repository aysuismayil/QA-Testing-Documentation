# Requirements Traceability Matrix: Demo Booking App 2.4.0 (Sample)

> Fictional data. One table that connects every requirement to scenarios, test cases, results and bugs.

## The matrix

| Requirement | Risk | Scenarios | Test cases | Result (final) | Bugs | Covered? |
|---|---|---|---|---|---|---|
| REQ-BOOK-001 Slot list, 14 days, no past slots | Low | TS-01, 02, 03, 04 | TC-001, 002, 003 | ✅ 3/3 Pass | | ✅ Yes |
| REQ-BOOK-002 Confirm → Confirmed + My Bookings | Medium | TS-05, 06, 07, 08 | TC-004, 005 + ET-BOOK-01 | ✅ 2/2 Pass | | ✅ Yes |
| REQ-BOOK-003 No double booking | **High** | TS-09, 10, 11 | TC-006, 007, 019 + ET-BOOK-01 | ✅ 3/3 Pass | BUG-BOOK-004 (Verified) | ⚠️ Yes, 2 users only. Load not tested. |
| REQ-BOOK-004 Promo code rules | Medium | TS-12 to 17 | TC-008 to 012 | ❌ 4/5 Pass | BUG-BOOK-002 (Open, deferred) | ✅ Yes |
| REQ-BOOK-005 Free/paid cancellation | **High** | TS-18 to 21 | TC-013, 014, 015 + regression checklist | ✅ 3/3 Pass | BUG-BOOK-001 (Verified) | ✅ Yes |
| REQ-BOOK-006 Email + push | Low | TS-22, 23 | TC-016, 017 | ✅ 2/2 Pass | | ✅ Yes |
| REQ-BOOK-007 Customer time zone | **High** | TS-24, 25 | TC-018 | ✅ 1/1 Pass | BUG-BOOK-003 (Verified) | ⚠️ Partly. TS-25 (change zone after booking) not tested yet. |

IDs are shortened in the table: TS-01 = TS-BOOK-01, TC-001 = TC-BOOK-001.

## What the matrix tells us

- **Every requirement has at least one test case.** No requirement was forgotten.
- **Every bug is linked to a requirement.** No "random" bugs; each one breaks an agreed rule.
- **Two gaps are visible and honest:**
  - REQ-BOOK-003 was tested with 2 users, not real load.
  - REQ-BOOK-007: changing time zone after booking is not tested yet.
  Both go into the [release readiness report](../11-test-summary/release-readiness-example.md) as known risks.

## Reading it backwards (bug → requirement)

| Bug | Requirement | Test case | Found by |
|---|---|---|---|
| BUG-BOOK-001 | REQ-BOOK-005 | TC-BOOK-014 | Scripted boundary test |
| BUG-BOOK-002 | REQ-BOOK-004 | TC-BOOK-009 | Scripted edge test |
| BUG-BOOK-003 | REQ-BOOK-007 | TC-BOOK-018 | Scripted cross-platform test |
| BUG-BOOK-004 | REQ-BOOK-003 | TC-BOOK-019 (added after) | Exploratory session ET-BOOK-01 |

This view helps when a requirement changes: you instantly see which test cases and bugs need another look.

## Links to the source documents

[Requirements](../03-requirements-analysis/acceptance-criteria-review-example.md) ·
[Scenarios](../04-test-scenarios/sample-test-scenarios.md) ·
[Test cases](../05-test-cases/sample-test-cases.md) ·
[Exploratory session](../08-exploratory-testing/sample-session.md) ·
[Execution results](../09-test-execution/execution-results-example.md) ·
[Bug reports](../07-bug-reporting/sample-bug-reports.md)
