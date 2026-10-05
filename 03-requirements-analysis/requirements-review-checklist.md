# Requirements Review Checklist

Use this when a user story or spec arrives for refinement, **before** development starts.
Go through it in 10–15 minutes. Write your questions down, then bring them to the refinement meeting or post them on the ticket.

> Tip: You don't need an answer to every line. You need to know which lines are **not** answered.

---

## 1. Goal and users

- [ ] I can explain in one sentence **why** this feature exists (business goal).
- [ ] I know **who** uses it (roles: customer, admin, guest, provider...).
- [ ] I know what happens if this feature fails. (Lost money? Lost data? Just annoying?)

## 2. Acceptance Criteria quality

- [ ] Each AC is **pass/fail**. No words like "fast", "easy", "user-friendly", "should work well" without a number or rule.
- [ ] Each AC has a **visible result** I can check (a status, a message, a screen, a record).
- [ ] There is no AC that two people could read in two different ways.

## 3. Rules and data

- [ ] Field rules are written: required/optional, format, min/max length.
- [ ] **Boundaries** are clear: is the limit included (`>=`) or not (`>`)?
- [ ] Dates and times: which **time zone**? Is "today" included in a range?
- [ ] Money: rounding, currency, tax, discounts, can a total be zero or negative?
- [ ] Case-sensitivity and extra spaces for text that users copy-paste (codes, emails).

## 4. Unhappy paths

- [ ] What error does the user see for **invalid input**? (exact message if possible)
- [ ] What happens on **no results / empty state**?
- [ ] What happens on **network loss, timeout, server error**?
- [ ] What happens if the user **goes back, refreshes, or closes the app** in the middle?

## 5. More than one user / more than one action

- [ ] Two users acting on the **same item at the same time** (same slot, same stock, same seat).
- [ ] Same user on **two devices or two tabs**.
- [ ] **Double tap / double click** on the main button.

## 6. Platforms and states

- [ ] Web, iOS, Android: same rules? Any differences written down?
- [ ] Logged in vs. guest. New user vs. returning user.
- [ ] Permissions: notifications, location, camera turned **off**.

## 7. Dependencies and scope

- [ ] Other teams or third parties involved (payments, email, maps)? Who tests that part?
- [ ] What is clearly **out of scope**? Is it written down?
- [ ] Is there a design (mockup) and does it match the AC?

## 8. Non-functional (only what matters for this feature)

- [ ] Any speed expectation? (example: "shown within 2 seconds")
- [ ] Accessibility for new UI: labels, contrast, screen reader.
- [ ] Security basics: who can see or change this data?

---

## Question formats that work

Short, specific, with an example. Easy to answer with one word.

| Weak question | Better question |
|---|---|
| "What about edge cases?" | "If the user cancels at exactly 24h 00m before start, is it free or paid?" |
| "Is validation defined?" | "Promo code `spring10` vs `SPRING10`: should both work?" |
| "What about errors?" | "If payment fails after the slot is held, is the slot released right away?" |
| "Will it work on mobile?" | "Are the iOS and Android rules the same as web, or is anything different?" |

---

## Common mistakes

- Reviewing only the happy path.
- Asking questions **after** the build is ready. By then the answer costs a code change.
- Accepting "we'll figure it out later" for money, time, or permission rules.
- Not writing the final answer back into the ticket. A rule agreed only in a meeting gets lost.
- Turning the review into a list of 40 questions. Prioritize: money, data, security, and main flow first.

---

See it used: [acceptance-criteria-review-example.md](acceptance-criteria-review-example.md)
