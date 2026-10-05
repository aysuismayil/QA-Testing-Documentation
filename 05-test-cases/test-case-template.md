# Test Case Template

Two formats. Use the **full** format for important or tricky checks. Use the **compact** format for simple ones.
Both work in a spreadsheet, a test management tool, or Markdown.

---

## Full format

| Field | Value |
|---|---|
| **ID** | TC-[AREA]-[NNN] |
| **Title** | *[Action] + [condition] + [expected outcome]* |
| **Requirement** | REQ-... |
| **Priority** | High / Medium / Low |
| **Type** | Positive / Negative / Boundary / Edge |
| **Platform** | Web / iOS / Android / All |
| **Preconditions** | *State that must be true before step 1 (logged in, data exists...)* |
| **Test data** | *Exact values: accounts, codes, dates, amounts* |

| # | Step | Expected result |
|---|---|---|
| 1 | | |
| 2 | | |
| 3 | | |

| **Notes** | *Anything a new tester needs to know: why this case exists, known limits* |
|---|---|

---

## Compact format

| ID | Title | REQ | Preconditions / data | Steps (short) | Expected result | Priority |
|---|---|---|---|---|---|---|
| | | | | | | |

---

## Writing rules that keep test cases useful

- **Title tells the story.** "Cancel exactly 24h before start → no fee" beats "Cancellation test 3".
- **One goal per test case.** If it can fail for two unrelated reasons, split it.
- **Exact data.** "Use a valid code" → which one? Write `SPRING10`.
- **Expected result is checkable.** Not "works correctly" but "Status shows *Confirmed*, total is $48.60".
- **Steps a new person can follow** without asking you.
- **Don't write a test case for every label and button.** Simple UI checks can go into the expected result of a real scenario.
- **Write it so it can be reused in regression.** Avoid "today's date"-style data that breaks next month; describe how to create it instead.

## Common mistakes

| Mistake | Example | Better |
|---|---|---|
| Vague expected result | "Promo code works" | "Discount line shows −$5.00, total $48.60" |
| Missing preconditions | Step 1: "Open My Bookings" | Precondition: "Customer has 1 confirmed booking for tomorrow" |
| Steps mixed with checks | "Click Confirm and check status and email" | Separate steps, one expected result each |
| Hidden test data | "Log in as test user" | "Log in as Customer A (`customer.a@example.test`)" |
| Too many cases | 30 cases for one form | Group by business scenario, keep targeted negatives |

See examples: [sample-test-cases.md](sample-test-cases.md)
