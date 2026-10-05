# Bug Report Template

Copy this into Jira, GitHub Issues, or any tracker. Field names can change per team. The content shouldn't.

---

**Title:** *[Area] What is wrong + when it happens*

| Field | Value |
|---|---|
| ID | BUG-[AREA]-[NNN] |
| Environment | *QA / Staging / Production* |
| Build / version | *e.g. 2.4.0 (212)* |
| Platform / device / OS / browser | |
| Account / role | *e.g. Customer, test account A* |
| Severity | Critical / High / Medium / Low |
| Priority | P1 / P2 / P3 / P4 |
| Frequency | *Always (5/5) · Sometimes (2/5) · Once* |
| Linked requirement | REQ-... |
| Linked test case | TC-... |

**Preconditions**
*What must be true before step 1.*

**Steps to reproduce**
1.
2.
3.

**Expected result**
*What should happen. Quote the requirement if possible.*

**Actual result**
*What happens. Exact message, exact number.*

**Evidence**
*Screenshot, screen recording, console/network log, API response. Mark what to look at.*

**Workaround**
*Is there a way for users to get around it? "None" is a valid answer.*

**Notes**
*Extra facts you checked: other platforms, other builds, when it started. Facts only. No guessing about the code.*

---

## Title formula

`[Area] + what's wrong + condition`

| Weak | Strong |
|---|---|
| Cancel bug | [Cancellation] Late fee charged when cancelling exactly 24h before start |
| Promo not working | [Promo code] Valid code rejected when pasted with a space at the end |
| Wrong time | [My Bookings] Booking time shown in provider's time zone instead of customer's |

## Severity vs. priority (short)

- **Severity** = how bad the impact is for the user/system. QA sets it.
- **Priority** = how soon it must be fixed. Usually product owner decides, QA suggests.

Full guide: [severity-vs-priority.md](../12-qa-reference/severity-vs-priority.md)

## Before you click "Create"

- [ ] I reproduced it at least twice (or wrote "Once" in frequency)
- [ ] I searched for duplicates
- [ ] Steps start from a clear state (not "continue from before")
- [ ] Expected result is based on a requirement, design, or clear common sense (and I said which)
- [ ] One bug per report
- [ ] Evidence is attached and test data is not real customer data
- [ ] Anything I didn't check is written as "Not checked", not guessed

## Common mistakes

- Two problems in one report. One gets fixed, the ticket gets closed, the other is lost.
- "Doesn't work" as the actual result.
- Guessing the cause ("backend bug") instead of describing behavior.
- Severity based on how annoyed you are, not on impact.
- No build number, so dev tests on a different build and says "can't reproduce".
