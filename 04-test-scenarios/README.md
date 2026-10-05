# 04 · Test Scenarios

A test scenario is **one line that says what to check**, without steps.
Example: *"Customer cancels exactly 24 hours before the appointment and pays no fee."*

Scenarios are the fastest way to see coverage. You can review 25 scenarios with a product owner in 10 minutes. You can't do that with 25 full test cases.

## When QA writes them

- Right after the requirements review, before detailed test cases.
- When time is short: scenarios can be executed directly by an experienced tester.
- To review coverage with developers or the product owner ("Did we miss anything?").

## Scenario vs. test case

| Test scenario | Test case |
|---|---|
| **What** to test | **How** to test it |
| One line | Preconditions, data, steps, expected result |
| Good for coverage review | Good for repeatable execution and regression |
| TS-BOOK-19: Cancel at exactly 24h → free | TC-BOOK-014: full steps to check it |

## Files in this folder

| File | Use it for |
|---|---|
| [sample-test-scenarios.md](sample-test-scenarios.md) | 25 scenarios for the booking feature, grouped by requirement, with type, priority and where each one is covered |

## A simple way to write them

For each requirement, ask:
1. What is the normal case?
2. What can the user do wrong?
3. Where are the limits?
4. What about timing, two users, interruptions, platforms?

## Common mistakes

- Scenarios that are too vague: "Check booking works."
- Scenarios that are really test cases (with steps).
- Forgetting to link each scenario to a requirement.
