# Rollback Plan

This plan defines the steps to revert the Q4 release if production health metrics breach agreed thresholds.

## Rollback triggers

- Error rate exceeds 2% for more than 10 minutes.
- p99 latency degrades by more than 50% vs. baseline.
- Critical customer-facing errors reported by more than 5 customers.
- Any data corruption or migration failure detected during cutover.

## Rollback steps

1. **Declare incident:** notify the on-call engineer and page the release owner; start the incident timer.
2. **Decide:** if triggers are met, declare a rollback and freeze further deployment attempts.
3. **Revert the deployment:** roll back to the last known-good release tag using the documented rollout script.
4. **Verify:** run health checks and confirm the metrics dashboard shows normal error rate and latency.
5. **Communicate:** post a status update in the customer comms channel and notify support.
6. **Preserve evidence:** save logs, metrics snapshots, and timeline notes for the post-incident review.
7. **Follow-up:** schedule a blameless retro within 3 business days to capture root cause and预防 measures.

## Rollback owner

The release owner is the primary rollback owner and must be reachable (on-call phone + Slack) before any production push.

## Contact list

- Release owner: @hezi-liu (on-call rotation)
- Platform team: @platform-oncall
- Support lead: @support-lead
