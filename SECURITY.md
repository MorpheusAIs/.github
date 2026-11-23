# Security

Report suspected vulnerabilities privately. Do not open a public GitHub issue, pull request, or discussion for a suspected vulnerability.

## Reporting

- Public repositories: use GitHub private vulnerability reporting. Open the Security tab on the affected repository and choose Report a vulnerability, or use https://github.com/MorpheusAIs/<repo>/security/advisories/new and replace `<repo>` with the repository name.
- Private repositories, hosted services, or a repository without a Report a vulnerability button: email security@mor.org.

Include:

- Affected repo, host, endpoint, version, or commit.
- Impact.
- Steps to reproduce.
- Whether you have already seen it used against the service or network.

Do not include live credentials, customer data, or proof-of-concept traffic against production. Do not test against production with live credentials or customer data, and do not conduct denial of service or social engineering.

## What happens next

We will acknowledge the report and follow up with a fix path. Please give us time to investigate before any public write-up. Valid reports become private GitHub security advisories; fixes are prepared on a private branch and the advisory is published when the fix ships.

Supported version: latest release on main. Fixes land on dev and are promoted to main.

Bounty program terms: [Bug Bounty Program](https://github.com/MorpheusAIs/Docs/blob/main/Security%20Audit%20Reports/Bug%20Bounty%20Program.md).

Acknowledgement target: 3 business days.
