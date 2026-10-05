# Severity vs. Priority

| | Severity | Priority |
|---|---|---|
| Question | **How bad** is the impact? | **How soon** must we fix it? |
| Based on | Effect on users, data, money, security | Business: users affected, deadlines, campaigns, workaround |
| Usually set by | QA | Product owner (QA suggests) |
| Changes over time? | Rarely | Often (a campaign starts, a release date moves) |

They are related, but **not the same**. Keep them in separate fields.

---

## A simple severity scale

| Severity | Meaning | Example |
|---|---|---|
| **Critical** | Main flow broken, data loss, money or security problem, no workaround | Two customers booked into the same slot |
| **High** | Important feature wrong, workaround is hard or unknown to users | Late fee charged when cancel should be free |
| **Medium** | Feature partly wrong, easy workaround | Filter resets after going back |
| **Low** | Cosmetic or small inconvenience | Typo, misaligned icon, pasted promo code needs retyping |

## A simple priority scale

| Priority | Meaning |
|---|---|
| **P1** | Fix now / blocks release |
| **P2** | Fix in this release or the next small one |
| **P3** | Fix when there's capacity |
| **P4** | Nice to have |

---

## The four combinations (with realistic examples)

| | **High priority** | **Low priority** |
|---|---|---|
| **High severity** | Payment charged twice on retry. Fix now. | App crashes on an old OS version used by very few customers, and support for that version ends next month. Severe for those users, but the business plans to drop it. |
| **Low severity** | Company name misspelled on the home page before a big launch. Small defect, very visible. | Tooltip text cut off on one rarely used admin screen. |

Demo Booking App example: **BUG-BOOK-002** (promo code with spaces) is **Low severity** but **P2**, because a marketing email with a copy button is going out soon. See [sample-bug-reports.md](../07-bug-reporting/sample-bug-reports.md#bug-book-002).

---

## How to choose severity fast

Ask in this order. Stop at the first "yes".

1. Can users lose money, data, or access, or is security affected? → **Critical / High**
2. Is the main flow blocked with no workaround? → **Critical**
3. Is an important feature wrong, but users can get around it? → **High / Medium**
4. Is it only how it looks or a small annoyance? → **Low**

## Interview answer (short)

> "Severity is how bad the bug is for the user or the system. Priority is how fast the business needs it fixed. I set severity based on impact, and suggest priority, but the product owner decides it because it depends on things like deadlines and how many users are affected. For example, a typo in the company name on the home page is low severity but high priority."

## Common mistakes

- Making every bug Critical. Then nothing is.
- Priority = severity automatically.
- Not updating priority when the business situation changes.
- QA deciding priority alone without the product owner.
