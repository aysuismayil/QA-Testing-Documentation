# 10 · Traceability

Traceability means you can follow a line from a **requirement** to its **test cases**, their **results**, and any **bugs**, and back again.
It answers questions like:

- "Did we test everything in the story?"
- "This requirement changed. What tests do we need to update?"
- "This bug: which rule does it break?"
- "Are we ready to release? What's not covered?"

## When QA uses it

- While writing test cases: to spot requirements with no tests.
- Before a release: to show coverage and known gaps.
- When requirements change mid-sprint.
- In regulated or audited projects, where it's required.

## Files in this folder

| File | Use it for |
|---|---|
| [requirements-traceability-example.md](requirements-traceability-example.md) | Full matrix for the booking feature: REQ → TS → TC → result → bug, plus the reverse view |

## Minimal columns that are enough

| Requirement | Test cases | Latest result | Bugs | Covered? |
|---|---|---|---|---|

Add risk and scenarios when you have them. Don't add columns nobody reads.

## Tips

- Use **IDs everywhere** (REQ-, TC-, BUG-). Titles change, IDs don't.
- Most test management tools and Jira can link these for you. The matrix can be an export, not manual work.
- "Covered" isn't always yes/no. Write **partly** and say what is missing.

## Common mistakes

- Matrix created at the end just for show, never used to find gaps.
- Requirements without IDs, so nothing can be linked.
- Saying "100% covered" when edge cases or platforms were not tested.
