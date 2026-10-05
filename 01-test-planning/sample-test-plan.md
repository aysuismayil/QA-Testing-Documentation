# Test Plan: Book an Appointment (Sample)

> Fictional example. Product, people, dates and numbers are made up for learning.

## Plan at a glance

| | |
|---|---|
| Product / release | Demo Booking App 2.4.0 |
| Feature | US-BOOK-01 Book an appointment (REQ-BOOK-001 to 007) |
| QA owner | QA Engineer |
| Plan version / date | v1.1, Sprint 24 – Day 1 |
| Testing window | Sprint 24, Day 3 – Day 9 |
| Target release | Sprint 24, Day 10 |
| Status | Approved |

## 1. Goal of testing

Customers can find a slot, book it, apply a promo code and cancel, on web, iOS and Android, **without double bookings, wrong fees or wrong times**.

## 2. Scope

### In scope

| Area | Requirement IDs | Priority |
|---|---|---|
| Slot list (14 days, no past slots) | REQ-BOOK-001 | Low |
| Booking confirm + My Bookings | REQ-BOOK-002 | Medium |
| No double booking | REQ-BOOK-003 | High |
| Promo code rules | REQ-BOOK-004 | Medium |
| Free / paid cancellation | REQ-BOOK-005 | High |
| Email + push confirmation | REQ-BOOK-006 | Low |
| Time zone display | REQ-BOOK-007 | High |
| Regression of login, search, provider page | n/a | Medium |

Priority comes from the risk map in the [testing approach](../02-test-approach/sample-testing-approach.md).

### Out of scope

| Area | Reason | Who covers it |
|---|---|---|
| Card payment processing | Separate service | Payments team |
| Rescheduling | Next release | n/a |
| Load testing | No load tool in this cycle | Risk noted below |
| Provider (business) app | Not changed in 2.4.0 | Smoke only |

## 3. How we will test

| Test type | Why here | When |
|---|---|---|
| Smoke | Is the build testable at all? | Every new build |
| Functional (test cases) | Check every REQ rule, incl. boundaries | Day 3–6 |
| Exploratory | Double booking + interruptions are hard to script | Day 5, 90 min session |
| Retest | Confirm fixes | As fixes arrive |
| Regression | Booking touches login, search, My Bookings | Day 8 |
| Cross-platform | Web, iOS, Android behave the same | Throughout |

## 4. Environments, devices, data

| Item | Details |
|---|---|
| Environment | Staging (payment provider in test mode) |
| Web | Chrome (latest), Safari (latest) |
| iOS | iPhone, latest iOS + one version back |
| Android | Pixel-class phone, latest Android + one version back |
| Accounts | Customer A, Customer B, Provider P (time zone PST) |
| Data | Promo codes `SPRING10` (valid), `WINTER5` (expired), `FREE100` ($100 off); bookings at 24h ± 1 min |
| Email | Test inbox on staging |

## 5. Tools

| Purpose | Tool |
|---|---|
| Test cases / runs | Test management tool (e.g. TestRail) |
| Bugs | Jira |
| API checks | Postman (booking status, promo response) |
| Logs / network | Browser DevTools, device logs |

## 6. Schedule

| Milestone | When |
|---|---|
| Requirements review | Sprint 23 refinement ✔ |
| Test cases written + peer review | Day 1–2 |
| Build ready (code complete) | Day 3 |
| Test execution, run 1 | Day 3–6 |
| Exploratory session | Day 5 |
| Fixes + retest, run 2 | Day 7–8 |
| Regression | Day 8 |
| Go / No-Go meeting | Day 9 |

## 7. Entry and exit criteria

**Start testing when:**
- [ ] Build 2.4.0 is on Staging with release notes
- [ ] Smoke checklist passes
- [ ] Test accounts, promo codes and time zone setup are ready
- [ ] Test cases reviewed

**Pause testing when:**
- Customers can't log in or can't book at all
- Staging is down for more than 2 hours

**Resume when:**
- A new build fixes the blocker and smoke passes again

**Testing is done when:**
- [ ] 100% of planned test cases executed (Pass / Fail / Blocked with reason)
- [ ] No open **Critical** bugs
- [ ] No open **High** bugs, unless the Product Owner accepts it in writing with a workaround
- [ ] All **High** risk areas tested on web, iOS and Android
- [ ] Regression run complete with no new Critical/High bugs
- [ ] Test summary report shared before the Go / No-Go meeting

## 8. Risks

| Risk | Impact on testing | What we'll do |
|---|---|---|
| Concurrency can't be fully tested with 2 users | Double booking may still happen under real load | Exploratory session with 2 users + slow network; recommend load test next release |
| Late build | Less time for regression | Test High risk areas first; smoke on every build |
| Email delays on staging | Notification tests blocked | Check email service status first; mark Blocked, not Failed |
| Fix for double booking touches booking service | New bugs in booking/cancel | Rerun all booking + cancellation cases after the fix |

## 9. Deliverables

| Deliverable | Link |
|---|---|
| Test scenarios | [sample-test-scenarios.md](../04-test-scenarios/sample-test-scenarios.md) |
| Test cases | [sample-test-cases.md](../05-test-cases/sample-test-cases.md) |
| Exploratory session notes | [sample-session.md](../08-exploratory-testing/sample-session.md) |
| Execution results | [execution-results-example.md](../09-test-execution/execution-results-example.md) |
| Bug reports | [sample-bug-reports.md](../07-bug-reporting/sample-bug-reports.md) |
| Traceability | [requirements-traceability-example.md](../10-traceability/requirements-traceability-example.md) |
| Release readiness report | [release-readiness-example.md](../11-test-summary/release-readiness-example.md) |

## 10. People

| Role | Responsibility in testing |
|---|---|
| QA Engineer | Plan, test cases, execution, bugs, report, Go/No-Go input |
| Developers (web, mobile, backend) | Fixes, build notes, help with logs |
| Product Owner | Answers questions, accepts or rejects known issues |
| Designer | Questions about UI and messages |

## 11. Open questions

| # | Question | Owner | Status |
|---|---|---|---|
| 1 | Is the cancellation fee shown with tax? | PO | Closed: yes, incl. tax |
| 2 | Do we need a load test before release? | Eng lead | Closed: not this release, planned next |

## 12. Approval

| Role | Date | OK? |
|---|---|---|
| Product Owner | Day 2 | ✔ |
| Engineering Lead | Day 2 | ✔ |
| QA | Day 2 | ✔ |
