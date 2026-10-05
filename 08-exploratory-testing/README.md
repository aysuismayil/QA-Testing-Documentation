# 08 · Exploratory Testing

Exploratory testing finds the bugs that nobody thought to write a test case for.
It's not random clicking: you have a **charter** (goal), a **time box**, and you take **notes**.

## When QA uses it

- On new or high-risk features, next to scripted test cases.
- When requirements are thin and you need to learn the product fast.
- For timing, interruptions, two-user and "weird but real" situations.
- After a big fix, to look around the changed area.

## Files in this folder

| File | Use it for |
|---|---|
| [exploratory-testing-charter-template.md](exploratory-testing-charter-template.md) | Charter, notes table, summary, idea starters |
| [sample-session.md](sample-session.md) | 90-minute session ET-BOOK-01 that found the double-booking bug (BUG-BOOK-004) |

## Scripted vs. exploratory

| Scripted test cases | Exploratory testing |
|---|---|
| Check known rules | Discover unknown problems |
| Same steps every time | Next step depends on what you just saw |
| Great for regression | Great for new and risky areas |
| Pass / Fail | Notes, bugs, questions, new test ideas |

You need both. In the sample, scripted TC-BOOK-007 passed, but the exploratory session found BUG-BOOK-004 by changing the timing and network.

## Common mistakes

- No written result. Nobody knows what was covered.
- Exploring only the happy path.
- Not turning important findings into regression test cases.
- Session too long with no breaks. 60–90 minutes is enough.
