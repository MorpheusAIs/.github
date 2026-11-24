# Governance

This document outlines the governance structure of the MorpheusAIs organization. It defines roles, decision-making processes, communication channels, branch protections, and the path from community member to maintainer.

## Roles and responsibilities

### Owners
Owners have administrative access across all repositories and organization settings. They can bypass the branch rulesets only through a pull request, never by pushing directly, manage org-level configurations, and act as final decision-makers when consensus cannot be reached.

Current owners: see [MAINTAINERS.md](./MAINTAINERS.md#owners).

### Maintainers
Members of the Maintainers team hold the `all_repo_maintain` organization role, which grants Maintain permission on every repository. They are required reviewers on protected branches (see [Branch protection](#branch-protection)), approve and merge pull requests, triage issues, and ensure the quality and security of the codebase. Maintainers participate in the private Buzz coordination room and have access to the private `Morpheus-Maintainer-Context` repository.

Current maintainers: see [MAINTAINERS.md](./MAINTAINERS.md#maintainers-team).

### Security managers
Security managers hold the `security_manager` organization role. They handle private vulnerability reports, manage security alerts and advisories, and coordinate with maintainers on security-sensitive code changes. They are the first responders for reports sent to `security@mor.org` or submitted through GitHub’s private vulnerability reporting.

Current security managers: see [MAINTAINERS.md](./MAINTAINERS.md#security-team).

### Agents
Agents are automated accounts that contribute code or perform tasks. They are granted `all_repo_write` (Write on every repository, never Admin). Agents work through draft pull requests, never approve or merge, and must disclose that they are agents and name the accountable human. Agent activity is subject to the same review and approval gates as human contributions. See [AGENTS.md](./AGENTS.md) for more details.

Current agents: see [MAINTAINERS.md](./MAINTAINERS.md#agents-team).

### Community and contributors
Anyone can read public repositories, fork them, open issues, and participate in GitHub Discussions. Contributors who submit pull requests are recognized as community contributors. Over time, proven contributors may be invited to higher trust levels; the full progression is described in the [Contributor ladder](#contributor-ladder) section.

## How we make decisions

### Discussions
Day-to-day decisions, questions, and ideas are discussed publicly in [GitHub Discussions](https://github.com/orgs/MorpheusAIs/discussions). Where possible, discussions happen in the relevant category (Start here / General, Q&A, Ideas, etc.). Maintainers and community members are encouraged to participate.

### Major changes (MRC)
Large or fundamental changes (protocol upgrades, governance modifications, new standards) must follow the MRC (Morpheus Request for Comments) process. The change is first discussed in the `Contracts & MRC` Discussions category. Once a clear proposal emerges, it is formally written up and submitted as a pull request to the [MRC repository](https://github.com/MorpheusAIs/MRC). An accepted MRC may become a Roadmap item tracked in the [Morpheus Roadmap](https://github.com/orgs/MorpheusAIs/projects) project.

### Lazy consensus (proposed)
For smaller, non-controversial decisions, maintainers use lazy consensus. A proposal is posted in the relevant public channel and is considered accepted if no maintainer objects within **72 hours** (proposed). Maintainers may shorten this window for urgent, low-risk items. Any maintainer may escalate to a formal MRC if they believe more deliberation is needed.

### Owners as tie-breakers
When maintainers cannot reach a decision after discussion and an MRC review, the Owners act as the final decision-makers. Owners may also intervene in emergency situations that threaten the integrity or security of the project.

## Where things live

| Surface | Purpose | Visibility | Who |
|--------|---------|------------|-----|
| **GitHub repos, Issues, PRs** | Code, documentation, task tracking, technical decisions | Public (most repos) | Everyone (public), maintainers (all) |
| **GitHub Discussions** | Questions, ideas, announcements, community support | Public | Community and maintainers |
| **Morpheus Roadmap project** | Public tracking of roadmap items | Public | Everyone |
| **Morpheus Work project** | Private product status, private-report stubs | Private | Maintainers |
| **MRC repo** | Formal proposals for major changes | Public | Everyone |
| **Morpheus-Maintainer-Context repo** | Decision log, private initiatives, how-we-work | Private | Maintainers |
| **Discord** | Real-time community chat | Public ([invite](https://discord.gg/YYKEahcutB)) | Community |
| **Buzz** | Private maintainer coordination room | Private | Maintainers |
| **Signal** | Urgent / private communication | Private | Owners and maintainers (as needed) |

**Motto:** *"Discord helps the community talk, Buzz helps the maintainers talk, GitHub remembers."*

GitHub is the single source of record for announcements, decisions, and roadmap items. Announcements are pushed one-way from GitHub to Discord. Decisions made on Buzz or Signal are written back to a GitHub issue or PR the same day. Private records that must remain private stay in Morpheus-Maintainer-Context.

## Branch protection

All repositories are covered by organization-wide rulesets. The key protections are:

| Branch pattern | Rules |
|---------------|-------|
| `main`, `test`, `stg` | No deletion, no force push. Pull request required with at least **1 approval from the Maintainers team**. Stale approvals are dismissed on new pushes. Conversations must be resolved before merging. Merge method: **merge commit only**. |
| `dev`, `develop` | Same as above, except merge methods allowed: **merge commit or squash**. |

Org Owners **cannot push directly** to protected branches. They may bypass these restrictions only by opening a pull request.

## Branch flow

- **Feature branches**: fork the repo (outside contributors) or create an in-repo branch (org members), branch from `dev` (or `main` if the repo has no `dev`), submit a PR to `dev`.
- **Node and API repos**: changes flow `dev` → `test` → `main` via promote PRs.
- **App repos**: changes flow `dev` → `main`.
- **Uplink and single-main-branch repos**: PR directly into `main`.
- **Promote PRs**: titled `promote: …` or `Release vX.Y.Z — …` are opened by maintainers only.

## Response targets

We aim to respond to new GitHub Discussions within **3 business days**. For security reports, the expected initial acknowledgement time is defined in [SECURITY.md](./SECURITY.md).

## Security

Report security vulnerabilities **privately**. Never discuss them in public issues, Discussions, PRs, Discord, or Buzz.

- **Preferred:** use GitHub’s private vulnerability reporting on the affected repository.
- **Alternate:** email `security@mor.org`.

Vulnerability reports are handled by the [Security managers](#security-managers) in coordination with the Maintainers team. We follow coordinated disclosure and will credit reporters unless they wish to remain anonymous. For more details, see [SECURITY.md](./SECURITY.md).

## Code of conduct

All participants must follow our [Code of Conduct](./CODE_OF_CONDUCT.md). Violations may result in removal from discussions, revocation of contributor privileges, or organization removal.

## Governance changes

This governance document can be updated by submitting a pull request to the `.github` repository. The PR must be reviewed and approved by at least one Maintainer (and follow the same [lazy consensus](#lazy-consensus-proposed) or MRC process as described above). Amendments that materially alter the role of Owners or the decision-making framework should be treated as major changes and follow the full MRC process.

## Contributor ladder

The community is built on trust and demonstrated contribution. The levels below show the progression. Except where a **fact** is quoted, the criteria and expectations are **proposed** and may be adjusted by maintainers as the org matures.

| Level | What you can do | How you get there | What's expected |
|-------|-----------------|-------------------|-----------------|
| **Community member** | Read public repos, fork, open issues, join GitHub Discussions and Discord. | Just show up. No invitation needed. | Follow the Code of Conduct, be respectful. |
| **Contributor** | Same as above, plus your merged PRs are publicly recorded. You may be listed in contributors files (proposed). | Have at least one merged PR in any MorpheusAIs repo (proposed). | Submit clear PRs, respond to review feedback, keep discussions constructive. |
| **Repeat contributor** | Write access as an outside collaborator on specific public repos (no paid seat). Can push branches, manage issues, and help triage. | Invited by maintainers after a pattern of quality contributions (multiple merged PRs, constructive reviews, demonstrated alignment with project principles) (proposed criteria). | Continue contributing actively, help review others’ work, mentor newcomers, uphold the Code of Conduct. |
| **Org collaborator (Collaborators team)** | Organization member (paid seat). Write access to additional private/internal repos as granted by the team permissions. May assist with maintenance tasks. | Invited from the pool of repeat contributors by maintainers. Requires a commitment to spend time on project coordination and a GitHub seat provided by the org (proposed). | Participate in team discussions, help with issue triage, participate in reviews, act as a responsible org member. |
| **Maintainer (Maintainers team)** | `all_repo_maintain` on every repo. Required reviewer on protected branches, can approve and merge PRs, access private maintainer contexts (Buzz, Morpheus-Maintainer-Context). | Invited by existing maintainers (and acknowledged by Owners) when the project needs and the individual’s track record warrants it. Must already be a Collaborator (proposed). | Enforce branch protections and security practices, review PRs in a timely manner, participate in Buzz discussions, follow the decision-making process, handle disputes professionally, and mentor lower-ladder members. |
| **Owner** | Administrative access on all repos and the org. Final decision authority. | Existing Owners vote to add new Owners. Candidates are typically drawn from long-time Maintainers. | Set strategic direction, ensure continuity, handle critical incidents. |

The path from Community member to Maintainer is not a guaranteed conveyor belt. Invitations are based on need and trust. The org reserves the right to skip or adjust rungs extraordinarily (e.g., bringing in a known expert as a Maintainer directly) — such exceptions are documented in the private decision log.
