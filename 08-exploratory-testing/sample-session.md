# Exploratory Session ET-BOOK-01: Booking Under Pressure (Sample)

> Fictional session for the fictional Demo Booking App. Shows how a charter, notes and follow-ups look in practice.

## Charter

| | |
|---|---|
| Session ID | ET-BOOK-01 |
| Explore | Booking confirm and My Bookings |
| With | Customer A (web, Chrome), Customer B (iOS), slow network throttling, provider schedule view |
| To discover | Double bookings, "half" bookings and wrong states caused by timing, interruptions and two users |
| Time box | 90 min |
| Build / env | 2.4.0 (212), Staging |
| Why this area | Highest risk in the [risk map](../02-test-approach/sample-testing-approach.md#3-risk-map); hard to cover with scripted cases |

## Session notes

| # | What I tried | What happened | Follow-up |
|---|---|---|---|
| 1 | Double-tap **Confirm & Pay** on iOS | Button disables after first tap. One booking. | None, works |
| 2 | Double-click on web with slow network | Button disables, but spinner shows ~4 s with no text | Note for designer: add "Booking…" text |
| 3 | A and B confirm the same slot one after the other (~3 s apart) | B gets "This time is no longer available" | None, matches TC-BOOK-007 |
| 4 | A and B confirm at the **same moment**, normal network, 5 tries | 0/5 double bookings | Try with slow network |
| 5 | Same as #4 with slow network on both, 5 tries | **2/5: both customers booked the same slot** | **BUG-BOOK-004** (Critical) |
| 6 | Put iOS app in background right after tapping Confirm, open again after 30 s | Success screen shows; booking is Confirmed | None, works |
| 7 | Turn off Wi-Fi right after clicking Confirm (web, laptop) | Error "Something went wrong", but booking **was** created | Question to dev: should the app check status before showing an error? Logged as Q-01 |
| 8 | Browser back from the success screen | Returns to summary with Confirm & Pay still active; tapping it shows "already booked" | Minor UX, logged as low priority improvement |
| 9 | Open My Bookings in two tabs, cancel in tab 1, cancel again in tab 2 | Tab 2 shows "This booking is already cancelled" | None, works |
| 10 | Provider with no free slots for 14 days | Empty state: "No free times in the next 2 weeks" | None, works |

## Session summary

| | |
|---|---|
| Time | 10 min setup · 65 min testing · 15 min bug investigation |
| Bugs filed | **BUG-BOOK-004** (Critical, double booking with slow network) |
| Questions | Q-01: Network loss after confirm shows an error even when the booking succeeded |
| Improvements | Loading text on Confirm button; back button after success |
| New test cases | **TC-BOOK-019** (same-moment confirm, slow network, 5 tries) added to regression |
| Not covered | Real load (many users), Android, daylight saving dates, changing device time zone after booking (TS-BOOK-25) → next session ET-BOOK-02 |
| Feeling about the area | **Risky until BUG-BOOK-004 is fixed.** Other interruption cases look solid. |

## What made this session useful

- **Two real users, not one.** Single-user scripted tests passed. The bug only appears with two people.
- **Changing one condition at a time.** Normal network: 0/5. Slow network: 2/5. That told the developer where to look.
- **Writing down "works" too.** Rows 1, 3, 6, 9 and 10 show what was checked and is fine, which matters for the release decision.
