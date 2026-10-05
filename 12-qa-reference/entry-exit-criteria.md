# Entry and Exit Criteria

| | Entry criteria | Exit criteria |
|---|---|---|
| Answers | "Can we **start** testing?" | "Can we **stop** testing / are we ready?" |
| Protects from | Wasting time on a broken or incomplete build | Releasing too early, or testing forever |
| Written in | Test plan | Test plan, checked in the test summary |

Two more that are useful:
- **Suspension criteria**: when to **pause** testing (e.g. login broken).
- **Resumption criteria**: when to **continue** (e.g. new build fixes it and smoke passes).

---

## Good criteria are checkable

Each line should be answerable with **yes / no** by anyone.

| Weak | Strong |
|---|---|
| Build is ready | Build 2.4.0 is deployed on Staging and release notes are shared |
| Environment is OK | Smoke checklist passes on Staging |
| Data is available | 2 customer accounts, 1 provider in another time zone, 3 promo codes exist |
| Testing is complete | 100% of planned test cases executed; each has Pass / Fail / Blocked with reason |
| Quality is good | No open Critical bugs; High bugs fixed or accepted in writing by the PO |
| Most tests pass | Pass rate ≥ 95% of executed cases, and every failure has a bug with a decision |

---

## Ready-to-use examples

### Entry
- [ ] Requirements reviewed, open questions answered or written as assumptions
- [ ] Test cases written and reviewed
- [ ] Build deployed to the test environment, version confirmed
- [ ] Smoke checklist passes
- [ ] Test accounts and test data ready
- [ ] Third-party services available in test mode (email, payments)

### Suspension
- Smoke fails, or the main flow is blocked
- Environment down for more than an agreed time (e.g. 2 hours)
- A big requirement change during testing

### Resumption
- Blocker fixed in a new build and smoke passes again
- Updated requirements reviewed and test cases updated

### Exit
- [ ] All planned test cases executed (or skipped with reason)
- [ ] No open Critical bugs
- [ ] No open High bugs unless accepted in writing with a workaround
- [ ] All high-risk areas tested on all target platforms
- [ ] Regression completed on the release candidate build
- [ ] Test summary shared

Used in practice: [sample-test-plan.md](../01-test-planning/sample-test-plan.md#7-entry-and-exit-criteria) · checked in [release-readiness-example.md](../11-test-summary/release-readiness-example.md#5-exit-criteria-check)

---

## What if exit criteria are not met?

That doesn't automatically mean "no release". It means a **decision** is needed:
1. Show which criterion is not met and why.
2. Explain the risk in user terms.
3. Suggest options (fix and delay / release with workaround / release without the feature).
4. The business decides, and the decision is written down.

## Common mistakes

- Criteria nobody can measure.
- Exit criteria written but never checked at release time.
- Pass-rate only ("95%") without looking at **which** tests failed.
- Starting to test before entry criteria are met, then reporting bugs that are just setup problems.
