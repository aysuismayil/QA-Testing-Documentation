# Acceptance Criteria Review: Example

**Product:** Demo Booking App (fictional, web + iOS + Android)
**Feature:** Book an appointment
**Release:** 2.4.0

This is the starting point of the QA story in this repository. Every other document (test plan, test cases, bugs, traceability, release decision) uses the requirement IDs created here.

---

## 1. The story as it came into refinement

> **US-BOOK-01**
> As a customer, I want to book a time slot with a service provider so that I can get an appointment without calling.
>
> **Acceptance Criteria**
> 1. Customer can see available times for the next 2 weeks.
> 2. Customer can pick a time and book it.
> 3. A booked time is no longer available.
> 4. Customer can use a promo code.
> 5. Customer can cancel for free up to 24 hours before.
> 6. Customer gets a confirmation.

It reads fine. But almost every line has a hidden question that a developer and a tester could answer differently.

---

## 2. My review notes

| AC | What's unclear | Why it matters | Question I asked |
|---|---|---|---|
| 1 | "Next 2 weeks": does it include today? 14 or 15 days? | Boundary. Dev and QA will test different last days. | Is the range today + 13 days (14 calendar days)? |
| 1 | Are past times today still shown? | User could try to book 9:00 at 11:00. | Should slots earlier than "now" be hidden? |
| 1 | Which time zone are slots shown in? | Customer and provider can be in different zones. | Customer's device time, provider's time, or both? |
| 2 | What does "book it" end with? Status? Where does it show? | We can't check "done" without a visible result. | What status does the booking get, and where does the customer see it? |
| 3 | What if two customers confirm the same slot at the same time? | Double booking = angry customer + angry provider. | Who wins? What does the second customer see? |
| 4 | One code or several? Case-sensitive? Spaces? Expired code? | Codes are copied from emails, often with spaces. | Rules for case, spaces, expiry, and more than one code? |
| 4 | Discount on what amount? Can total go below zero? | Money. Wrong math = real loss or complaints. | Before or after tax? What if discount > price? |
| 5 | "Up to 24 hours": is exactly 24:00 free or paid? | Classic boundary. Easy to code as `>` instead of `>=`. | Is a cancel at exactly 24h 00m before start free? |
| 5 | What happens under 24 hours? | Missing rule = dev decides alone. | Is there a fee? Is it shown before the user confirms? |
| 6 | Confirmation by what? How fast? | Push may be turned off. | Email, push, or both? What if push is disabled? |
| - | Web and mobile both in scope? | Different bugs per platform. | Same rules on web, iOS and Android? |

**Not a question, but a risk I flagged:** AC 3 and AC 5 involve money and trust. I asked for them to be treated as high priority in testing.

---

## 3. Revised requirements (after the refinement meeting)

These are the rules everyone agreed on. Each one has an ID so it can be traced.

| ID | Requirement |
|---|---|
| **REQ-BOOK-001** | Customer sees available slots for the selected provider and service for **today + the next 13 days** (14 calendar days). Slots earlier than the current time are hidden. |
| **REQ-BOOK-002** | Customer selects one slot and taps **Confirm & Pay**. The booking gets status **Confirmed** and appears in **My Bookings**. |
| **REQ-BOOK-003** | A confirmed slot cannot be booked by anyone else. If two customers confirm the same slot at the same time, only the first succeeds. The second sees *"This time is no longer available"* and the slot list refreshes. |
| **REQ-BOOK-004** | Customer can apply **one** promo code per booking. Codes are **not case-sensitive**. Spaces before/after the code are **ignored**. Expired or unknown codes show a clear message. Discount applies to the service price **before tax**. The total can't go below $0.00. |
| **REQ-BOOK-005** | Cancellation is **free when it is 24 hours or more** before the start time (exactly 24:00 is free). Under 24 hours, a **50% fee** applies and is shown **before** the customer confirms the cancellation. |
| **REQ-BOOK-006** | After booking, the customer gets a **confirmation email and a push notification within 2 minutes**. If push is disabled, the email is still sent. |
| **REQ-BOOK-007** | All booking times are shown in the **customer's device time zone**, with the time zone label (example: *2:00 PM EST*). |

**Out of scope for this story** (agreed in the meeting):
- Payment processing itself (owned by the Payments team; we only check the amount sent to the payment step).
- Rescheduling (separate story, next release).

---

## 4. What changed because of the review

| Before review | After review |
|---|---|
| "Next 2 weeks" | Exact range: today + 13 days |
| No rule for double booking | First confirm wins, second gets a clear message |
| "Can use a promo code" | 5 clear rules: one code, case, spaces, expiry, $0 floor |
| "Up to 24 hours" | Exactly 24:00 is free, fee shown before confirming |
| "Gets a confirmation" | Email + push, 2 minutes, email always sent |
| Time zone not mentioned | New requirement REQ-BOOK-007 |

Four of these questions later turned into defects found in testing (see [sample bug reports](../07-bug-reporting/sample-bug-reports.md)). The rule was clear, so the bugs were easy to prove and fast to fix. Nobody had to argue about what "correct" meant.

---

## Where this goes next

- Test approach: [sample-testing-approach.md](../02-test-approach/sample-testing-approach.md)
- Test plan: [sample-test-plan.md](../01-test-planning/sample-test-plan.md)
- Traceability: [requirements-traceability-example.md](../10-traceability/requirements-traceability-example.md)
