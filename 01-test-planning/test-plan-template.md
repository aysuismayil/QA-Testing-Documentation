# Test Plan Template

Copy this file for each release or big feature. Keep it short and real: if a section doesn't apply, write "N/A" and why.
Hints are in *italics*. Delete them when you fill it in.

---

# Test Plan: *[Feature or Release name]*

## Plan at a glance

| | |
|---|---|
| Product / release | *e.g. App name 3.1.0* |
| Feature(s) | *Story / epic IDs* |
| QA owner | |
| Plan version / date | *v1.0, date* |
| Testing window | *start – end* |
| Target release date | |
| Status | *Draft / In review / Approved* |

## 1. Goal of testing

*1–3 sentences. What must be true before we can release? Example: "Customers can book, pay and cancel without double bookings or wrong fees."*

## 2. Scope

### In scope

| Area | Requirement IDs | Priority |
|---|---|---|
| | | High / Medium / Low |

### Out of scope

| Area | Reason | Who covers it |
|---|---|---|
| | | |

## 3. How we will test

*Short summary. Link the testing approach for details.*

| Test type | Why we need it here | When |
|---|---|---|
| Smoke | | Every new build |
| Functional | | |
| Exploratory | | |
| Regression | | |
| *other* | | |

## 4. Environments, devices, data

| Item | Details |
|---|---|
| Test environment(s) | *e.g. QA, Staging* |
| Browsers | |
| Mobile devices / OS | |
| Test accounts | *roles, how many* |
| Test data | *special data you must prepare* |
| Third-party services | *sandbox / test mode?* |

## 5. Tools

| Purpose | Tool |
|---|---|
| Test cases / runs | |
| Bug tracking | |
| API checks | |
| Logs / network | |

## 6. Schedule

| Milestone | Date | Notes |
|---|---|---|
| Requirements review done | | |
| Test cases ready + reviewed | | |
| Build ready for QA (code complete) | | |
| Test execution | | |
| Regression | | |
| Release decision (Go / No-Go) | | |

## 7. Entry and exit criteria

**Start testing when:**
- [ ] *e.g. Smoke checklist passes on the build*
- [ ] 

**Pause testing when:**
- *e.g. Login or main flow is broken (blocker)*

**Resume when:**
- *e.g. A new build fixes the blocker and smoke passes again*

**Testing is done when:**
- [ ] *e.g. 100% of planned test cases executed*
- [ ] *e.g. No open Critical/High bugs, or each one accepted in writing*
- [ ] 

*Write criteria you can check with a yes/no. See [entry-exit-criteria.md](../12-qa-reference/entry-exit-criteria.md).*

## 8. Risks

| Risk | Impact on testing | What we'll do |
|---|---|---|
| | | |

## 9. Deliverables

| Deliverable | Where |
|---|---|
| Test cases | |
| Test run results | |
| Bug reports | |
| Traceability matrix | |
| Test summary / release readiness report | |

## 10. People

| Role | Name | Responsibility in testing |
|---|---|---|
| QA | | |
| Developer(s) | | |
| Product owner | | |

## 11. Open questions

| # | Question | Owner | Status |
|---|---|---|---|
| | | | |

## 12. Approval

| Role | Name | Date | OK? |
|---|---|---|---|
| | | | |

---

## Common mistakes

- Copying last release's plan and forgetting to change scope and dates.
- Out of scope list is empty. Something is always out of scope.
- Exit criteria like "testing is finished" or "quality is good". Not measurable.
- Risks with no action ("tight deadline" and nothing else).
- 20 pages nobody reads. A good plan is the shortest plan that still answers: what, how, when, who, when are we done.

See a filled-in version: [sample-test-plan.md](sample-test-plan.md)
