# QA Documentation Checklist

Use it to review your own QA documents (or a teammate's) before sharing them.

---

## For every document

- [ ] Has a clear title, product/version, and date or sprint
- [ ] Someone new can understand it without asking you
- [ ] Uses IDs (REQ-, TS-, TC-, BUG-) instead of "the thing we discussed"
- [ ] Short sentences, tables and lists where possible
- [ ] No real customer data, real passwords, tokens or internal links in shared/public copies
- [ ] Says what's **not** covered

## Requirements review

- [ ] Every unclear AC has a written question
- [ ] Answers are written back into the ticket
- [ ] Boundaries, errors, time zones, money rules, two-user cases checked
- [ ] Final requirements have IDs

## Testing approach / test plan

- [ ] Business goal in 1–3 sentences
- [ ] Risks ranked, high risk tested first
- [ ] In scope **and** out of scope (with reasons)
- [ ] Environments, devices, test data listed
- [ ] Entry / exit criteria are yes/no checkable
- [ ] Risks have an action

## Test scenarios / test cases

- [ ] Every requirement has at least one test
- [ ] Positive, negative, boundary and edge cases where they make sense
- [ ] Exact test data
- [ ] Expected results are checkable (numbers, statuses, messages)
- [ ] One goal per test case
- [ ] Reusable for regression (no data that only works today)

## Bug reports

- [ ] Title: area + what's wrong + condition
- [ ] Build, environment, platform
- [ ] Steps from a clean state
- [ ] Expected (with reference) vs. actual (exact)
- [ ] Severity and priority separate
- [ ] Frequency, evidence, workaround
- [ ] One bug per report, no guessing about the cause

## Execution / traceability / summary

- [ ] Results recorded with build number
- [ ] Failed → bug linked; Blocked → reason written
- [ ] Traceability shows gaps honestly ("partly covered")
- [ ] Summary starts with a clear recommendation
- [ ] Every open bug has impact, workaround, owner, plan
- [ ] Exit criteria checked one by one

---

## The 30-second test

Give the document to someone who wasn't in the meetings. Can they answer:
1. What was tested?
2. What wasn't, and why?
3. What's broken right now?
4. What does QA recommend?

If yes, the document is doing its job.
