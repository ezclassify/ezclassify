# Security Policy

## What This Repository Is

This repository holds documentation. It ships no software, publishes no
package, and runs no service. Documentation can still affect the security of
an integration. This policy routes reports for the documentation and the wider
product to the security team.

## Reporting a Vulnerability

**Do NOT open a public issue for security vulnerabilities.**

Email **security@ezclassify.com**. That address covers every EzClassify
repository and every EzClassify application, so use it whether you found the
issue in a client library, in a public marking scheme, in the REST API, or in
Studio. Include:

- What is affected: the repository, package, application, and version.
- A description of the issue and its impact.
- Steps to reproduce, with a proof of concept if you have one.
- Any suggested remediation.

You will receive an acknowledgment within **48 hours**. We follow a **90-day
coordinated disclosure** window from the date of the initial report.

## Scope

A security issue is a defect that could be exploited to compromise
confidentiality, integrity, or availability. For this repository specifically,
the realistic cases are documentation that would lead an integrator into an
insecure setup: an example that sends a credential somewhere it should not go,
an install instruction that points at a package coordinate we do not control,
or guidance that misstates where policy is evaluated.

An access decision that grants access the policy should refuse, or a marking
that comes out below the level the rules require, is a confidentiality failure.
Report those to security@ezclassify.com no matter which surface you found them
on.

These are not security issues and belong in the ordinary issue tracker:

- A typo, a broken link, or an out-of-date package coordinate.
- An access decision you disagree with, or a result that follows the documented
  rules. Those are decided by the runtime; file them on the [central EzClassify
  tracker](https://github.com/ezclassify/ezclassify/issues).
- A disagreement with a documented design choice.

If you are unsure whether something qualifies, send it to
security@ezclassify.com and we will triage it.

## Response Timeline

| Stage                  | Timeline                         |
| ---------------------- | -------------------------------- |
| Acknowledgment         | Within 48 hours                  |
| Initial assessment     | Within 5 business days           |
| Patch development      | Within 30 days for critical/high |
| Coordinated disclosure | 90 days from initial report      |

If a fix is available before the 90-day deadline, we disclose on release. If a
fix is delayed, we negotiate an extended timeline with the reporter.

## Contact

For non-vulnerability security questions, reach us at security@ezclassify.com.
