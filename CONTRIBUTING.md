# Contributing

There is no code in this repository and no pull requests to open. The measurement pipeline is
private, for the reason given in the [README](README.md#what-this-repo-is-for). What this repository
takes is reports, and a report is only useful if it is checkable.

## Which channel

| Report | Channel |
|---|---|
| Site or API defect | Issue, `Bug report` |
| A figure you believe is wrong | Issue, `Data dispute` |
| A provider or service to add | Issue, `Provider request` |
| A change you would like | Issue, `Feature request` |
| A question, or an argument about methodology | Discussions |
| A security vulnerability | Private advisory, see [SECURITY.md](SECURITY.md). Never an issue. |

Blank issues are disabled. Pick the template that matches; the fields on it are the fields needed to
reproduce the problem.

## Data disputes

The most valuable report this project receives, and the one most often unusable. To act on a dispute
the following are needed:

1. **Service** as it appears on the site, with the URL of its page.
2. **Time window in UTC**, with a start and an end. "Yesterday afternoon" cannot be queried.
3. **What our data says** and **what you believe is true**, as two separate statements.
4. **Evidence.** A provider status page entry or postmortem link, your own monitoring, or `curl -v`
   output with timestamps.

Three outcomes are possible, and the third is common enough to state up front:

- The measurement was wrong. It gets corrected, and the cause is named in the issue.
- The measurement was right and the disagreement is a methodology one. Both readings can be
  correct: a provider status page reports the internal state of provider-owned systems, while these
  probes report external reachability from five specific networks. A regional transit fault has no
  internal signal and a real customer impact.
- The measurement was right and the methodology already covers the case, in which case the issue
  closes with a link to the relevant section rather than a change.

Point 2 of [the methodology FAQ](https://uptimeproject.org/methodology/) covers the divergence
between provider status pages and external measurement in more detail.

## Provider requests

A request is actionable when it names the exact endpoint to check, not just the company. `Add
Vercel` is a wish; `Add Vercel, category dev infra, check https://vercel.com/api/... which returns
200 unauthenticated` is a task.

Requirements for a service to be added:

- A stable, unauthenticated endpoint that answers on a predictable status code. Anything requiring
  an account, a paid tier or a signed request is out.
- Enough traffic that its reliability is of general interest. This is not a monitoring service for
  individual sites.
- No terms of service prohibiting automated requests at the cadences on the methodology page.

Not every accepted request ships. The registry is a fixed cost per check, and additions are batched.

## Response expectations

One maintainer, evenings and weekends, occasionally a week with nothing. Rough targets, not an SLA:

| | Target |
|---|---|
| First response on a data dispute | 3 days |
| First response on anything else | 1 week |
| Security report acknowledgement | 3 days, see [SECURITY.md](SECURITY.md) |

An issue with no response after two weeks has been missed rather than ignored. Bump it.

Issues closed as `wont-fix` get a reason. Issues sitting on `needs-info` for 30 days close
automatically and reopen the moment the information arrives.

## Conduct

The [Code of Conduct](CODE_OF_CONDUCT.md) applies to issues, discussions and email. Disagreeing with
a measurement is expected. Accusing the project of taking money to publish it, without evidence, is
not.
