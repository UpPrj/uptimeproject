# UptimeProject

Independent uptime measurement for cloud providers, CDNs, DNS providers, object storage, developer
infrastructure, AI APIs, email services and payment processors. Measured from outside each
provider's own network, ranked publicly, published under an open licence.

**[uptimeproject.org](https://uptimeproject.org)**

## What gets measured, and how

Probe agents in Europe, North America and Asia-Pacific, spread across four hosting providers, run
HTTP, DNS, TLS and object-storage checks on per-check cadences from once a minute to once an hour.
Results stream to a single TimescaleDB instance, where continuous aggregates produce the per-minute,
per-hour and per-day rollups the site and API read from.

A service is `up` in a given minute when a strict majority of the probes that reported saw it
succeed, `down` when none did, and `degraded` in between. Minutes with fewer than three reporting
probes are `unknown` and excluded from the availability denominator rather than counted either way.

Probe locations, service and check counts, status thresholds and the reasoning behind each rule:
[uptimeproject.org/methodology](https://uptimeproject.org/methodology/).

## Data and API

- Public read-only API: `https://api.uptimeproject.org/v1`, spec at
  [`/v1/openapi.json`](https://api.uptimeproject.org/v1/openapi.json), reference at
  [uptimeproject.org/docs/api](https://uptimeproject.org/docs/api/).
- Measurement data is licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Use it,
  redistribute it, build on it, with attribution and a link back.
- No authentication, no key, no rate-limit tier. Responses are edge-cached for 5 minutes.

## What this repo is for

This is the public front door. The code that runs the measurement (probe agent, ingest API, public
API, site, service registry, infrastructure) lives in private repositories, because the project's
value is the independence of the numbers and a solo maintainer cannot review outside contributions
to a measurement pipeline without weakening that.

So there is nothing here to send a pull request against. There is somewhere to report a problem:

| You want to | Go to |
|---|---|
| Report a bug on the site or API | [Bug report](https://github.com/UpPrj/uptimeproject/issues/new?template=bug-report.yml) |
| Dispute a measurement or an availability figure | [Data dispute](https://github.com/UpPrj/uptimeproject/issues/new?template=data-dispute.yml) |
| Ask for a provider or service to be added | [Provider request](https://github.com/UpPrj/uptimeproject/issues/new?template=add-provider.yml) |
| Suggest a feature or a change | [Feature request](https://github.com/UpPrj/uptimeproject/issues/new?template=feature-request.yml) |
| Ask a question, or argue about methodology | [Discussions](https://github.com/UpPrj/uptimeproject/discussions) |
| Report a security vulnerability | [SECURITY.md](SECURITY.md) |

What each report needs to be actionable is in [CONTRIBUTING.md](CONTRIBUTING.md). Data disputes in
particular are welcome and get priority, but they need a UTC time window and evidence.

## Independence

Built and maintained by one person, funded out of pocket. No investors, no provider sponsorships, no
advertising. Affiliate links may appear on the site for consumer-side commissions, and they never
influence a ranking: the rankings come out of the database, and the database does not know which
providers pay.

If a provider disputes a figure, the dispute goes through the same public issue tracker as everyone
else's.

## Contact

`hello@uptimeproject.org` for anything that does not belong in a public issue.
