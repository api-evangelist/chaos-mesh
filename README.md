# Chaos Mesh

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Chaos Mesh is a CNCF graduated cloud-native chaos engineering platform that orchestrates chaos experiments on Kubernetes to test system resilience and reliability. It exposes Kubernetes Custom Resource Definitions (CRDs) for a wide range of chaos kinds (network, pod, IO, stress, DNS, time, kernel, JVM, HTTP), along with a Chaos Dashboard web UI backed by a REST API for creating, managing, and monitoring chaos experiments and workflows. Chaos Mesh integrates with Kubernetes, Argo Workflows, Prometheus, Grafana, and CI/CD pipelines to run experiments safely in staging and production environments.

**Areas:** Chaos Engineering · Cloud-Native · CNCF · Kubernetes · Observability · Open Source · Reliability · Resilience · Testing

## Chaos Mesh on APIs.io

Everything profiled for Chaos Mesh is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/chaos-mesh/](https://apis.io/providers/chaos-mesh/)** — or go straight to one of the APIs or properties below.

### APIs (7)

- [Chaos Mesh Archives API](https://apis.io/apis/chaos-mesh/chaos-mesh-archives-api/) — Access archived (completed or deleted) experiments, schedules, and workflows
- [Chaos Mesh Common API](https://apis.io/apis/chaos-mesh/chaos-mesh-common-api/) — Utility endpoints for cluster metadata, namespaces, and configuration
- [Chaos Mesh Events API](https://apis.io/apis/chaos-mesh/chaos-mesh-events-api/) — Query chaos experiment events and audit logs
- [Chaos Mesh Experiments API](https://apis.io/apis/chaos-mesh/chaos-mesh-experiments-api/) — Create, manage, pause, and delete chaos experiments
- [Chaos Mesh Schedules API](https://apis.io/apis/chaos-mesh/chaos-mesh-schedules-api/) — Create and manage scheduled chaos experiments
- [Chaos Mesh Templates API](https://apis.io/apis/chaos-mesh/chaos-mesh-templates-api/) — Manage reusable status check templates for workflows
- [Chaos Mesh Workflows API](https://apis.io/apis/chaos-mesh/chaos-mesh-workflows-api/) — Create and manage chaos engineering workflows with multiple steps

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Chaos Mesh Agentic Access](https://apis.io/agentic-access/chaos-mesh/chaos-mesh-agentic-access/)

#### JSON Schema (1)

The data models the API reads and writes.

- [Chaos Mesh Experiment](https://apis.io/schemas/chaos-mesh/chaos-mesh-experiment/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Chaos Mesh Context](https://apis.io/jsonld/chaos-mesh/chaos-mesh-context/)

#### Collections (9)

Postman and Open Collection request collections.

- [Chaos Mesh Dashboard Archives API](https://apis.io/collections/chaos-mesh/open-chaos-mesh-archives-api/)
- [Chaos Mesh Dashboard Archives Common API](https://apis.io/collections/chaos-mesh/open-chaos-mesh-common-api/)
- [Chaos Mesh Dashboard API](https://apis.io/collections/chaos-mesh/open-chaos-mesh-dashboard/)
- [Chaos Mesh Dashboard API](https://apis.io/collections/chaos-mesh/open-chaos-mesh-dashboard-api/)
- [Chaos Mesh Dashboard Archives Events API](https://apis.io/collections/chaos-mesh/open-chaos-mesh-events-api/)
- [Chaos Mesh Dashboard Archives Experiments API](https://apis.io/collections/chaos-mesh/open-chaos-mesh-experiments-api/)
- [Chaos Mesh Dashboard Archives Schedules API](https://apis.io/collections/chaos-mesh/open-chaos-mesh-schedules-api/)
- [Chaos Mesh Dashboard Archives Templates API](https://apis.io/collections/chaos-mesh/open-chaos-mesh-templates-api/)
- [Chaos Mesh Dashboard Archives Workflows API](https://apis.io/collections/chaos-mesh/open-chaos-mesh-workflows-api/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Chaos Mesh — jsonschema rules](https://apis.io/rules/chaos-mesh/chaos-mesh-jsonschema-spectral-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Chaos Mesh Authentication](https://apis.io/security/chaos-mesh/chaos-mesh-authentication/)
- [Chaos Mesh Domain Security](https://apis.io/security/chaos-mesh/chaos-mesh-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Chaos Mesh Plans Pricing](https://apis.io/plans/chaos-mesh/chaos-mesh-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Chaos Mesh Rate Limits](https://apis.io/rate-limits/chaos-mesh/chaos-mesh-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Chaos Mesh Finops](https://apis.io/finops/chaos-mesh/chaos-mesh-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://chaos-mesh.org/)
- [Documentation](https://chaos-mesh.org/docs/)
- [Getting started](https://chaos-mesh.org/docs/quick-start/)
- [Changelog](https://github.com/chaos-mesh/chaos-mesh/blob/master/CHANGELOG.md)
- [Blog](https://chaos-mesh.org/blog/)

## API Evangelist rating

**Kin Score 42.2** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 57.1 |
| Contract quality | 60.2 |
| Contract governance | 9.8 |
| Operational transparency | 39.5 |
| Developer ergonomics | 38.1 |
| Access clarity | 7.9 |

**Agent readiness 16.9** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | — |
| OpenAPI Examples | — |
| Rate Limit Signal | derived (partial credit) |
| Event Surface Described | — |
| Agent Skills | — |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | — |

**Regulatory alignment 16.7** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/chaos-mesh/](https://apis.io/providers/chaos-mesh/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Chaos Mesh: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/chaos-mesh/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
