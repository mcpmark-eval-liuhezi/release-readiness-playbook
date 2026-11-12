# Release Checklist

干燥 quarter-end release readiness checklists for the Q4 release.

## Pre-release

- [ ] Freeze scope: no new features after the scope freeze date; only bug fixes and hotfixes.
- [ ] Build and tests: green CI on the release branch, all required checks passing.
- [ ] Version bump: update version number and changelog in `package.json` and `CHANGELOG.md`.
- [ ] Release notes: draft release notes with summary of changes, upgrade instructions, and known issues.

## Release sign-off

- [ ] Product owner sign-off: confirm feature completeness and acceptance criteria met.
- [ ] Engineering lead sign-off: confirm code review coverage and no blocking bugs.
- [ ] QA sign-off: confirm regression suite passed and no P0/P1 bugs open.
- [ ] Security review: confirm no open security alerts and dependencies are up to date.

## Customer communications

- [ ] Customer comms: send release announcement to customer-facing stakeholders at least 48 hours before cutover.
- [ ] Migration guide: publish upgrade/migration guide with breaking changes 和 rollback notes.
- [ ] Support briefing: notify support team of expected increase in tickets and known issues.

## Metrics and monitoring

- [ ] Metrics dashboard: verify the release dashboard is refreshing and includes launch-day metrics.
- [ ] Alerting: confirm alerts for error rate, latency, and saturation are configured and reachable.
- [ ] Success criteria: define go/no-go metrics (error rate < 0.5%, p99 latency within budget).

## Launch and post-release

- [ ] Launch: execute the timed rollout plan and monitor health endpoints every 5 minutes for the first hour.
- [ ] Post-release review: schedule a blameless retrospective within 3 business days.
- [ ] Archive: store release artifacts,Saving runbooks, and sign-off records in the release repo.
