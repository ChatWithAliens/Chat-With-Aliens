# Security Policy

## Supported Versions

Only the latest production release at [chatwithaliens.net](https://chatwithaliens.net) is actively maintained.

## Reporting a Vulnerability

If you discover a security vulnerability, please do **not** open a public GitHub issue.

Instead, report it privately:

1. Email a description of the vulnerability, steps to reproduce, and any proof-of-concept to the repository maintainer via GitHub's private vulnerability reporting feature.
2. We will acknowledge receipt within 48 hours and aim to release a fix within 7 days for critical issues.
3. Once a fix is deployed, we will publicly disclose the issue with credit to the reporter (unless you prefer to remain anonymous).

## Scope

In scope:
- SQL injection or data exposure via the API
- Authentication or session vulnerabilities
- Cross-site scripting (XSS) in the chat interface
- Exposure of server-side environment variables or API keys

Out of scope:
- Denial-of-service via message flooding (rate limiting is enforced)
- Social engineering attacks
- Issues in third-party dependencies not yet publicly disclosed (report those upstream)

Thank you for helping keep this project and its users safe.
