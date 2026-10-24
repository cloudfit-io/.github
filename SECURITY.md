# Security policy

This policy covers every repository in the cloudfit-io organization: cloudfit-core, cloudfit-provider-gcp, cloudfit-provider-aws, cloudfit-api, cloudfit-ui, and the project website.

## Supported versions

Security fixes go into the latest release of each package. Older releases are not patched; upgrade to the latest version to get fixes.

## Reporting a vulnerability

Please report vulnerabilities privately, not in a public issue.

1. Open the affected repository on GitHub.
2. Go to **Security**, then **Report a vulnerability**.
3. Describe the issue, the affected version, and how to reproduce it.

This uses GitHub's private vulnerability reporting, so the report is visible only to the maintainers until a fix is published.

What to expect:

- An acknowledgement within 5 business days.
- An assessment and, if confirmed, a fix plan within 14 days.
- Credit in the release notes when the fix ships, unless you prefer to stay anonymous.

## Scope

In scope: the cloudfit libraries, the API service, the demo UI, and their release and data-refresh automation.

The public demos on Hugging Face Spaces are best-effort services for evaluation. They hold no user data and require no credentials; please do not run load or denial-of-service tests against them.

## How the project manages dependencies

Every pull request runs a dependency audit (`pip-audit`) against each package's runtime dependencies, and publishing a release requires that audit to pass. Dependabot proposes dependency updates monthly. Any advisory that is deliberately ignored is listed, with the reason, in the repository's CI workflow.
