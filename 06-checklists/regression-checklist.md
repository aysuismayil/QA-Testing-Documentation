# Regression Checklist

**Goal:** make sure **new changes didn't break things that worked before**.
Regression is deep where the risk is, and light everywhere else. You rarely have time to rerun everything, so you choose.

---

## Step 1 · Decide the scope

Answer these before you start:

- [ ] What changed in this build? (release notes, merged tickets, ask the developers)
- [ ] Which areas **share code or data** with the change?
- [ ] Which flows bring money or are used the most?
- [ ] Where did bugs happen in the last releases?
- [ ] Which bugs were fixed in this build? (retest them + the area around them)

## Step 2 · Choose what to run

| Level | What | When |
|---|---|---|
| **Must run** | Areas changed + areas sharing code + critical flows | Every release |
| **Should run** | Areas with recent bugs, important secondary flows | If time allows (usually yes) |
| **Can skip this time** | Stable areas not touched for a while | Write down that you skipped them |

## Step 3 · Run and record

- [ ] Use the same test cases as before (don't rewrite during regression)
- [ ] Record build number and platform
- [ ] New bug? Check: is it **new in this build** (regression) or was it always there? Try the previous build if possible.
- [ ] Update test cases that no longer match the agreed behavior

---

## Demo Booking App 2.4.0 example (build 215)

**Changed:** booking service (fix for BUG-BOOK-004), cancellation rule (BUG-BOOK-001), mobile My Bookings time display (BUG-BOOK-003).

| Area | Why | Level | Result |
|---|---|---|---|
| Book a slot on web, iOS, Android | Booking service changed | Must | ✅ |
| Same-moment double booking (TC-BOOK-019) | Fix verification + stays in regression | Must | ✅ |
| Cancel: free, exactly 24h, under 24h | Cancellation rule changed | Must | ✅ |
| Cancel an already cancelled booking (two tabs) | Cancel code changed; TS-BOOK-21 | Must | ✅ |
| My Bookings list and details, all platforms | Display code changed | Must | ✅ |
| Booking confirmation email + push | Uses booking data | Should | ✅ |
| Promo code apply / remove | Same checkout screen | Should | ✅ (BUG-BOOK-002 still known) |
| Login / logout | Critical flow | Must | ✅ |
| Search and provider page | Critical flow, not changed | Should (quick pass) | ✅ |
| Profile settings, help pages | Not touched, stable | Skipped | Written in report |

**Result:** no new issues.

---

## Common mistakes

- "Regression = run everything" → never finishes, so the important areas get rushed.
- Testing only the fixed bug, not the code around it.
- Not knowing what changed. Always read the release notes / ask.
- Not writing down what was skipped. Skipping is fine. Hiding it isn't.
- Never adding new test cases to the regression suite after a bug escapes.
