# Sample Bug Reports: Demo Booking App 2.4.0

> Fictional bugs for a fictional app. Each one connects to a requirement and a test case, so you can follow it through the whole cycle.

| ID | Title | Severity | Priority | Found by | Final status |
|---|---|---|---|---|---|
| BUG-BOOK-001 | Late fee charged when cancelling exactly 24h before start | High | P1 | TC-BOOK-014 | Fixed, verified |
| BUG-BOOK-002 | Valid promo code rejected when it has a space before/after | Low | P2 | TC-BOOK-009 | Open, deferred to 2.4.1 |
| BUG-BOOK-003 | My Bookings shows provider's time zone instead of customer's | High | P1 | TC-BOOK-018 | Fixed, verified |
| BUG-BOOK-004 | Two customers can book the same slot when they confirm at the same moment | Critical | P1 | Exploratory ET-BOOK-01 | Fixed, verified |

---

<a id="bug-book-001"></a>
## BUG-BOOK-001 · [Cancellation] Late fee charged when cancelling exactly 24h before start

| Field | Value |
|---|---|
| Environment | Staging |
| Build | 2.4.0 (212) |
| Platform | Web (Chrome), iOS · same result |
| Account | Customer A |
| Severity | **High**: customer is charged money they should not pay |
| Priority | **P1**: affects a common action; refunds + support tickets |
| Frequency | Always (4/4) |
| Requirement | REQ-BOOK-005 |
| Test case | TC-BOOK-014 |

**Preconditions**
Customer A has a Confirmed booking (Haircut, total $54.00) that starts in exactly 24h 00m.

**Steps to reproduce**
1. Log in as Customer A.
2. Open **My Bookings** → select the booking.
3. Tap **Cancel**.

**Expected result**
Dialog shows "Free cancellation". REQ-BOOK-005: *"exactly 24:00 is free"*.

**Actual result**
Dialog shows "Late cancellation fee: $27.00". After confirming, the fee is recorded on the booking.

**Evidence**
- Screenshot of the cancel dialog with booking start time and device clock visible.
- At 24h 01m before start: free (correct). At 24h 00m: fee (wrong). At 23h 59m: fee (correct).

**Workaround**
Cancel at least one minute earlier. Users can't know this.

**Notes**
Only the exact boundary minute fails. Same result on web and iOS.

---

<a id="bug-book-002"></a>
## BUG-BOOK-002 · [Promo code] Valid code rejected when it has a space before/after

| Field | Value |
|---|---|
| Environment | Staging |
| Build | 2.4.0 (212) |
| Platform | Web (Chrome, Safari), Android · same result |
| Account | Customer A |
| Severity | **Low**: user can retype the code and continue |
| Priority | **P2**: next spring campaign email has a copy button; many users will paste |
| Frequency | Always (3/3) |
| Requirement | REQ-BOOK-004 |
| Test case | TC-BOOK-009 |

**Preconditions**
Customer A is on the booking summary for Haircut ($50.00).

**Steps to reproduce**
1. Tap **Add promo code**.
2. Enter ` SPRING10 ` (one space before and one after).
3. Tap **Apply**.

**Expected result**
Code accepted, discount −$5.00. REQ-BOOK-004: *"Spaces before/after the code are ignored."*

**Actual result**
Message "This code is not valid". No discount.

**Evidence**
- Screen recording: pasting the code, error shown, then the same code typed without spaces is accepted.
- Lower case `spring10` without spaces: **accepted** (case rule works). Only spaces fail.

**Workaround**
Delete the spaces and apply again.

**Notes**
This is a good example of **low severity, but not low priority**: the impact per user is small, but marketing traffic makes it frequent.

---

<a id="bug-book-003"></a>
## BUG-BOOK-003 · [My Bookings] Booking time shown in provider's time zone instead of customer's

| Field | Value |
|---|---|
| Environment | Staging |
| Build | 2.4.0 (212) |
| Platform | iOS and Android. **Web is correct.** |
| Account | Customer A (device time zone EST), Provider in PST |
| Severity | **High**: customer can arrive 3 hours late and miss the appointment |
| Priority | **P1** |
| Frequency | Always (3/3) |
| Requirement | REQ-BOOK-007 |
| Test case | TC-BOOK-018 |

**Preconditions**
Customer device time zone = EST. Provider = PST.

**Steps to reproduce**
1. On iOS, open the provider and select the slot shown as **10:00 AM EST**.
2. Tap **Confirm & Pay**.
3. Open **My Bookings**.

**Expected result**
My Bookings shows **10:00 AM EST** (same as slot list and success screen).

**Actual result**
My Bookings shows **7:00 AM**, no time zone label.

**Evidence**
- 3 screenshots side by side: slot list (10:00 AM EST), success screen (10:00 AM EST), My Bookings (7:00 AM).
- Booking API response returns the same start time for all three screens, so the data is the same, only the display differs.

**Workaround**
Check the confirmation email (shows the correct time).

**Notes**
Slot list and success screen are correct. Only My Bookings is wrong, on mobile only.

---

<a id="bug-book-004"></a>
## BUG-BOOK-004 · [Booking] Two customers can book the same slot when they confirm at the same moment

| Field | Value |
|---|---|
| Environment | Staging |
| Build | 2.4.0 (212) |
| Platform | Customer A on web (Chrome), Customer B on iOS |
| Network | Both throttled to a slow connection |
| Severity | **Critical**: two customers, one appointment; breaks the main promise of the app |
| Priority | **P1**: release blocker |
| Frequency | Sometimes (2/5) |
| Requirement | REQ-BOOK-003 |
| Found in | Exploratory session [ET-BOOK-01](../08-exploratory-testing/sample-session.md) |

**Preconditions**
Customer A (web) and Customer B (iOS) are both on the booking summary for the **same** free slot. Both devices use a slow network (Chrome DevTools throttling "Slow 4G"; iOS Network Link Conditioner).

**Steps to reproduce**
1. Count down and tap **Confirm & Pay** on both devices at the same moment.
2. Check both success screens.
3. Check the provider schedule for that slot.

**Expected result**
Only one booking is Confirmed. The other customer sees *"This time is no longer available"* and is not charged. (REQ-BOOK-003)

**Actual result**
In 2 of 5 tries, **both** customers see "You're booked!" and both bookings appear as Confirmed on the provider schedule for the same time.

**Evidence**
- Two screen recordings started at the same time (web + iOS).
- Provider schedule screenshot with two Confirmed bookings in one slot.
- Booking IDs of both duplicate bookings (test data only).

**Workaround**
None for customers. Provider would have to call one customer and cancel.

**Notes**
- With a normal network, 0 of 5 tries reproduced it. Slow network makes the timing window bigger.
- "One after the other" (TC-BOOK-007) passes. Only the "same moment" case fails.
- After this bug, TC-BOOK-019 was added to the regression suite.
