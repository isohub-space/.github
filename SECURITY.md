# Security Policy

This is the default policy for repositories in the **isohub-space** organisation. A repository
that ships something security-sensitive overrides it with its own `SECURITY.md` — notably
[tessera](https://github.com/isohub-space/tessera), which is an OIDC / OAuth 2.0 authorization
server and carries its own, stricter policy. If you are reading this on a repository, no
override exists and the terms below apply.

## Reporting a vulnerability

**Please do not open a public issue, discussion, or pull request for a security problem.**

Use GitHub's **private vulnerability reporting**: the *Security* tab on the affected repository
→ **Report a vulnerability**. That opens a private advisory visible only to the maintainers, and
it gives us a private fork in which to develop and review the fix before anything is public.

If that button is missing on a repository, that is our bug and not yours — report it against
[tessera](https://github.com/isohub-space/tessera/security/advisories/new) instead and say which
repository you meant.

Please include:

- what you found, and the security impact if it were exploited;
- a `file:line` reference or reproduction steps — the exact command you ran is ideal;
- the version, tag, or commit SHA you tested;
- a suggested fix or mitigation, if you have one.

If you are unsure whether something counts, send it anyway.

## What to expect

These projects are maintained by a small team, so triage is best-effort rather than
contractual:

- **Acknowledgement within 5 business days.** If you have not heard back within 10, assume the
  message went astray and ping again — silence here is never a decision.
- We verify every report against the real code before acting. We will not dismiss a finding
  without saying why, and we will not call something fixed without a command that demonstrates
  it.
- We will agree a disclosure timeline with you rather than impose one. If we cannot fix an
  issue, we will say so and document the limitation rather than leave it unstated.
- We credit reporters in the advisory and release notes unless you would rather stay anonymous.

## Supported versions

**The default branch is the supported version.** These are pre-1.0, actively developed
projects; fixes land on the default branch. Where a repository maintains release lines or
publishes container images, its own `SECURITY.md` will say so — please otherwise report against
the latest default branch or the newest published artifact.

We deliberately publish no version-support table. A hardcoded table rots the moment it is not
updated, and a stale one is worse than none — it makes "is my version supported?" unanswerable
while still looking authoritative.

## Scope

These repositories cover space mission software and the services and tooling around it. In
scope:

- authentication, authorization, and multi-tenant isolation on any exposed surface;
- secrets committed, logged, or embedded in images, manifests, or compose files;
- injection, path traversal, deserialization, and SSRF in code we ship;
- dependency vulnerabilities we can act on;
- CI and release workflows that could be abused to ship altered artifacts, and published
  container images that carry more than they should;
- integrity of mission and telemetry data paths where a flaw could let one tenant read or
  influence another's.

Out of scope: findings that require an already-compromised host or a deliberately misconfigured
deployment — for example exposing a service directly to untrusted clients without the documented
authenticating gateway in front of it; missing hardening with no demonstrated exploit path; and
raw scanner output pasted without a verified impact. Reports that depend on a misconfiguration
are still assessed case by case rather than dismissed outright.

Volume-submitted or AI-generated reports with no verified reproduction will be closed unread.

## What we do not claim

This document asserts no list of security guarantees. Any such claim would be one a reporter
could falsify in ten minutes, and a policy that overstates its own rigour loses credibility
exactly when it is most needed. What we commit to is the process above: private intake, real
verification against the code, honest disclosure, and credit.
