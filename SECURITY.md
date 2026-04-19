# Security policy

## Reporting a vulnerability

If you discover a security issue with the PlanMySaaS Claude Skill, please **do not open a public GitHub issue**. Instead, email **security@planmysaas.com** with:

- A description of the issue
- Steps to reproduce
- The version of the skill you tested (commit SHA or release tag)
- Your assessment of severity (low / medium / high / critical)
- Any proof-of-concept code or output

You should receive an acknowledgement within **48 hours**. We aim to publish a fix within **7 days** for high/critical severity, longer for low/medium.

## Scope

The skill itself is plain markdown — there is no executable code, no network calls, no data persistence inside this repository. The most likely security categories are:

- **Prompt injection** — a stage prompt that could be manipulated to make Claude write malicious content into the user's project folder
- **Output sanitisation** — generated build prompts that, if pasted into an AI coding tool, could produce insecure code patterns by default (e.g. weak password hashing, missing CSRF protection, exposed env vars)
- **Supply-chain** — anything in the install path (the `git clone` line in the README) that could be tampered with

## Out of scope

- The PlanMySaaS web dashboard at planmysaas.com — that has its own security policy at <https://planmysaas.com/security>
- Bugs in Claude itself, in Claude Code, or in Anthropic's services — please report those to Anthropic directly
- Bugs in third-party tools the skill mentions (Cursor, Lovable, Bolt, v0) — report those to the respective vendors

## Supported versions

| Version | Supported |
|---|---|
| v1.x   | ✓ Active development, security fixes ship within the SLAs above |
| < v1.0 | ✗ Not supported — please upgrade |

## Disclosure policy

We follow **coordinated disclosure**:
1. You report the issue privately
2. We acknowledge within 48 hours
3. We work on a fix together (you may be credited if you wish)
4. We publish the fix
5. After 30 days, we publish a brief disclosure with credit (unless you prefer otherwise)

## Thanks

Security researchers and ethical disclosers make every project safer. Thank you in advance.
