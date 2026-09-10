# Security policy

## Reporting

Use GitHub's private vulnerability reporting:
[Report a vulnerability](https://github.com/UpPrj/uptimeproject/security/advisories/new). It is
enabled on this repository and keeps the report private until a fix ships.

If that is unavailable to you, email `hello@uptimeproject.org` with `SECURITY` in the subject.

Never open a public issue or discussion for a vulnerability.

## What to include

- The affected host or endpoint.
- Reproduction steps, or a request and response pair.
- What an attacker gains.
- Whether the finding is already public elsewhere.

## Scope

In scope:

| Host | What runs there |
|---|---|
| `uptimeproject.org` | Static site |
| `api.uptimeproject.org` | Public read-only API |
| `ingest.uptimeproject.org` | Authenticated probe ingest endpoint |

Out of scope:

- The services being measured. A finding against AWS, Cloudflare or any other provider on the
  leaderboard belongs to that provider's disclosure process, not this one.
- Anything on `grafana.uptimeproject.org`, which is not routable from the public internet.
- Findings that require access to a probe host or the core box.
- Missing hardening headers, TLS configuration preferences and cookie flags with no demonstrated
  impact. Send them anyway if you like, but they are handled as ordinary issues.
- Volumetric denial of service, automated scanner output with no verified finding, and social
  engineering.

Two properties worth knowing before reporting them as bugs: the API is deliberately unauthenticated
and read-only, and the measurement data is deliberately public under CC BY 4.0. Neither is a leak.

## Handling

| Stage | Target |
|---|---|
| Acknowledgement | 3 days |
| Assessment and severity | 7 days |
| Fix for a high or critical finding | 30 days |

Solo maintainer, so these are targets rather than guarantees. Coordinated disclosure after a fix is
welcome and credit is given by default. Say so if you would rather not be named.

## No bounty

This project has no revenue and pays nothing for reports. Say what you want up front if that changes
whether you report.
