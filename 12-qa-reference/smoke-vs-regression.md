# Smoke vs. Regression (and Sanity, Retest)

| | Smoke | Sanity | Retest | Regression |
|---|---|---|---|---|
| Question | Is the build **testable / alive**? | Does **this fix or small change** basically work? | Is **this bug** fixed? | Did changes **break anything that worked**? |
| Width | Wide, all critical areas | Narrow, one area | One bug | Wide or targeted, based on risk |
| Depth | Shallow | Shallow | Exact bug steps | Deep where risk is |
| Time | 15–30 min | Minutes | Minutes | Hours to days |
| When | Every new build, after deploy | After a small fix / hotfix | When a fix is ready | Before release, after big changes |
| If it fails | Reject the build | Send the fix back | Reopen the bug | New bug (regression) |

Note: teams use "smoke" and "sanity" differently. Agree on the meaning in your team and stay consistent.

---

## Demo Booking App example

| Moment | What QA ran | Type |
|---|---|---|
| Build 212 arrives | Log in, open provider, book one slot, see it in My Bookings | Smoke |
| BUG-BOOK-001 fix in build 215 | Cancel at 24h 01m, 24h 00m, 23h 59m | Retest |
| Same build | Cancel 3 days before, cancel under 24h, cancel twice | Regression around the fix |
| Before release | Booking, cancel, My Bookings, login, search on all platforms | Regression |
| After deploy | Same as smoke, on production | Smoke (production) |

Checklists: [smoke](../06-checklists/smoke-testing-checklist.md) · [regression](../06-checklists/regression-checklist.md)

---

## Interview answer (short)

> "Smoke testing checks that the build is stable enough to test: the app opens, I can log in, and the main flow works once. If smoke fails, I send the build back. Regression testing checks that new changes didn't break existing features. I choose the regression scope based on what changed, what shares code with it, and the most important flows."

## Common mistakes

- Calling a 4-hour test run "smoke".
- Retesting the fixed bug but skipping regression around it.
- Running the full regression for a one-line text change. Match effort to risk.
- Regression suite never updated with tests for escaped bugs.
