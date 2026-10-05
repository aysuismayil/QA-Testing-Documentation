# Test Execution Results: Demo Booking App 2.4.0 (Sample)

> Fictional results. Shows how to record a run, link failures to bugs, and track retests.

## Run overview

| Run | Build | Env | When | Goal |
|---|---|---|---|---|
| Run 1 | 2.4.0 (212) | Staging | Day 3–6 | First full execution of TC-BOOK-001 to 019 |
| Run 2 | 2.4.0 (215) | Staging | Day 7–8 | Retest fixes + rerun cases around the fixed code |

Build 215 release notes: fixes for BUG-BOOK-001, BUG-BOOK-003, BUG-BOOK-004. BUG-BOOK-002 not included (deferred).

---

## Run 1 · Build 212

| TC | Title (short) | Platform | Result | Bug / comment |
|---|---|---|---|---|
| TC-BOOK-001 | Slot list loads | Web, iOS, Android | ✅ Pass | |
| TC-BOOK-002 | Past slots hidden | Web, iOS | ✅ Pass | |
| TC-BOOK-003 | Day 14 shown, day 15 not | Web | ✅ Pass | |
| TC-BOOK-004 | Book a slot → Confirmed | Web, iOS, Android | ✅ Pass | |
| TC-BOOK-005 | Details in My Bookings | Web, iOS, Android | ✅ Pass | Time zone checked separately in TC-018 |
| TC-BOOK-006 | Booked slot hidden for others | Web + iOS | ✅ Pass | |
| TC-BOOK-007 | Confirm a slot just taken | Web + iOS | ✅ Pass | |
| TC-BOOK-008 | Valid promo code | Web, Android | ✅ Pass | |
| TC-BOOK-009 | Promo code case + spaces | Web, Android | ❌ Fail | **BUG-BOOK-002**: spaces not trimmed. Case rule passes. |
| TC-BOOK-010 | Expired / unknown code | Web | ✅ Pass | |
| TC-BOOK-011 | One code per booking | Web | ✅ Pass | |
| TC-BOOK-012 | Discount > price → $0.00 | Web | ✅ Pass | |
| TC-BOOK-013 | Cancel 3 days before → free | Web, iOS | ✅ Pass | |
| TC-BOOK-014 | Cancel exactly 24h → free | Web, iOS | ❌ Fail | **BUG-BOOK-001**: fee charged at 24h 00m |
| TC-BOOK-015 | Cancel under 24h → fee shown | Web, iOS | ✅ Pass | |
| TC-BOOK-016 | Email + push | iOS | ⛔ Blocked | Staging email service down (Day 4). Not a product bug. |
| TC-BOOK-017 | Push off → email sent | iOS | ⛔ Blocked | Same as above |
| TC-BOOK-018 | Customer time zone | Web, iOS, Android | ❌ Fail | **BUG-BOOK-003**: My Bookings wrong on iOS + Android; web OK |
| TC-BOOK-019 | Same-moment confirm (added Day 5) | Web + iOS | ❌ Fail | **BUG-BOOK-004**: 2/5 double bookings |

### Run 1 numbers

| Total | Pass | Fail | Blocked | Not run | Pass rate (of executed) |
|---|---|---|---|---|---|
| 19 | 13 | 4 | 2 | 0 | 13 / 17 = **76%** |

---

## Run 2 · Build 215

| TC | Why rerun | Result | Comment |
|---|---|---|---|
| TC-BOOK-014 | Retest BUG-BOOK-001 | ✅ Pass | 24h 01m, 24h 00m free; 23h 59m fee. **BUG-BOOK-001 verified** |
| TC-BOOK-018 | Retest BUG-BOOK-003 | ✅ Pass | iOS + Android + web all show 10:00 AM EST. **Verified** |
| TC-BOOK-019 | Retest BUG-BOOK-004 | ✅ Pass | 10 tries (5 slow network, 5 normal): 0 double bookings. **Verified** |
| TC-BOOK-016 | Was blocked | ✅ Pass | Email 40 s, push 5 s |
| TC-BOOK-017 | Was blocked | ✅ Pass | |
| TC-BOOK-009 | Known open bug | ❌ Fail | BUG-BOOK-002 still open, deferred to 2.4.1 (expected) |
| TC-BOOK-004, 005, 006, 007 | Booking code changed by BUG-004 fix | ✅ Pass | No side effects |
| TC-BOOK-013, 015 | Cancel code changed by BUG-001 fix | ✅ Pass | No side effects |

Plus: regression checklist on build 215. See [regression-checklist.md](../06-checklists/regression-checklist.md). Result: no new issues.

---

## Final status per test case (after Run 2)

| Total | Pass | Fail | Blocked | Not run | Pass rate |
|---|---|---|---|---|---|
| 19 | 18 | 1 (known, deferred) | 0 | 0 | **95%** |

## Bugs from this cycle

| Bug | Severity | Status at end of testing |
|---|---|---|
| BUG-BOOK-001 | High | Verified |
| BUG-BOOK-002 | Low | Open, deferred to 2.4.1, PO accepted |
| BUG-BOOK-003 | High | Verified |
| BUG-BOOK-004 | Critical | Verified |

Next: [traceability](../10-traceability/requirements-traceability-example.md) → [release readiness](../11-test-summary/release-readiness-example.md)
