# Test Plan vs. Testing Approach (and Test Strategy)

These names are mixed up a lot, and every company uses them a bit differently. This is a practical way to separate them.

| | Test strategy | Test plan | Testing approach |
|---|---|---|---|
| Level | Company / product | Release / project | Feature |
| Question | How do **we** test in general? | **What, when, who** for this release? | **How** will I test **this feature** and why? |
| Typical content | Test levels, tools, automation vs. manual, environments, defect process | Scope, out of scope, schedule, environments, entry/exit criteria, risks, deliverables, sign-off | Business goal, assumptions, risk map, test ideas by type, test data, what's not tested |
| Changes | Rarely | Every release | Every feature |
| Length | Medium | Medium | Short (1–2 pages) |
| Main reader | Team leads, new team members | Whole team, managers | QA, devs, PO |

Some teams have only a test plan with an "approach" section inside. That's fine. What matters is that the content exists.

---

## Same feature, different documents

Demo Booking App, cancellation rule (REQ-BOOK-005):

| Document | What it says about cancellation |
|---|---|
| Test strategy | "Money-related rules always get boundary tests and are part of regression." |
| [Test plan](../01-test-planning/sample-test-plan.md) | "Cancellation is in scope, High priority, tested on web + iOS during Day 3–6. Exit: no open High bugs." |
| [Testing approach](../02-test-approach/sample-testing-approach.md) | "Risk: fee charged at exactly 24h. Test 24h 01m / 24h 00m / 23h 59m. Need bookings created at exact times." |

## Interview answer (short)

> "A test plan is about organizing the testing for a release: scope, schedule, environments, who does what, and entry and exit criteria. A testing approach is about how I think about testing a specific feature: the business goal, the risks, and which kinds of tests I'll run, like negative, boundary and edge cases. The plan says *what and when*, the approach says *how and why*."

## Common mistakes

- A "test plan" that is only a list of test cases.
- An "approach" that lists every test type ever invented, without connecting them to the feature.
- Arguing about names instead of making sure scope, risks and exit criteria are written somewhere.
