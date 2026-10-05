# 01 · Test Planning

A test plan tells the team **what** will be tested, **how**, **when**, **by whom**, and **when testing is done**.
It's an agreement, not a formality: when scope or exit criteria are written down, nobody is surprised at release time.

## When QA writes one

- At the start of a release, or a big feature.
- When several people/teams test the same release.
- When the business needs a clear Go / No-Go rule.

For a small bug fix you usually don't need a full plan. A few lines in the ticket (scope + what you'll retest) is enough.

## Files in this folder

| File | Use it for |
|---|---|
| [test-plan-template.md](test-plan-template.md) | Empty template with hints |
| [sample-test-plan.md](sample-test-plan.md) | Filled-in plan for Demo Booking App 2.4.0 |

## What a reader should find in 1 minute

- What's in scope and **what's not**
- Which areas are high risk
- Environments, devices, test data
- Entry / exit criteria you can check with yes/no
- Dates and owners

## Common mistakes

- Plan written once and never updated when scope changes.
- No "out of scope" section, so people assume everything was tested.
- Exit criteria that can't be measured ("good quality").
- Risks listed without an action.
- Too long. If nobody reads it, it doesn't help.

## Related

- [Testing approach](../02-test-approach/) – the thinking behind the plan
- [Entry / exit criteria](../12-qa-reference/entry-exit-criteria.md)
- [Test plan vs. test approach](../12-qa-reference/test-plan-vs-test-approach.md)
