# Test Scenarios: Book an Appointment (Sample)

**Product:** Demo Booking App 2.4.0 (fictional)
**Source:** REQ-BOOK-001 to 007 ([requirements review](../03-requirements-analysis/acceptance-criteria-review-example.md)) and the [risk map](../02-test-approach/sample-testing-approach.md#3-risk-map)

A scenario is **one line**: what situation we check. Steps come later, in test cases.
Not every scenario becomes a test case. Some are better covered by exploratory testing or a checklist. The last column shows where each one went.

Type: **P** positive · **N** negative · **B** boundary · **E** edge case

---

## REQ-BOOK-001 · Slot list

| ID | Scenario | Type | Priority | Covered by |
|---|---|---|---|---|
| TS-BOOK-01 | Customer sees available slots for the selected provider and service | P | High | TC-BOOK-001 |
| TS-BOOK-02 | Slots earlier than the current time today are not shown | B | Medium | TC-BOOK-002 |
| TS-BOOK-03 | Day 14 (today + 13) is shown, day 15 is not | B | Medium | TC-BOOK-003 |
| TS-BOOK-04 | Provider with no free slots shows an empty state, not a blank screen | N | Low | Exploratory |

## REQ-BOOK-002 · Booking confirm

| ID | Scenario | Type | Priority | Covered by |
|---|---|---|---|---|
| TS-BOOK-05 | Customer books an available slot and gets status Confirmed | P | High | TC-BOOK-004 |
| TS-BOOK-06 | New booking shows in My Bookings with correct provider, service, date, time, price | P | High | TC-BOOK-005 |
| TS-BOOK-07 | Customer double-taps **Confirm & Pay**: only one booking is created | E | High | Exploratory |
| TS-BOOK-08 | App goes to background or network drops during confirm: no "half" booking | E | Medium | Exploratory |

## REQ-BOOK-003 · No double booking

| ID | Scenario | Type | Priority | Covered by |
|---|---|---|---|---|
| TS-BOOK-09 | Slot booked by Customer A no longer appears for Customer B | P | High | TC-BOOK-006 |
| TS-BOOK-10 | Customer B confirms a slot that A booked a few seconds earlier (B's list was old) | N | High | TC-BOOK-007 |
| TS-BOOK-11 | A and B confirm the same slot at the same moment | E | High | Exploratory → TC-BOOK-019 |

## REQ-BOOK-004 · Promo code

| ID | Scenario | Type | Priority | Covered by |
|---|---|---|---|---|
| TS-BOOK-12 | Valid code gives the right discount before tax | P | High | TC-BOOK-008 |
| TS-BOOK-13 | Code works in lower/mixed case and with spaces before/after | E | Medium | TC-BOOK-009 |
| TS-BOOK-14 | Expired code shows "This code has expired" | N | Medium | TC-BOOK-010 |
| TS-BOOK-15 | Unknown code shows "This code is not valid" | N | Low | TC-BOOK-010 (same steps, second data row) |
| TS-BOOK-16 | Second code can't be added on top of the first | N | Medium | TC-BOOK-011 |
| TS-BOOK-17 | Discount equal to or bigger than price → total is $0.00, not negative | B | Medium | TC-BOOK-012 |

## REQ-BOOK-005 · Cancellation

| ID | Scenario | Type | Priority | Covered by |
|---|---|---|---|---|
| TS-BOOK-18 | Cancel 3 days before → free | P | High | TC-BOOK-013 |
| TS-BOOK-19 | Cancel at **exactly 24h 00m** before → free | B | High | TC-BOOK-014 |
| TS-BOOK-20 | Cancel at 23h 59m before → 50% fee shown **before** confirming | B | High | TC-BOOK-015 |
| TS-BOOK-21 | Cancel an already cancelled booking (second tab / old screen) | N | Low | Regression checklist |

## REQ-BOOK-006 · Confirmation

| ID | Scenario | Type | Priority | Covered by |
|---|---|---|---|---|
| TS-BOOK-22 | Email and push arrive within 2 minutes with correct details | P | Medium | TC-BOOK-016 |
| TS-BOOK-23 | Push turned off → email still arrives | N | Medium | TC-BOOK-017 |

## REQ-BOOK-007 · Time zone

| ID | Scenario | Type | Priority | Covered by |
|---|---|---|---|---|
| TS-BOOK-24 | Customer (EST) and provider (PST): all screens show customer's time with label | E | High | TC-BOOK-018 |
| TS-BOOK-25 | Customer changes device time zone after booking: My Bookings updates | E | Low | Planned: ET-BOOK-02 (not tested yet) |

---

## How these were built

1. One requirement at a time. First the normal case (P).
2. Then: what can the user do wrong? (N)
3. Then: where are the limits? Test exactly on the limit and one step past it. (B)
4. Then: what about timing, order, two users, interruptions? (E)
5. Priority comes from the risk map, not from the type.

## Common mistakes

- Writing steps inside scenarios. Keep it to one line.
- Only positive scenarios.
- No link back to the requirement, so gaps are invisible.
- Turning every scenario into a test case. Some are cheaper and better as exploratory ideas.
