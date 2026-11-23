# Security and privacy baseline

This repository must contain **only synthetic public data**. Never commit tokens, browser/session exports, credentials, real Jira issues, internal URLs, corporate code or employee records.

## Incident to resolve
On 2026-11-23 an accidentally pasted browser/session export was found in the publicly accessible README and removed from its latest version. **The original commit/branches and external caches may still contain the data.** Treat any exposed access tokens as compromised; revoke sessions/tokens, review sign-in activity and rotate affected credentials. Deleting content in a new commit does NOT remove it from Git history. Follow GitHub's sensitive-data-removal guidance and contact GitHub Support for cached objects/PR refs if necessary.

## Application controls
- Explicit authorization before any real corporate integration; least-privilege read-only scopes first.
- Keep tokens in approved secret storage, encrypt at rest; never return to frontend or logs.
- Inbound issues/messages are untrusted data; defend against prompt injection, replay and forged webhook calls.
- Agent runner must be isolated, rate-limited, permission-scoped, with auditable tool calls, cancellation and timeouts.
- Human approval binds to exact action parameters and revision/fingerprint; expiration and idempotency are mandatory.
- No destructive changes, upstream issue edits, privileged access updates, prod deploy or merges without human permission.
- Separate human effort, agent wall time and human review time.
- Avoid sensitive data in screenshots, demo fixtures, traces and AI model requests.

## Before real integration
Document organization permission, data classifications, data destinations, subprocessors, retention, approved environment, auth scope, threat model and rollback plan.
