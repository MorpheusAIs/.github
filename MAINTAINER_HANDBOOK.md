# Maintainer Handbook

## 1. Purpose and audience

This handbook describes how the **MorpheusAIs** GitHub organization works. It is written for:

- human maintainers who run the org
- agents, whether brought by maintainers, by community members, or the collective Buzz agent (proposed)

Agents can parse the **Rules** tables to know exactly what is allowed.  
Everyone else should read from top to bottom.

## 2. Where records live

One home per record; link, don’t copy. Use this table to decide where something belongs.

| Place                      | What goes here                                             | Never here                                |
|-----------------------------|------------------------------------------------------------|-------------------------------------------|
| Discord                     | Community chats                                            | Official announcements, decisions, records|
| Buzz (private maintainer room) | Private maintainer talk; urgent heads-ups               | Permanent records, public announcements, security reports |
| Signal                      | Urgent / private only; decisions written back same day    | General discussion, permanent records    |
| GitHub Discussions (org)     | Announcements (maintainers only), Start here / General, Q&A, ideas, polls | Security reports; team coordination; work that should already be an issue |
| Issues (repos)              | Bugs, Features, Tasks, Initiatives, roadmap tracking   | Security reports, private discussions    |
| PRs (repos)                 | Code changes, promote PRs, release PRs                  | Security fixes (use private advisory)     |
| Morpheus Work project (private) | Private initiative status, private-issue stubs; no PRs | Public tracking, code                   |
| Morpheus Roadmap project (public) | Public tracking issues labeled `roadmap`; Horizon / Wave fields | Private information, code               |
| Maintainer-Context (private repo) | Decision log, initiatives, how-we-work               | Public discussion, code changes          |
| MRC repo (public)            | Accepted MRC proposals (Contracts & MRC category)       | Other discussions                        |

## 3. Daily loop

### Triage

- Issue forms in Node, API and Uplink add the `needs-triage` label.  
- Issue types: **Bug**, **Feature**, **Task**, **Initiative** (an Initiative groups epics and tasks as sub-issues).  
- Discussions that are actionable should be converted to an issue.  
- Response target: 3 business days.

### Reviewing PRs

**Branch flow for features**  
- Node and API repos: `dev` → `test` → `main`  
- APP repo: `dev` → `main`  
- Uplink and repos with only `main`: PR into `main`

Outside contributors fork, branch from the current `dev`, and PR into `dev`.  
Org members may branch directly in the repo.

**Rules** (enforced by branch protection rulesets)

| Area                          | Rule                                                                                       |
|-------------------------------|--------------------------------------------------------------------------------------------|
| Target branch                | Must be correct development branch; retarget if wrong.                                    |
| Approval                    | At least 1 approval from a member of the **maintainers** team.                             |
| Stale approvals             | Dismissed on new push.                                                                     |
| Conversations               | All must be resolved before merge.                                                        |
| Merge method on main/test/stg | merge commit only                                                                        |
| Merge method on dev/develop    | merge or squash                                                                        |
| Bypass                     | Org owners may bypass **only via pull request**; no force-push or direct admin override. |

Humans approve and merge; agents never approve or merge (see section 7).

### Promotion and releases

Promote PRs titled `promote: ...` or `Release vXYZ — ...` are **maintainers-only**.

**Release notes grouping**  
In the Node, API, and Uplink repos, a `.github/release.yml` file groups release notes by label.  
Before merging a PR to those repos, apply the correct label so it appears in the right section:

- `enhancement`
- `bug`
- `documentation`
- `dependencies`

## 4. Roadmap

### Go-public step

When a private Initiative (in Maintainer-Context, type **Initiative**) is ready to be seen publicly:  
1. A maintainer opens or labels a public tracking issue with the `roadmap` label in the product repo.  
2. Link it from the private initiative.  
3. The public issue is the window; the private issue remains the record.

### Horizon and Wave

The public **Morpheus Roadmap** project has these fields:

| Field    | Values                                                       | Who sets it     |
|----------|--------------------------------------------------------|-----------------|
| Horizon  | 00-Urgent, 01-Now, 02-Next, 03-Later, 04-Someday | Person (maintainer) |
| Wave     | Optional number                                     | Person (maintainer) |

Views: board grouped by Horizon, table grouped by Initiative / parent issue.

### Rules that drive the roadmap



Nothing moves to **01-Now** while it has an open blocker.  
Use `blocked-by` links to express sequence, and sub-issues to define the hierarchy **Initiative → epics → tasks**.

Keep the **Morpheus Work** project private; it never contains PRs.

Project: [Morpheus Roadmap](https://github.com/orgs/MorpheusAIs/projects) (public).

## 5. Security handling

All security reports must use:

- **Private vulnerability reporting** on the affected repo, or
- **security@mor.org**

Never discuss security issues in public Issues, Discussions, PRs, Discord, or Buzz.

Process:
1. Reporter opens a private report.  
2. Maintainer creates a **private advisory**.  
3. Fix is developed in private.  
4. Advisory is published when the fix ships; or, once safe, a maintainer opens a public issue.

## 6. Announcements

- Post official announcements in the **Announcements** category of GitHub Discussions.  
- That category feeds **one-way** to the community Discord.  
- Motto: *“Discord helps the community talk, Buzz helps the maintainers talk, GitHub remembers.”*

## 7. Working with agents

Agents contribute code through **draft PRs**. A human maintainer must always review, approve, and merge.

### Agent rules

| MUST (always)                                | MUST NOT (ever)                                                   |
|----------------------------------------------|-------------------------------------------------------------------|
| Work in draft PRs                            | Approve or merge any PR                                           |
| Disclose that they are an agent              | Release or deploy to any environment                              |
| Name the accountable human                   | Modify workflows, release configurations, or deploy configurations (unless the exact change is requested by the linked issue) |
| Follow the same review gates as humans       | Put secrets, keys or tokens in any file, issue, PR or prompt      |
| Keep changes small and scoped to the issue   | Bypass branch protections                                         |

### Human maintainer tasks for agents

- Review the agent’s draft PR.  
- Approve only when it meets the same quality and security bar.  
- Merge on behalf of the agent.  

See the full agent guidance in [AGENTS.md](./AGENTS.md).

## 8. Your membership

Org membership is **private** by default.  
Maintainers may optionally make their membership **public** — it is a personal choice.

To change visibility:
1. Open the [People tab](https://github.com/orgs/MorpheusAIs/people).
2. Find your username.
3. Use the Private/Public visibility menu next to it and choose Public.

You can switch back to Private at any time.

## 9. Onboarding / offboarding checklist

### Adding a new maintainer

Add to the **maintainers** team (grants the `all_repo_maintain` role).  
- Two-factor authentication on your GitHub account (the org will require it).  
- Ensure they have read (at minimum):  
  - [README.md](./README.md)  
  - [CONTRIBUTING.md](./CONTRIBUTING.md)  
  - [SECURITY.md](./SECURITY.md)  
  - [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md)  
  - [AGENTS.md](./AGENTS.md)  
  - This handbook  
  - Private **Morpheus-Maintainer-Context** repo  
- Brief them on the Buzz room and Discord presence.

### When a maintainer leaves or steps down

1. Remove from the **maintainers** team.  
2. Remove from the **security** team (if member).  
3. Remove from the **collaborators** team (if member).  
4. Record their status as **emeritus** in Maintainer-Context.  
5. Do **not** leave any unwanted write or admin access.

## 10. Quick reference card

One home per record; link don’t copy.  
- Respond to issues within 3 business days.  
- All PRs need one maintainer approval + resolved conversations.  
- Agent PRs are always draft; never approve/merge; disclose agent and human.  
- Security → private reporting or security@mor.org only.  
- Announcements → GitHub Discussions Announcements → feeds one-way to Discord.  
- Roadmap: Horizon set manually; nothing to 01-Now with open blockers; use sub-issues (Initiative → epic → task).  
- Promote PRs titled `promote: ...` or `Release vX.Y.Z`; label PRs for release-note grouping.  
- Decisions from Buzz / Signal must be written back to GitHub the same day.  
- Public membership is optional → [People tab](https://github.com/orgs/MorpheusAIs/people).
