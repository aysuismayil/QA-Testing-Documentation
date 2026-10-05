# QA Testing Documentation

A practical collection of QA documentation, templates, examples, and checklists based on real testing workflows.

Use it to:
- create a QA document quickly from a template,
- see what a filled-in version looks like,
- check your own work before you share it.

All examples follow **one fictional product, Demo Booking App**, so you can follow a single feature (booking an appointment) through the whole testing lifecycle.

---

## Find what you need

| I want to learn / create... | Go here |
|---|---|
| Test Plan | [01-test-planning](01-test-planning/) |
| Testing Approach | [02-test-approach](02-test-approach/) |
| Requirements Review | [03-requirements-analysis](03-requirements-analysis/) |
| Test Scenarios | [04-test-scenarios](04-test-scenarios/) |
| Test Cases | [05-test-cases](05-test-cases/) |
| Smoke / Regression / Release checklists | [06-checklists](06-checklists/) |
| Bug Reports | [07-bug-reporting](07-bug-reporting/) |
| Exploratory Testing | [08-exploratory-testing](08-exploratory-testing/) |
| Test Execution results | [09-test-execution](09-test-execution/) |
| Traceability | [10-traceability](10-traceability/) |
| Test Summary / Release readiness | [11-test-summary](11-test-summary/) |
| Quick answers (severity vs. priority, entry/exit criteria...) | [12-qa-reference](12-qa-reference/) |

---

## Follow one feature from start to release

Feature: **US-BOOK-01 · Book an appointment** (Demo Booking App 2.4.0)

| Step | Document | What happens |
|---|---|---|
| 1 | [Requirements review](03-requirements-analysis/acceptance-criteria-review-example.md) | Vague story → clarification questions → **REQ-BOOK-001 to 007** |
| 2 | [Testing approach](02-test-approach/sample-testing-approach.md) | Business goal, risk map, test ideas |
| 3 | [Test plan](01-test-planning/sample-test-plan.md) | Scope, schedule, environments, entry/exit criteria |
| 4 | [Test scenarios](04-test-scenarios/sample-test-scenarios.md) | **TS-BOOK-01 to 25**, one line each |
| 5 | [Test cases](05-test-cases/sample-test-cases.md) | **TC-BOOK-001 to 019** |
| 6 | [Exploratory session](08-exploratory-testing/sample-session.md) | **ET-BOOK-01** finds a double-booking bug |
| 7 | [Execution results](09-test-execution/execution-results-example.md) | 2 runs, 2 builds, pass/fail/blocked |
| 8 | [Bug reports](07-bug-reporting/sample-bug-reports.md) | **BUG-BOOK-001 to 004** |
| 9 | [Traceability](10-traceability/requirements-traceability-example.md) | REQ → TC → result → bug, with gaps shown |
| 10 | [Regression](06-checklists/regression-checklist.md) / [Smoke](06-checklists/smoke-testing-checklist.md) | Targeted regression around the fixes |
| 11 | [Release readiness](11-test-summary/release-readiness-example.md) | **GO with one known issue** |

One example of how the IDs connect:

```
REQ-BOOK-005  Free cancellation at 24h or more before start
   └─ TS-BOOK-19  Cancel at exactly 24h 00m → free
       └─ TC-BOOK-014  Run 1: Fail
           └─ BUG-BOOK-001  Late fee charged at exactly 24h → fixed in build 215
               └─ TC-BOOK-014  Run 2: Pass → Verified → included in release decision
```

---

## How each topic is written

Most folders follow the same pattern:

**What it is → When QA uses it → Template → Filled-in example → Common mistakes**

Short explanations, real-life situations, tables and checklists. Less theory, more "what do I actually write".

---

## Using the templates

- Copy any template into Confluence, Google Docs, Jira, a test management tool, or a Markdown file.
- Delete the hints in *italics*.
- Keep the IDs. They are what makes traceability possible.
- Make it shorter for small changes. A one-line bug fix doesn't need a 10-section test plan.

---

## About the examples

Demo Booking App, its users, providers, promo codes, builds, numbers and bugs are **fictional**.
No real company, product, user, or project data is included.

---

## Author

**Aysu Ismayilzada** · QA Engineer (web and mobile, manual and API testing)
[GitHub](https://github.com/aysuismayil) · [Portfolio](https://aysuismayil.github.io)

This library grows as I keep learning and testing. Suggestions and corrections are welcome through Issues.

## License

Copyright © 2026 Aysu Ismayilzada. Licensed under [CC BY 4.0](LICENSE): free to use and adapt, with credit.
