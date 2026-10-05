# Testing Approach Template

A testing approach is **how you think about testing one feature**: what matters, where the risk is, and what kinds of tests you will run.
It's short (1–2 pages). Write it after the requirements review and before test cases.

Copy the sections below. Delete hints in *italics*.

---

## Feature

| | |
|---|---|
| Feature | *Name + ticket/story ID* |
| Platforms | *Web / iOS / Android / API* |
| Requirements | *Links or IDs* |
| Written by / date | |

## 1. Why this feature matters

*2–3 sentences. What is the business goal? What happens to the user and the business if it breaks?*

## 2. What I know and what I'm assuming

| Known (from requirements) | Assumption (not confirmed yet) |
|---|---|
| | |

*Every assumption is a question. Ask it, then move it to "Known".*

## 3. Risk map

*Where would a bug hurt most? Rate each area. Test High first and deepest.*

| Area | What could go wrong | Impact | Likelihood | Risk |
|---|---|---|---|---|
| | | High / Med / Low | High / Med / Low | **High / Med / Low** |

## 4. Must work first

*The few checks that tell you the build is worth testing at all, plus the main happy path from start to finish.*

1.
2.
3.

## 5. Test ideas by type

| Type | What I will check for this feature |
|---|---|
| Positive / functional | *Each rule works with normal, valid data* |
| Negative | *Invalid input, wrong state, not allowed actions* |
| Boundary | *Exact limits: min, max, just inside, just outside* |
| Edge cases | *Timing, order of actions, interruptions, back/refresh, two users at once* |
| Integration | *Email, push, payments, other services* |
| Platform | *Browsers, devices, OS versions that matter* |
| Non-functional | *Only what's relevant: usability, accessibility, speed the user can feel, security basics* |

## 6. Test data I need

| Data | Why |
|---|---|
| | |

## 7. Not testing (and why)

| Item | Reason |
|---|---|
| | *Out of scope / owned by another team / no tool or environment / low risk* |

## 8. Open questions

| # | Question | Asked to | Answer |
|---|---|---|---|
| 1 | | | |

---

## Common mistakes

- Copying the same generic list of test types for every feature. If a type doesn't apply, say so.
- No risk ranking, so every area gets the same time.
- Hiding what you won't test. Write it down. It protects you and informs the team.
- Writing it once and never updating it after a requirement changes.

See a filled-in version: [sample-testing-approach.md](sample-testing-approach.md)
