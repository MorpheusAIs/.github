# Contributing

## Before you start

- Check org Discussions. Share questions or ideas in the matching category first.
- Read the repository README and AGENTS.md if present.
- Look for issues labeled good first issue or help wanted.

## Branch model

| Branch | Role |
| --- | --- |
| dev | integration and the default PR target |
| test | staging, where present |
| main | production and releases |

Maintainers promote linearly `dev -> test -> main`. Some repositories use `dev -> main` only.

## How to submit

1. Make sure the work is tracked in an issue.
2. Outside contributors: fork the repository, branch from the current `dev`, and open a PR into `dev`.
3. Org members: branch from `dev` in the repository instead of forking.
4. If GitHub defaults the PR base to `main`, retarget it to `dev` before review. A few small repositories work directly against `main`; follow that repository's CONTRIBUTING if it has one.
5. Keep the branch up to date with `dev`.

## PR rules

- Every PR targets `dev` unless it is a promotion or release PR. A PR target check fails PRs aimed elsewhere.
- Use title prefixes: `feat(scope):`, `fix(scope):`, `docs(scope):`, `ci:`, or `chore:`.
- Link the issue with `Refs #123` or `Fixes #123`, or state why there is no issue (for example chore, revert, or CI-only).
- PRs need one approval from the Maintainers team, all conversations resolved, and required checks green.
- Squash merge into `dev`.

## Promotion and releases

Only Maintainers open promotion and release PRs.

- Promotion PR title: `promote: <summary> to test` or `to main`.
- Release PR into main: `Release vX.Y.Z — <themes>`.
- Promotions use merge commits.

## Workflows on fork PRs

Workflows from external contributors' fork PRs run only after a maintainer approves the PR. Fork PRs get a read-only token and no secrets.

## Agents and bots

AI agents and bots are welcome and follow the same rules and review gates as people. A human is accountable for each agent's PR. Repositories may have AGENTS.md with agent rules; the org-wide agent guide is [AGENTS.md](https://github.com/MorpheusAIs/.github/blob/main/AGENTS.md).

## No secrets

Do not put secrets in PRs, issues, or logs. This includes `.env` files, private keys, API keys, mnemonics, seed phrases, and base64 secret blobs.

## Code of conduct and security

See CODE_OF_CONDUCT.md. Report security issues privately; see SECURITY.md.

## Per-repository rules

If a repository has its own CONTRIBUTING.md, that file overrides this one.
