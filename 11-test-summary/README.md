# 11 · Test Summary & Release Readiness

The test summary is the **last QA document before a release**. It tells the team what was tested, what was found, what's still open, and QA's recommendation: **GO** or **NO-GO**.

QA gives the recommendation with facts. The business (product owner, engineering lead) makes the final call, especially when accepting known risks.

## When QA writes it

- Before a Go / No-Go or release meeting.
- At the end of a test cycle or sprint, as a short status.
- After a hotfix, in a much shorter form (3–5 lines is fine).

## Files in this folder

| File | Use it for |
|---|---|
| [test-summary-template.md](test-summary-template.md) | Template: recommendation, scope, results, bugs, exit criteria, risks |
| [release-readiness-example.md](release-readiness-example.md) | Filled-in GO-with-known-issue report for Demo Booking App 2.4.0 |

## What a good report has

- The **recommendation first**, in plain words.
- Numbers **with context** (19 run, 18 pass, 1 accepted).
- Every open bug with impact, workaround, who accepted it, and when it will be fixed.
- Honest **gaps**: what wasn't tested and why.
- A check against the **exit criteria** from the test plan.

## GO / NO-GO: a simple guide

| Situation | Usual recommendation |
|---|---|
| All exit criteria met | GO |
| Only Low/Medium bugs open, with workaround and owner | GO with known issues |
| Critical bug open in the main flow | NO-GO |
| High-risk area not tested at all | NO-GO, or GO only if the business accepts the risk in writing |

## Common mistakes

- No clear recommendation ("testing is done" is not a recommendation).
- Treating the report as a formality written after the decision.
- Not mentioning gaps.
- Forgetting the after-release smoke check.
