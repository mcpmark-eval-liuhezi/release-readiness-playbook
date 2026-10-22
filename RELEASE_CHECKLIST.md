# Release Checklist

This checklist is the gate the **Release Readiness Check** workflow enforces: the workflow fails if this file is not present at the repository root before a release is published.

## Reference release

Anchored on a real, mature open-source release — Node.js `v20.11.0`:

- **Project:** [nodejs/node](https://github.com/nodejs/node)
- **Release tag:** [`v20.11.0`](https://github.com/nodejs/node/releases/tag/v20.11.0)
- **Release title (as GitHub returns it):** 2024-01-09, Version 20.11.0 'Iron' (LTS), @UlisesGascon
- **Line:** LTS (Node.js 20 "Iron")
- **Release `target_commitish`:** `main`
- **Commit SHA the tag points to:** `8d4fbd7bb11a300157aeff8e13221c093628dd4e`
- **Tag object:** annotated & GPG-signed, tag object SHA `2a7cc6b52ae43f928ad7fdeb38dc6ed7d1089708`, tagged by Ulises Gascón on 2024-01-09T20:04:41Z

## Pre-publish verification

Before publishing, the release manager must verify:

- [ ] **Release notes are complete and accurate** — every notable change since the last tag is listed, semver-impactful items are flagged (e.g. SEMVER-MINOR), and no changelog entry is missing or duplicated.
- [ ] **The tag is created on the intended commit** — the annotated, signed tag points at the reviewed, CI-green commit SHA, and the tag message and Git-EVTag checksum are verified against that commit.
- [ ] **CI is green on the release commit** — the full build/test/lint suite has passed on the exact commit being tagged, not merely on a nearby branch tip.
- [ ] **Artifacts build and are reproducibly hashable** — binaries, packages, and source tarballs build cleanly and their published checksums match what was produced locally.
- [ ] **Security and dependency review is current** — no open critical/high dependabot or code-scanning alerts, and bundled dependency updates are accounted for (Node.js bundles these in release notes; e.g. NSS, zlib, undici updates in v20.11.0).
- [ ] **Version numbers and metadata are correct** — version bumped in every required place (e.g. `process.versions` equivalent, docs), and the "Current vs LTS" line and release date in the title are right.
- [ ] **Signatures and verification pass** — release artifacts and the tag verify against the maintainer's published key; the GPG signature on the tag is `valid`.
- [ ] **Announcements are drafted and approved** — the release blog post, changelog entry, and any migration/upgrade notes are reviewed and scheduled.
- [ ] **Rollback plan is documented** — what to do if the release must be yanked or superseded, including who owns the decision and how users get notified.

---

## Runbook for this repo

1. Update this checklist for the release in question.
2. Run the **Release Readiness Check** workflow (Actions → *Release Readiness Check* → *Run workflow*), passing the tag under review as the `reference_tag` input (e.g. `v20.11.0`).
3. The workflow echoes the reference tag and fails if this file is missing, so an unchecklisted release cannot pass the gate.
4. Merge, tag, publish.
