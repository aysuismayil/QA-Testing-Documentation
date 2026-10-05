# Smoke Testing Checklist

**Goal:** decide in 15–30 minutes if a build is **worth testing** (or safe after a deploy).
Smoke is wide and shallow: touch every critical area once, don't go deep.

**Rule:** if any item marked 🔴 fails, stop and send the build back. Don't start full testing on a broken build.

---

## Part A · Generic smoke (any web or mobile app)

| # | Check | Critical |
|---|---|---|
| 1 | App / site opens without crash or blank screen | 🔴 |
| 2 | Correct build/version is deployed (check About screen, footer, or release notes) | 🔴 |
| 3 | Sign up or log in with an existing test account | 🔴 |
| 4 | Main navigation works: every main tab/menu opens | 🔴 |
| 5 | Main business flow works once, start to finish | 🔴 |
| 6 | Data is saved: create something, refresh, it's still there | 🔴 |
| 7 | Search / list pages load with data | |
| 8 | Key integration answers (email, payment test mode, maps...) | |
| 9 | Log out works | |
| 10 | No obvious errors in console / crash logs during the above | |

## Part B · Demo Booking App example (build 2.4.0)

| # | Check | Critical | Result |
|---|---|---|---|
| 1 | Web, iOS and Android open; version shows 2.4.0 (215) | 🔴 | |
| 2 | Customer A logs in | 🔴 | |
| 3 | Search shows providers near test location | 🔴 | |
| 4 | Provider page shows slot list | 🔴 | |
| 5 | Book one slot → Confirmed → visible in My Bookings | 🔴 | |
| 6 | Apply `SPRING10` → discount shown | | |
| 7 | Cancel the booking (3+ days ahead) → free | | |
| 8 | Confirmation email arrives in test inbox | | |
| 9 | Provider app opens and shows the new booking | | |
| 10 | Log out | | |

**Time:** about 20 minutes for all 3 platforms if one person runs items 1–5 on each and 6–10 on one platform.

---

## Production smoke (after deploy)

Use a **real but internal** test account on production. Don't create real charges unless the team has a safe way (test card / refund process).

- [ ] Version on production = released version
- [ ] Log in, open main pages
- [ ] Main flow up to the step before payment (or full flow if agreed)
- [ ] One new feature from this release works
- [ ] Clean up any test data you created

## Common mistakes

- Smoke that takes 2 hours. That's regression.
- Continuing full testing on a build that failed smoke "to save time".
- Forgetting to check the **version**. Testing the old build is a classic.
- Same smoke list for years. Update it when the main flows change.
