# AI-assisted pull-request promotion

These instructions apply to AI agents and AI-assisted automation. Repository-specific rules may be stricter and take precedence.

An AI agent may merge only when all required status checks and all relevant tests pass on the exact commit; the source is current with the target and conflict-free; required approvals are present; review threads and requested changes are resolved; no security, privacy, compliance, or data-integrity blocker is known; and the change matches its approved scope. Record the tested SHA, source and target branches, check results, exact confidence percentage, and an evidence-based rationale in the pull request.

Confidence is an additional gate, never a replacement for tests, reviews, approvals, or branch protection. Never bypass protections, force-merge, dismiss valid reviews, round confidence up, or treat a skipped, cancelled, neutral, stale, or failing check as passing. Re-evaluate every gate whenever the head SHA changes.

## Feature branch to `dev`

When every gate passes and calibrated confidence that the feature is correct, complete, and safe is **strictly greater than 99.1%**, merge the pull request into `dev`, the integration branch. At 99.1% or lower, when confidence cannot be calibrated, or when a material assumption remains unresolved, leave the pull request open for human review. If `dev` does not exist, do not substitute `main` or `master`; establish the integration branch or follow a stricter repository-specific policy.

## `dev` to `main` or `master`

When every gate passes for the exact `dev` head commit, all release-level tests pass, and calibrated confidence that the integrated result is production-ready is **strictly greater than 99.7%**, merge the `dev` promotion pull request into the repository's production branch: `main` when that is the production branch, otherwise `master`. At 99.7% or lower, leave the promotion pull request open for human review. Do not merge feature branches directly into `main` or `master` under this policy.

The confidence assessment must include test relevance and coverage, review findings, security and privacy risk, backward compatibility, data migrations, deployment behavior, observability, and rollback readiness. Any material unknown keeps confidence below the applicable threshold.


<!-- ore-org-baseline:begin -->
These instructions apply to this repository. Repository-local instructions may add stricter requirements, but they must not weaken this baseline.

## Canonical organization links

- GitHub organization: https://github.com/streempilot-test
- Public organization defaults: https://github.com/streempilot-test/.github
- Canonical Linear project: https://linear.app/denman/project/githubcomstreempilot-test-481b1eec976c
- Fleet tracking issue: https://github.com/ORESoftware/k8s-cluster/issues/1222

## Instruction discovery

Lowercase `agents.md` is canonical. Read every applicable lowercase `agents.md` from the repository root toward the current working directory before editing. Uppercase `AGENTS.md` and provider-specific instruction files are compatibility mirrors and must remain aligned with the applicable lowercase policy.

## Inspect before editing

Inspect the current branch, complete working tree, remotes, default branch, open pull requests, linked GitHub issues, linked Linear work, repository documentation, tests, schemas, generated artifacts, deployment definitions, and relevant related repositories. Preserve every unfamiliar or uncommitted change.

Use read-only inspection and non-pruning synchronization such as `git status --short --branch`, `git remote -v`, `git fetch --all`, `git diff`, `git log`, `git show`, and `git blame`. Never treat a dirty worktree or inconvenient branch as permission to discard state.

## Mandatory semantic conflict resolution

> resolve any and all git conflicts semantically, will full context, even looking back 3-10 commits in git log history for more context - never hastily pick sides in a conflict but merge things conceptually, using max context and complete conceptual awareness for a given github organization's repos and external org repos too

For every conflict:

1. Read the merge base, both complete sides, surrounding implementation, tests, schemas, generated artifacts, documentation, deployment configuration, and public contracts—not only conflict markers.
2. Inspect the affected path history and normally review 3–10 relevant commits on each side with `git log`, `git show`, and `git blame` where useful.
3. Review linked pull requests, issues, Linear work, related repositories in `streempilot-test`, and relevant external-organization repositories whenever behavior or contracts cross boundaries.
4. Preserve compatible intent and invariants from both sides. Synthesize a conceptual merge; never resolve by selecting `ours`, `theirs`, `current`, or `incoming` wholesale.
5. Scan the complete tree for unresolved markers and run the applicable formatter, linter, unit, integration, contract, build, security, and end-to-end checks.
6. Document incompatible requirements, intentional choices, and any discarded intent in the commit and pull-request description.

## Hard denylist for automated agents

Automated agents must **never execute or recommend** destructive, state-concealing, history-rewriting, purge, revocation, or policy-bypass operations. This is a hard denylist: authorization may support a reviewed human-run procedure, but it does not authorize an automated agent to perform the destructive step.

The blacklist includes, without limitation:

- every form of `git stash`, every mode of `git reset`, every mode of `git clean`, `git filter-repo`, `git filter-branch`, BFG, `git rebase`, interactive history rewriting, `git commit --amend`, commit replacement, destructive `git checkout -- <path>`, destructive `git restore`, `git branch -D`, ref or tag deletion, `git reflog expire`, `git gc --prune`, `git push --force`, and `git push --force-with-lease`;
- recursive or bulk deletion and destructive filesystem mutation, including `rm -rf`, `find -delete`, truncation, shredding, destructive overwrite, formatting, and access-removing ownership or permission changes;
- destructive data operations, including `DROP`, `TRUNCATE`, unbounded `DELETE`, destructive rollback, irreversible migration, bucket/object purge, queue/topic deletion, and bulk mutation without a bounded reversible plan;
- destructive infrastructure or identity operations, including `kubectl delete`, `helm uninstall`, `terraform destroy`, `pulumi destroy`, cloud delete/purge calls, cluster or namespace teardown, and autonomous secret, key, certificate, credential, factor, or session revocation or rotation;
- deleting repositories, worktrees, submodules, branches, tags, releases, packages, artifacts, registries, environments, evidence, audit logs, customer data, or production state;
- bypassing hooks, reviews, branch protection, rulesets, required checks, security/compliance gates, approvals, or audit logging, including `--no-verify` and equivalent bypasses.

Do not use destructive commands merely to make tests pass, clear a conflict, simplify a migration, or hide an inconvenient state.

### Required safe alternatives

Use additive branches, separate clean worktrees or clones, explicit path staging, ordinary commits, non-force pushes, patch-based edits, read-only queries, dry runs, backups, additive migrations, and reversible roll-forward changes. Leave unrelated work untouched. When safe progress is impossible, preserve all state and report the exact blocker.

## Source ownership and cross-repository context

Edit authoritative sources rather than generated mirrors, vendored copies, caches, or downstream consumers. Identify generators and regenerate derived artifacts from reviewed sources. Never detach, absorb, relocate, remove, or rewrite a submodule or worktree. Cross-repository behavior must be understood across the owning organization and relevant external organizations before contracts are changed.

## Secrets and sensitive data

Never print, log, commit, paste into issues, include in fixtures, or expose tokens, passwords, private keys, session material, database URLs, customer data, legal records, private health data, production data, or unpublished security details. Use approved secret stores, placeholders, and redacted diagnostics.

## Pull requests, validation, and evidence

Use focused branches and pull requests. Link the relevant Linear issue or project. Explain behavior, risks, migration and roll-forward considerations, security impact, tests run, conflicts and their semantic resolution, and cross-repository dependencies. Never report a branch, commit, pull request, merge, deployment, test run, or external update as complete without authoritative remote evidence.
<!-- ore-org-baseline:end -->
