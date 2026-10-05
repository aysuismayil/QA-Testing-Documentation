# 09 · Test Execution

Execution is running the tests and **recording results so others can trust them**.
A result without a build number, platform, or bug link is just an opinion.

## When QA does it

- After entry criteria are met (build on the environment, smoke passed).
- Again after fixes (retest) and around changed code (regression).

## Files in this folder

| File | Use it for |
|---|---|
| [execution-results-example.md](execution-results-example.md) | Two runs on two builds: failures linked to bugs, blocked vs. failed, retests, final numbers |

## Result statuses

| Status | Use when | Don't use when |
|---|---|---|
| **Pass** | Every expected result matched | You only checked part of it |
| **Fail** | The product did not match the expected result. Link a bug. | The environment was broken |
| **Blocked** | You **couldn't** run it (environment down, other bug blocks the path, no test data). Write why. | The product is wrong (that's Fail) |
| **Not run** | Not executed yet, or skipped by decision. Write why. | |

## Good habits during execution

- Record the **build number** for every run.
- Record **platform** when you test more than one.
- One failed test case → link the bug ID right away.
- Retest on the build that **contains the fix**, check the release notes.
- After a fix, rerun nearby cases too, not just the failed one.
- Keep notes short in the comment column: what you saw, not a story.

## Common mistakes

- Marking a case Failed because staging was down. That's Blocked.
- Pass rate without saying how many were executed.
- Rerunning only the failed case after a fix.
- Results only in your head or in chat messages.
