# CrewAI Cloud (crewai-cloud)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

CrewAI Cloud (CrewAI AMP) is the managed Agent Management Platform for deploying, monitoring, scaling, and governing CrewAI multi-agent workflows in production. AMP exposes a per-crew REST API for kickoff, status, inputs, and human-in-the-loop resume operations, plus webhook streaming for task, step, and crew events. The platform ships in two deployment modes — AMP Cloud (managed, multi-tenant at app.crewai.com) and AMP Factory (self-hosted on AWS, Azure, or GCP) — and layers RBAC, SSO, secrets manager federation (AWS/Azure/GCP), agent and tool repositories, a marketplace, A2A communication, automations and triggers, traces with PII redaction, and observability exports on top of the open-source CrewAI framework.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/crewai-cloud/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/crewai-cloud/refs/heads/main/apis.yml)

## Scope

- **Type:** Index

## Tags

- AI Agents
- AI Agent Platform
- Agent Orchestration
- Multi-Agent Systems
- Agent Management Platform
- Managed Agents
- Automations
- Observability
- Human In The Loop

## Timestamps

- **Created:** 2026-05-24
- **Modified:** 2026-05-24

## APIs

### CrewAI AMP REST API

Per-crew REST API exposed for every crew deployed to CrewAI AMP. Each deployed crew is reachable at https://{crew-name}.crewai.com and exposes four operations — GET /inputs to discover required input parameters, POST /kickoff to launch an execution with inputs and optional task/step/crew webhook URLs (returns a kickoff_id), GET /status/{kickoff_id} to poll execution status (running, completed, error) and retrieve per-task results, and POST /resume to deliver human feedback (approve or retry) on a task that paused for HITL review. All endpoints require Bearer token authentication using either an organization-level or user-scoped token from the AMP dashboard Status tab.

- **Human URL:** [https://docs.crewai.com/en/api-reference/introduction](https://docs.crewai.com/en/api-reference/introduction)
- **Base URL:** `https://{crew-name}.crewai.com`

#### Tags

- AI Agents
- Crew Execution
- Kickoff
- Status
- Human In The Loop

#### Properties

- [Documentation](https://docs.crewai.com/en/api-reference/introduction)
- [Documentation](https://docs.crewai.com/en/api-reference/inputs)
- [Documentation](https://docs.crewai.com/en/api-reference/kickoff)
- [Documentation](https://docs.crewai.com/en/api-reference/status)
- [Documentation](https://docs.crewai.com/en/api-reference/resume)
- [Documentation](https://docs.crewai.com/en/enterprise/guides/kickoff-crew)
- [Authentication](https://docs.crewai.com/en/api-reference/introduction)
- [OpenAPI](openapi/crewai-amp-rest-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/crewai-amp-rest-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/crewai-amp-rest-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### CrewAI AMP Webhook Streaming

Outbound event streaming for AMP crew executions. When you kick off a crew you can supply three callback URLs — taskWebhookUrl (fired after each task completes), stepWebhookUrl (fired after each agent thought/action), and crewWebhookUrl (fired when the overall crew run finishes). AMP POSTs JSON event payloads to those URLs so your systems can react to agent progress in real time, log traces externally, or chain follow-on automations.

- **Human URL:** [https://docs.crewai.com/en/enterprise/features/webhook-streaming](https://docs.crewai.com/en/enterprise/features/webhook-streaming)

#### Tags

- Webhooks
- Event Streaming
- Observability

#### Properties

- [Documentation](https://docs.crewai.com/en/enterprise/features/webhook-streaming)
- [Documentation](https://docs.crewai.com/en/enterprise/guides/webhook-automation)
- [AsyncAPI](asyncapi/crewai-amp-webhooks-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/latest)
- [Postman Collection](collections/crewai-amp-rest-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/crewai-amp-rest-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### CrewAI Enterprise MCP Server

Model Context Protocol server published by CrewAI Inc. that exposes AMP crew deployment operations and status tracking to MCP-compatible agents and IDEs. Lets Claude, Cursor, and other MCP clients list, deploy, and inspect AMP crews via the MCP standard rather than the raw REST surface.

- **Human URL:** [https://github.com/crewAIInc/enterprise-mcp-server](https://github.com/crewAIInc/enterprise-mcp-server)

#### Tags

- MCP
- Model Context Protocol
- Agents
- Deployment

#### Properties

- [Git Hub](https://github.com/crewAIInc/enterprise-mcp-server)
- [Documentation](https://docs.crewai.com/en/enterprise/guides/custom-mcp-server)
- [Postman Collection](collections/crewai-amp-rest-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/crewai-amp-rest-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Arazzo Workflows](arazzo/) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)
- [Website](https://www.crewai.com)
- [Portal](https://www.crewai.com/enterprise)
- [Sign Up](https://app.crewai.com)
- [Console](https://app.crewai.com)
- [Documentation](https://docs.crewai.com/en/enterprise/introduction)
- [Documentation](https://docs.crewai.com/)
- [L L Ms Txt](https://docs.crewai.com/llms.txt)
- [Getting Started](https://docs.crewai.com/en/enterprise/guides/deploy-to-amp)
- [API Reference](https://docs.crewai.com/en/api-reference/introduction)
- [Authentication](https://docs.crewai.com/en/api-reference/introduction)
- [Webhooks](https://docs.crewai.com/en/enterprise/features/webhook-streaming)
- [SDK](https://github.com/crewAIInc/crewai)
- [SDK](https://github.com/crewAIInc/crewai-tools)
- [C L I](https://docs.crewai.com/en/concepts/cli)
- [Tool](https://docs.crewai.com/en/enterprise/features/crew-studio)
- [Tool](https://github.com/crewAIInc/enterprise-mcp-server)
- [GitHub Organization](https://github.com/crewAIInc)
- [LinkedIn](https://www.linkedin.com/company/crewai-inc)
- [Blog](https://blog.crewai.com)
- [Forum](https://community.crewai.com)
- [Status Page](https://status.crewai.com)
- [Terms of Service](https://www.crewai.com/legal/terms-of-use)
- [Privacy Policy](https://www.crewai.com/legal/privacy-notice)
- [Trust Center](https://www.crewai.com/trust)
- [Changelog](https://docs.crewai.com/en/release-notes)
- [Plans](https://www.crewai.com/pricing)
- [Pricing](https://www.crewai.com/pricing)
- [Security And Compliance](https://www.crewai.com/trust)
- [Integrations](https://docs.crewai.com/en/enterprise/integrations)
- [Documentation](https://docs.crewai.com/en/enterprise/features/sso)
- [Documentation](https://docs.crewai.com/en/enterprise/features/rbac)
- [Documentation](https://docs.crewai.com/en/enterprise/features/secrets-manager/overview)
- [Documentation](https://docs.crewai.com/en/enterprise/features/secrets-manager/aws)
- [Documentation](https://docs.crewai.com/en/enterprise/features/secrets-manager/aws-workload-identity)
- [Documentation](https://docs.crewai.com/en/enterprise/features/secrets-manager/azure)
- [Documentation](https://docs.crewai.com/en/enterprise/features/secrets-manager/azure-workload-identity)
- [Documentation](https://docs.crewai.com/en/enterprise/features/secrets-manager/gcp)
- [Documentation](https://docs.crewai.com/en/enterprise/features/secrets-manager/gcp-workload-identity)
- [Documentation](https://docs.crewai.com/en/enterprise/features/traces)
- [Documentation](https://docs.crewai.com/en/enterprise/features/pii-trace-redactions)
- [Documentation](https://docs.crewai.com/en/enterprise/features/hallucination-guardrail)
- [Documentation](https://docs.crewai.com/en/enterprise/guides/capture_telemetry_logs)
- [Documentation](https://docs.crewai.com/en/enterprise/features/automations)
- [Documentation](https://docs.crewai.com/en/enterprise/guides/automation-triggers)
- [Documentation](https://docs.crewai.com/en/enterprise/features/flow-hitl-management)
- [Documentation](https://docs.crewai.com/en/enterprise/features/agent-repositories)
- [Documentation](https://docs.crewai.com/en/enterprise/features/marketplace)
- [Documentation](https://docs.crewai.com/en/enterprise/features/a2a)
- [Documentation](https://docs.crewai.com/en/enterprise/guides/tool-repository)
- [Documentation](https://docs.crewai.com/en/enterprise/guides/custom-mcp-server)
- [Documentation](https://docs.crewai.com/en/concepts/production-architecture)
- [Documentation](https://docs.crewai.com/en/enterprise/resources/frequently-asked-questions)
- [Plans](plans/crewai-cloud-plans-pricing.yml)
- [Rate Limits](rate-limits/crewai-cloud-rate-limits.yml)
- [Fin Ops](finops/crewai-cloud-finops.yml)
- [Features](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
**URL:** https://apievangelist.com
