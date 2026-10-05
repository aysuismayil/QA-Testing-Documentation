# Exploratory Testing Charter Template

Exploratory testing is testing **without a script, but with a goal**. You learn, design and run tests at the same time.
A charter keeps the session focused, and notes make it reviewable.

A simple charter format:

> **Explore** *(target)* **with** *(resources, tools, data)* **to discover** *(what kind of information/risk)*

This charter format comes from Elisabeth Hendrickson's book *Explore It!* (Pragmatic Bookshelf, 2013).

---

## Charter

| | |
|---|---|
| Session ID | ET-[AREA]-[NN] |
| Explore | *Feature or flow* |
| With | *Accounts, devices, tools, data, conditions (slow network, 2 users...)* |
| To discover | *Risk you're looking for: data problems, timing issues, error handling...* |
| Time box | *60–90 min is a good size* |
| Build / environment | |
| Tester | |

## Test ideas to start with

*5–10 ideas. You don't have to do all of them. New ideas will appear during the session.*

- 
- 

## Session notes

| # | What I tried | What happened | Follow-up |
|---|---|---|---|
| 1 | | | *None / Bug ID / Question / New test case* |

## Session summary

| | |
|---|---|
| Time spent | *setup / testing / bug investigation* |
| Bugs filed | |
| Questions raised | |
| New test cases suggested | |
| Areas not covered | *What you didn't get to; maybe the next charter* |
| Overall feeling about this area | *Solid / some concerns / risky* |

---

## Useful idea starters

| Idea | Example |
|---|---|
| Interrupt it | Background the app, lock the phone, lose network in the middle |
| Repeat it fast | Double tap, tap again during loading |
| Go back | Browser back, Android back, swipe back, then forward |
| Two of something | Two users, two tabs, two devices, same account |
| Change something in the middle | Change price, time zone, permission while the flow is open |
| Wrong order | Do step 3 before step 2 (deep links, saved URLs) |
| Weird but real data | Spaces, emoji, long names, other languages |
| Boundaries in time | Midnight, end of month, daylight saving change |

## Common mistakes

- No charter = random clicking, and nothing to report at the end.
- No notes. If it isn't written, nobody can see the value of the session.
- Charter too big ("explore the whole app").
- Finding a bug and spending the rest of the session on it. File it, note it, continue.
