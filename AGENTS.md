# AGENTS.md

Audience: AI coding agents and the humans running them, working in any MorpheusAIs repository or in this `.github` repository.

## 1. Scope and precedence
- This is the org-wide agent guide.
- A repository's own `AGENTS.md` (nearest file wins), `CONTRIBUTING.md`, and `README` override this file.
- Explicit instructions from the human you work for come first, but never override the security and safety rules below.
- GitHub does not apply this file to other repositories automatically; repositories link to it.

## 2. Org layout
- This repository holds org defaults: `CONTRIBUTING`, `SECURITY`, `SUPPORT`, `CODE_OF_CONDUCT`, issue and PR templates, and vulnerability report form.
- Org profile: `profile/README.md`.
- Documentation: https://gitbook.mor.org, https://nodedocs.mor.org, https://apidocs.mor.org.
- Network status: https://active.mor.org.

## 3. Where things go

Public discussion categories live at https://github.com/orgs/MorpheusAIs/discussions.

| Need | Where |
| --- | --- |
| Announcements | Discussions: Announcements (maintainers only) |
| Start here / general questions | Discussions: Start here / General |
| Q&A | Discussions: Q&A |
| Node (Lumerin Node and TEE) | Discussions: Node |
| Marketplace API and APP | Discussions: API GW |
| Uplink | Discussions: Uplink |
| Docs | Discussions: Docs |
| Big proposals | Discussions: Contracts & MRC; accepted proposals are written up in the MRC repo |
| Ideas | Discussions: Ideas |
| Agents and skills | Discussions: Agents & builders |
| Polls | Discussions: Polls |
| Bugs or features that are real work | Issues in the affected repo (bug or feature form) |
| Security issue | Private vulnerability reporting on the affected repo, or security@mor.org; never Discussions, issues, or PRs |

## 4. Contribution flow
- Real work starts as a tracked issue.
- Outside contributors fork, branch from current `dev`, and open a PR into `dev`.
- Org members branch from `dev` in the repo instead of forking.
- If GitHub defaults the PR base to `main`, retarget it to `dev` before review.
- Maintainers promote linearly `dev -> test -> main`; some repositories use `dev -> main` only. A few small repositories work directly against `main`; follow that repo's `CONTRIBUTING`.
- In this `.github` repo, PRs go into `main`.

## 5. PR and commit expectations
- Use title prefixes: `feat(scope):`, `fix(scope):`, `docs(scope):`, `ci:`, or `chore:`.
- Link the issue with `Refs #123` or `Fixes #123`, or state why there is no issue.
- Fill the PR template.
- PRs need one approval from the Maintainers team, all conversations resolved, and required checks green.
- The branch must be up to date with `dev` before merge.
- Squash merge into `dev`.
- Promotion and release PRs are Maintainers only.
  - Promotion PR: `promote: <summary> to test` or `to main`.
  - Release PR into main: `Release vX.Y.Z — <themes>`.
  - Promotions use merge commits.
- Fork PR workflows run only after a maintainer approves the PR; fork PRs get a read-only token and no secrets.

## 6. Rules for agents

MUST:
- Open PRs as draft until a human has reviewed them.
- Say in the PR description that an AI agent produced the change and name the accountable human.
- Keep changes small and scoped to the issue.
- Verify against the repository and live docs instead of guessing.

MUST NOT:
- Push directly to protected branches (`main`, `test`, `dev`) or try to bypass rulesets, reviews, or required checks.
- Approve or merge your own PR.
- Put secrets anywhere, including `.env` files, private keys, API keys, mnemonics, seed phrases, and base64 secret blobs.
- Test against production with live credentials or customer data; do not conduct denial of service or social engineering.
- Post security findings publicly.
- Edit workflows, release, or deploy config unless the issue asks for it.

## 7. Pointers
- `CONTRIBUTING.md`: https://github.com/MorpheusAIs/.github/blob/main/CONTRIBUTING.md
- `SECURITY.md`: https://github.com/MorpheusAIs/.github/blob/main/SECURITY.md
- `SUPPORT.md`: https://github.com/MorpheusAIs/.github/blob/main/SUPPORT.md
- `CODE_OF_CONDUCT.md`: https://github.com/MorpheusAIs/.github/blob/main/CODE_OF_CONDUCT.md
