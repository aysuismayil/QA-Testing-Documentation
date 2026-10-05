# Testing Approach: Book an Appointment (Sample)

**Product:** Demo Booking App (fictional) · **Release:** 2.4.0
**Platforms:** Web (Chrome, Safari), iOS, Android
**Requirements:** REQ-BOOK-001 to REQ-BOOK-007 ([review](../03-requirements-analysis/acceptance-criteria-review-example.md))

---

## 1. Why this feature matters

Booking is the reason the app exists. Every booking is income for the provider and a fee for the business.
If booking breaks, customers go back to phone calls and some never come back.
The worst failures are the ones that break **trust**: two people at the same appointment, or a fee charged when it should be free.

## 2. Known vs. assumed

| Known | Assumption → status |
|---|---|
| Range is today + 13 days | Provider's working hours come from the provider profile → *confirmed by dev* |
| First confirm wins | "Same time" means the server decides by order received → *confirmed* |
| Promo: one code, case and spaces ignored | Promo codes are created by Marketing in the admin panel → *confirmed, test codes requested* |
| Cancel ≥ 24h is free | Fee is charged to the saved card → *payments team owns the charge itself* |
| Times shown in device time zone | Provider can be in another time zone → *confirmed, test provider set to PST* |

## 3. Risk map

| Area | What could go wrong | Impact | Likelihood | Risk |
|---|---|---|---|---|
| Double booking (REQ-003) | Two customers get the same slot | High | Medium (concurrency is hard) | **High** |
| Cancellation fee (REQ-005) | Fee charged at exactly 24h | High (money, complaints) | Medium (boundary) | **High** |
| Booking confirm (REQ-002) | Booking not saved or wrong status | High | Low | **Medium** |
| Time zone (REQ-007) | Customer shows up at wrong hour | High | Medium | **High** |
| Promo code (REQ-004) | Valid code rejected / wrong discount | Medium | Medium | **Medium** |
| Notifications (REQ-006) | No confirmation received | Medium | Low | **Low** |
| Slot list (REQ-001) | Wrong days or past slots shown | Medium | Low | **Low** |

Testing order: High → Medium → Low. High areas also get an exploratory session.

## 4. Must work first

1. App opens, customer can log in.
2. Provider page loads and shows slots.
3. Customer books one slot, sees **Confirmed** in My Bookings.

If any of these fail, the build goes back. No point testing promo codes on a build that can't book.

## 5. Test ideas by type

| Type | For this feature |
|---|---|
| Positive | Book a slot; apply valid code; cancel 3 days before; get email + push |
| Negative | Expired code, unknown code, second code; book a slot that was just taken; cancel an already cancelled booking |
| Boundary | Day 14 shown / day 15 not shown; slot at current time; cancel at **24:00** vs **23:59** before; discount equal to price and bigger than price ($0.00 floor) |
| Edge cases | Two customers confirm at the same moment; double-tap **Confirm & Pay**; app sent to background during confirm; promo code pasted with spaces; device time zone different from provider |
| Integration | Confirmation email content and timing; push with notifications on/off; amount sent to payment step |
| Platform | Latest iOS and Android + one older OS each; Chrome and Safari on web |
| Non-functional | Readable slot list on small phones; screen reader reads slot time and status; booking confirms within a few seconds on a slow network |

## 6. Test data

| Data | Why |
|---|---|
| 2 customer accounts (A, B) | Double-booking test needs two real users |
| Provider in PST, customer device in EST | Time zone check |
| Promo codes: valid, expired, $100-off code | Positive, negative, $0 floor |
| A booking starting in exactly 24h (+/- 1 min) | Cancellation boundary |

## 7. Not testing

| Item | Reason |
|---|---|
| Card payment processing | Owned and tested by the Payments team |
| Rescheduling | Not in this release |
| Load testing (100s of users) | No tool/environment in this cycle. Concurrency is checked with 2 users only. Risk noted in the test plan. |

## 8. Open questions

| # | Question | Answer |
|---|---|---|
| 1 | Is the fee amount shown with tax? | Yes, total fee incl. tax (PO) |
| 2 | Push text: does it include provider name? | Yes, name + date + time (Design) |

---

Next: the [test plan](../01-test-planning/sample-test-plan.md) uses this approach for scope, schedule and exit criteria.
