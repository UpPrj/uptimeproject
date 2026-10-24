# UptimeProject

Independent uptime measurement for cloud providers, CDNs, DNS providers, object storage, developer
infrastructure, AI APIs, email services and payment processors. Measured by independent probes,
ranked publicly, published under an open licence.

**[uptimeproject.org](https://uptimeproject.org)**

## What gets measured, and how

Probe agents in Europe, North America and Asia-Pacific, spread across four hosting providers, run
HTTP, DNS, TLS and object-storage checks on per-check cadences from once a minute to once an hour.
Results stream to a single TimescaleDB instance, where continuous aggregates produce the per-minute,
per-hour and per-day rollups the site and API read from.

Each service has one or more primary checks, and only primary checks vote; TLS certificate checks
are recorded but do not decide availability. In each minute, a primary check is `up` when a strict
majority of voting probes saw it succeed, `down` when none did, `degraded` in between, and
`unknown` with fewer than three voting probes.

A service takes the worst of its primary checks and is `unknown` only when all of them are.
`unknown` minutes are excluded from the availability denominator rather than counted either way.

- A probe hosted on a provider's network does not vote on that provider.
- A probe that fails at least 30% of its checks in a minute abstains for that minute, so a fault on
  the probe's side is not counted as an outage.
- Minutes measured before these rules took effect keep the earlier rule, under which any passing
  check counted the probe as up.

Probe locations, service and check counts, status thresholds and the reasoning behind each rule:
[uptimeproject.org/methodology](https://uptimeproject.org/methodology/).

## Data and API

- Public read-only API: `https://api.uptimeproject.org/v1`, spec at
  [`/v1/openapi.json`](https://api.uptimeproject.org/v1/openapi.json), reference at
  [uptimeproject.org/docs/api](https://uptimeproject.org/docs/api/).
- Measurement data is licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Use it,
  redistribute it, build on it, with attribution and a link back.
- No authentication, no key, no rate-limit tier. Responses are edge-cached for 5 minutes.
- Clients on datacenter networks may get a Cloudflare bot challenge from the API. AI agents on cloud
  hosts can use the read-only MCP server at `https://uptimeproject-mcp.webnox.workers.dev/mcp`
  (60 requests per minute per IP); desktop agents can use `https://mcp.uptimeproject.org/mcp`.

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
