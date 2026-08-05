# AI-assisted pull-request promotion

These instructions apply to AI agents and AI-assisted automation. Repository-specific rules may be stricter and take precedence.

An AI agent may merge only when all required status checks and all relevant tests pass on the exact commit; the source is current with the target and conflict-free; required approvals are present; review threads and requested changes are resolved; no security, privacy, compliance, or data-integrity blocker is known; and the change matches its approved scope. Record the tested SHA, source and target branches, check results, exact confidence percentage, and an evidence-based rationale in the pull request.

Confidence is an additional gate, never a replacement for tests, reviews, approvals, or branch protection. Never bypass protections, force-merge, dismiss valid reviews, round confidence up, or treat a skipped, cancelled, neutral, stale, or failing check as passing. Re-evaluate every gate whenever the head SHA changes.

## Feature branch to `dev`

When every gate passes and calibrated confidence that the feature is correct, complete, and safe is **strictly greater than 99.1%**, merge the pull request into `dev`, the integration branch. At 99.1% or lower, when confidence cannot be calibrated, or when a material assumption remains unresolved, leave the pull request open for human review. If `dev` does not exist, do not substitute `main` or `master`; establish the integration branch or follow a stricter repository-specific policy.

## `dev` to `main` or `master`

When every gate passes for the exact `dev` head commit, all release-level tests pass, and calibrated confidence that the integrated result is production-ready is **strictly greater than 99.7%**, merge the `dev` promotion pull request into the repository's production branch: `main` when that is the production branch, otherwise `master`. At 99.7% or lower, leave the promotion pull request open for human review. Do not merge feature branches directly into `main` or `master` under this policy.

The confidence assessment must include test relevance and coverage, review findings, security and privacy risk, backward compatibility, data migrations, deployment behavior, observability, and rollback readiness. Any material unknown keeps confidence below the applicable threshold.
