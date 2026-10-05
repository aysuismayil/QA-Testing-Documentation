# Test Summary / Release Readiness Template

Send this before the Go / No-Go meeting. The first section should be enough for a busy manager. The rest is proof.

---

# Test Summary: *[Product] [Version]*

## 1. Recommendation

**GO / GO with known issues / NO-GO**

*2–3 sentences: why. Name the main risks in plain words.*

## 2. Scope tested

| Area | Requirements | Tested on |
|---|---|---|
| | | |

**Not tested:** *list + reason*

## 3. Results

| Total test cases | Pass | Fail | Blocked | Not run |
|---|---|---|---|---|
| | | | | |

| Other activity | Result |
|---|---|
| Smoke on release candidate | |
| Regression | |
| Exploratory sessions | |

## 4. Bugs

| Severity | Found | Fixed + verified | Open |
|---|---|---|---|
| Critical | | | |
| High | | | |
| Medium | | | |
| Low | | | |

### Open bugs going to production

| Bug | Severity / priority | User impact | Workaround | Accepted by | Fix planned |
|---|---|---|---|---|---|
| | | | | | |

## 5. Exit criteria check

| Criterion (from test plan) | Met? | Comment |
|---|---|---|
| | ✅ / ❌ / ⚠️ | |

## 6. Risks and gaps

| Risk / gap | Why it remains | Suggested action |
|---|---|---|
| | | |

## 7. After release

- [ ] Smoke on production right after deploy
- [ ] *Monitoring / support notes / follow-up tickets*

---

## Common mistakes

- Only numbers, no recommendation. QA should give a clear opinion; the business makes the final call.
- Hiding open bugs or gaps to look good. It always comes back.
- "Accepted" known issues without a name and a fix plan.
- Writing a 5-page report for a small release. Match the size to the risk.
