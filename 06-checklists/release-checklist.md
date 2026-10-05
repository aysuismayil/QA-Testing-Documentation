# Release Checklist (QA Side)

Use it in the last days before a release. It makes sure nothing is forgotten between "testing is done" and "users have the new version".

---

## Before the Go / No-Go meeting

- [ ] All planned test cases executed (or skipped **with a written reason**)
- [ ] All Critical / High bugs fixed **and verified on the release build**
- [ ] Open bugs reviewed: each has severity, priority, workaround, owner and decision (fix now / accept / defer)
- [ ] Regression done on the release candidate build
- [ ] Smoke passed on the release candidate build
- [ ] Release notes checked: every fixed bug listed is really fixed; nothing missing
- [ ] Test summary / release readiness report sent
- [ ] Known risks and gaps written in the report

## Release build checks

- [ ] Version / build number is the one that was tested
- [ ] Feature flags / config set correctly for production (new feature on or off as planned)
- [ ] Test-only settings are **not** in the build (test promo codes, debug menus, test endpoints)
- [ ] Mobile: store listing text and screenshots match (if changed)
- [ ] Mobile: minimum OS version is correct

## Right after release

- [ ] Production smoke
- [ ] New feature checked on production once
- [ ] Watch error logs / crash reports for the first hours (with dev)
- [ ] Support team knows about new features and known issues + workarounds
- [ ] Clean up test data on production

## After the release (next days)

- [ ] Deferred bugs are in the next sprint backlog
- [ ] Bugs that escaped to production → add a test case to regression
- [ ] Short retro note: what helped, what to change next time

---

## Demo Booking App 2.4.0: items that mattered

| Item | Why |
|---|---|
| Test promo code `FREE100` disabled on production | It was a staging-only code for the $0.00 boundary test |
| Support note for BUG-BOOK-002 | Users pasting promo codes with spaces |
| Watch duplicate bookings for 1 week | Load was not tested |

## Common mistakes

- Verifying fixes on a different build than the one that ships.
- Leaving test data or test codes active in production.
- No one watching logs after release ("QA is done").
- Support learning about a known issue from an angry customer.
