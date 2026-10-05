# Test Cases: Book an Appointment (Sample)

**Product:** Demo Booking App 2.4.0 (fictional)
**Requirements:** REQ-BOOK-001 to 007 · **Scenarios:** [sample-test-scenarios.md](../04-test-scenarios/sample-test-scenarios.md)

## Shared test data

| Item | Value |
|---|---|
| Customer A | `customer.a@example.test`, device time zone **EST** |
| Customer B | `customer.b@example.test`, device time zone EST |
| Provider | "Demo Hair Studio", time zone **PST** |
| Service | Haircut, 45 min, **$50.00**, tax 8% |
| Promo codes | `SPRING10` = $5.00 off (valid) · `WINTER5` (expired) · `FREE100` = $100.00 off (valid) |

---

## Full test cases (high risk or tricky)

### TC-BOOK-004 · Book an available slot → status Confirmed

| | |
|---|---|
| Requirement | REQ-BOOK-002 |
| Priority / Type | High / Positive |
| Platform | All |
| Preconditions | Customer A is logged in. Provider has free slots tomorrow. |
| Test data | Service: Haircut, tomorrow 10:00 AM EST |

| # | Step | Expected result |
|---|---|---|
| 1 | Open "Demo Hair Studio" → Haircut | Slot list for 14 days is shown |
| 2 | Select tomorrow, 10:00 AM | Summary shows: Haircut, tomorrow, 10:00 AM EST, $50.00 + tax = **$54.00** |
| 3 | Tap **Confirm & Pay** | Success screen: "You're booked!" with date and time |
| 4 | Open **My Bookings** | Booking is listed with status **Confirmed** |

---

### TC-BOOK-007 · Second customer confirms a slot that was just taken

| | |
|---|---|
| Requirement | REQ-BOOK-003 |
| Priority / Type | High / Negative |
| Platform | All (A on web, B on mobile) |
| Preconditions | A and B are logged in on separate devices. Both have the same provider's slot list open. |
| Test data | Slot: tomorrow 11:00 AM |

| # | Step | Expected result |
|---|---|---|
| 1 | B selects 11:00 AM and stays on the summary screen | Summary shown |
| 2 | A selects 11:00 AM and taps **Confirm & Pay** | A's booking is Confirmed |
| 3 | B taps **Confirm & Pay** (B's screen is now out of date) | B sees *"This time is no longer available"*. No booking created for B. B is not charged. |
| 4 | B looks at the slot list | List refreshed, 11:00 AM is gone |

| Notes | This checks the "one after the other" case. The "exactly at the same moment" case is TC-BOOK-019. |
|---|---|

---

### TC-BOOK-009 · Promo code in lower case with spaces is accepted

| | |
|---|---|
| Requirement | REQ-BOOK-004 |
| Priority / Type | Medium / Edge |
| Platform | All |
| Preconditions | Customer A on the booking summary for Haircut ($50.00) |
| Test data | Run once per value: `spring10` · `Spring10` · `␣SPRING10␣` (one space before and after) |

| # | Step | Expected result |
|---|---|---|
| 1 | Tap **Add promo code**, enter the value, tap **Apply** | Code accepted. Discount line: **−$5.00** |
| 2 | Check totals | Subtotal $45.00, tax $3.60, total **$48.60** |

| Notes | Users copy codes from emails. Copy-paste often adds spaces. Failed in run 1 → [BUG-BOOK-002](../07-bug-reporting/sample-bug-reports.md#bug-book-002) |
|---|---|

---

### TC-BOOK-012 · Discount bigger than price → total is $0.00

| | |
|---|---|
| Requirement | REQ-BOOK-004 |
| Priority / Type | Medium / Boundary |
| Platform | Web |
| Preconditions | Customer A on the booking summary for Haircut ($50.00) |
| Test data | `FREE100` ($100.00 off) |

| # | Step | Expected result |
|---|---|---|
| 1 | Apply `FREE100` | Discount line shows **−$50.00** (not −$100.00) |
| 2 | Check totals | Subtotal $0.00, tax $0.00, total **$0.00**. No negative numbers anywhere. |
| 3 | Tap **Confirm & Pay** | Booking Confirmed. Payment step receives amount $0.00 (check in network tab or booking API response). |

---

### TC-BOOK-014 · Cancel exactly 24 hours before start → no fee

| | |
|---|---|
| Requirement | REQ-BOOK-005 |
| Priority / Type | High / Boundary |
| Platform | All |
| Preconditions | Customer A has a Confirmed booking that starts in **24h 00m** (create it so the cancel happens on the exact minute; staging lets QA set the booking time) |
| Test data | Booking total $54.00 |

| # | Step | Expected result |
|---|---|---|
| 1 | Open My Bookings → the booking → **Cancel** | Dialog says **"Free cancellation"**. No fee shown. |
| 2 | Tap **Confirm cancel** | Status **Cancelled**. Refund / charge: **$0.00 fee** |

| Notes | The edge of a rule is where `>` vs `>=` mistakes live. Failed in run 1 → [BUG-BOOK-001](../07-bug-reporting/sample-bug-reports.md#bug-book-001) |
|---|---|

---

### TC-BOOK-015 · Cancel under 24 hours → fee shown before confirming

| | |
|---|---|
| Requirement | REQ-BOOK-005 |
| Priority / Type | High / Boundary |
| Platform | All |
| Preconditions | Customer A has a Confirmed booking that starts in **23h 59m** |
| Test data | Booking total $54.00 |

| # | Step | Expected result |
|---|---|---|
| 1 | Open the booking → **Cancel** | Dialog shows fee **$27.00 (50%)** and asks to confirm |
| 2 | Tap **Keep booking** | Dialog closes. Booking still Confirmed. No fee. |
| 3 | Tap **Cancel** again → **Confirm cancel** | Status Cancelled. Fee $27.00 recorded. |

---

### TC-BOOK-018 · Booking times shown in customer's time zone

| | |
|---|---|
| Requirement | REQ-BOOK-007 |
| Priority / Type | High / Edge |
| Platform | All |
| Preconditions | Customer A device time zone EST. Provider time zone PST. |
| Test data | Provider slot 7:00 AM PST = **10:00 AM EST** |

| # | Step | Expected result |
|---|---|---|
| 1 | Open the slot list | Slot shows **10:00 AM EST** |
| 2 | Book it | Success screen shows 10:00 AM EST |
| 3 | Open My Bookings | **10:00 AM EST** |
| 4 | Open confirmation email and push | 10:00 AM EST |

| Notes | Check every screen, not just the first one. Different screens often format time in different code. Failed in run 1 → [BUG-BOOK-003](../07-bug-reporting/sample-bug-reports.md#bug-book-003) |
|---|---|

---

### TC-BOOK-019 · Two customers confirm the same slot at the same moment

| | |
|---|---|
| Requirement | REQ-BOOK-003 |
| Priority / Type | High / Edge |
| Platform | Web + iOS |
| Preconditions | A (web) and B (iOS) on the summary screen for the same slot. Both devices on a slow network (browser throttling "Slow 4G" / iOS Network Link Conditioner). |
| Test data | Slot: tomorrow 2:00 PM. Repeat **5 times** with new slots. |

| # | Step | Expected result |
|---|---|---|
| 1 | A and B tap **Confirm & Pay** at the same time (count down out loud) | Exactly **one** booking Confirmed |
| 2 | Check the other customer's screen | *"This time is no longer available"*, no charge |
| 3 | Check provider's schedule | Only one booking for that slot |

| Notes | Added after [exploratory session ET-BOOK-01](../08-exploratory-testing/sample-session.md) found [BUG-BOOK-004](../07-bug-reporting/sample-bug-reports.md#bug-book-004). Kept for regression. Real load testing is still recommended. |
|---|---|

---

## Compact test cases (simple checks)

| ID | Title | REQ | Preconditions / data | Steps (short) | Expected result | Priority |
|---|---|---|---|---|---|---|
| TC-BOOK-001 | Slot list loads for provider + service | 001 | Customer A logged in | Open provider → Haircut | Slots grouped by day, 45-min slots, only free times | High |
| TC-BOOK-002 | Past slots today are hidden | 001 | Run at 11:30 AM local time | Open today's slots | First slot shown is after 11:30 AM | Medium |
| TC-BOOK-003 | Last day of range: day 14 shown, day 15 not | 001 | Provider has slots every day | Scroll to end of date picker | Last date = today + 13 days; next date not selectable | Medium |
| TC-BOOK-005 | Booking details correct in My Bookings | 002 | After TC-BOOK-004 | Open booking details | Provider, service, date, time with zone, total $54.00, status Confirmed | High |
| TC-BOOK-006 | Booked slot disappears for others | 003 | A booked tomorrow 10:00 AM | B opens same provider, refreshes | 10:00 AM not in B's list | High |
| TC-BOOK-008 | Valid promo code applied | 004 | Summary for Haircut | Apply `SPRING10` | −$5.00, total $48.60 | High |
| TC-BOOK-010 | Expired / unknown code rejected | 004 | Summary for Haircut | Apply `WINTER5`, then `ABC123` | "This code has expired" / "This code is not valid". Total stays $54.00 | Medium |
| TC-BOOK-011 | Only one promo code per booking | 004 | `SPRING10` applied | Try to apply `FREE100` | Message: only one code per booking. Total stays $48.60 | Medium |
| TC-BOOK-013 | Cancel 3 days before → free | 005 | Booking in 3 days | Cancel → confirm | "Free cancellation", status Cancelled, fee $0.00 | High |
| TC-BOOK-016 | Email + push after booking | 006 | Push on | Book a slot, wait | Email and push within 2 min: provider, service, date, time | Medium |
| TC-BOOK-017 | Push off → email still sent | 006 | Push notifications disabled in OS settings | Book a slot | No push, email arrives within 2 min | Medium |

---

## Coverage check

| Requirement | Test cases |
|---|---|
| REQ-BOOK-001 | TC-BOOK-001, 002, 003 |
| REQ-BOOK-002 | TC-BOOK-004, 005 |
| REQ-BOOK-003 | TC-BOOK-006, 007, 019 |
| REQ-BOOK-004 | TC-BOOK-008, 009, 010, 011, 012 |
| REQ-BOOK-005 | TC-BOOK-013, 014, 015 |
| REQ-BOOK-006 | TC-BOOK-016, 017 |
| REQ-BOOK-007 | TC-BOOK-018 |

Every requirement has at least one test case. Full matrix with results and bugs: [traceability](../10-traceability/requirements-traceability-example.md).
