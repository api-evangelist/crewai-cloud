# CrewAI Cloud

CrewAI Cloud — formally CrewAI AMP (Agent Management Platform) — is the managed, governed, and observable runtime for CrewAI multi-agent workflows. Where the open-source CrewAI framework gives you the building blocks for role-playing agents and tasks, AMP is what you reach for when you want to put those crews into production at an organization that cares about deployment, security, SSO, RBAC, secrets federation, traces, webhooks, human review, and a marketplace of reusable agents and tools.

AMP ships in two deployment modes — **AMP Cloud** (multi-tenant managed service at `app.crewai.com`) and **AMP Factory** (self-hosted on AWS, Azure, or GCP) — and exposes a small but useful per-crew REST API at `https://{crew-name}.crewai.com` for kicking off runs, polling status, listing inputs, and resuming on human feedback.

This repository profiles CrewAI Cloud as an API provider under the [API Evangelist](https://apievangelist.com) catalog, capturing the surface area, plans, rate limits, FinOps shape, vocabulary, and the workflows you'd want to wire into a governed AI control plane.

## API Surface

The per-crew REST API is documented in [`openapi/crewai-amp-rest-api-openapi.yml`](openapi/crewai-amp-rest-api-openapi.yml) and covers four operations:

| Method | Path | Purpose |
|---|---|---|
| `GET` | `/inputs` | List the input parameters the deployed crew expects. |
| `POST` | `/kickoff` | Launch a crew run with inputs and optional task/step/crew webhook URLs. Returns a `kickoff_id`. |
| `GET` | `/status/{kickoff_id}` | Poll the kickoff — `running`, `completed`, or `error` — and retrieve per-task results. |
| `POST` | `/resume` | Submit human-in-the-loop feedback (approve or retry) on a task that paused for review. |

Every request authenticates with a Bearer token issued from the AMP dashboard's Status tab. Two token flavors exist: organization-level (full crew operations) and user-scoped (limited).

Webhook event streaming is documented separately in [`asyncapi/crewai-amp-webhooks-asyncapi.yml`](asyncapi/crewai-amp-webhooks-asyncapi.yml) — three callback URLs (`taskWebhookUrl`, `stepWebhookUrl`, `crewWebhookUrl`) supplied on kickoff receive POSTed JSON payloads as the crew runs.

## What's in this Repo

| Folder | What it Holds |
|---|---|
| [`apis.yml`](apis.yml) | APIs.json profile — APIs, properties, common metadata, plans/rate-limits/FinOps pointers, features. |
| [`openapi/`](openapi) | OpenAPI 3.1 description of the AMP per-crew REST API. |
| [`asyncapi/`](asyncapi) | AsyncAPI 3.0 description of AMP webhook event streams. |
| [`json-schema/`](json-schema) | JSON Schemas for kickoff request, status response, and resume request. |
| [`json-structure/`](json-structure) | JSON Structure document marking operational roles on the kickoff entity. |
| [`json-ld/`](json-ld) | JSON-LD context binding kickoff/execution/task/agent terms to schema.org. |
| [`examples/`](examples) | End-to-end request/response examples for kickoff, status, and resume. |
| [`rules/`](rules) | Spectral ruleset enforcing AMP's documented conventions. |
| [`capabilities/`](capabilities) | Naftiko capability definitions — `shared/` per-API + workflow compositions (`crew-execution`, `human-in-the-loop-review`). |
| [`vocabulary/`](vocabulary) | Operational vocabulary covering resources, lifecycle states, deployments, integrations, triggers, and observability. |
| [`plans/`](plans) | API Commons Plans 0.1 capture of the Basic (free) and Enterprise (custom) tiers. |
| [`rate-limits/`](rate-limits) | API Commons Rate Limits 0.1 — quotas tied to monthly workflow executions. |
| [`finops/`](finops) | FOCUS-aligned mapping of how AMP charges appear in customer billing. |

## Beyond the REST API

CrewAI AMP layers a meaningful set of platform features on top of the OSS framework:

- **Crew Studio** — visual editor with AI copilot for building crews and flows without code.
- **Automations and Triggers** — kick off crews from Gmail, Google Calendar, Google Drive, OneDrive, Outlook, HubSpot, Salesforce, Slack, Microsoft Teams, and Zapier events.
- **40+ enterprise integrations** — Salesforce, HubSpot, Stripe, Shopify, Zendesk, Jira, Linear, Asana, ClickUp, Notion, Slack, Microsoft Teams, Outlook, Gmail, Google Workspace, Microsoft 365, Box, SharePoint, and GitHub.
- **Identity** — Single Sign-On with Microsoft Entra and Okta, plus RBAC and team management.
- **Secrets federation** — AWS Secrets Manager, Azure Key Vault, GCP Secret Manager, with Workload Identity Federation (OIDC) on all three clouds for credential-less access.
- **Observability** — AMP Traces with PII redaction, OpenTelemetry export, and integrations with Arize Phoenix, Braintrust, Datadog, Galileo, Langfuse, Langtrace, MLflow, Opik, Portkey, and Weave.
- **Governance** — Hallucination Guardrail, Flow HITL Management, Agent Repositories, Marketplace, A2A on AMP (agent-to-agent communication with distributed state), Tool Repository, Custom MCP Servers, and private package registries.
- **Enterprise MCP Server** — [`crewAIInc/enterprise-mcp-server`](https://github.com/crewAIInc/enterprise-mcp-server) exposes AMP deployment operations to MCP-compatible clients like Claude.

## Plans, Limits, and FinOps

CrewAI's commercial model is execution-metered. The Basic tier is free for the first 50 workflow executions per month and $0.50 per execution after that. The Enterprise tier is custom-priced and includes up to 30,000 free executions per month, unlimited maximum executions, dedicated support, on-site training, and 50 hours of development per month. See [`plans/crewai-cloud-plans-pricing.yml`](plans/crewai-cloud-plans-pricing.yml), [`rate-limits/crewai-cloud-rate-limits.yml`](rate-limits/crewai-cloud-rate-limits.yml), and [`finops/crewai-cloud-finops.yml`](finops/crewai-cloud-finops.yml) for the structured detail.

## Related

- Open-source CrewAI framework profile: [api-evangelist/crewai](https://github.com/api-evangelist/crewai)
- CrewAI Inc. GitHub: [crewAIInc](https://github.com/crewAIInc)
- Official docs: [docs.crewai.com](https://docs.crewai.com/en/enterprise/introduction)
- Pricing: [crewai.com/pricing](https://www.crewai.com/pricing)
- Enterprise marketing: [crewai.com/enterprise](https://www.crewai.com/enterprise)

## Maintainer

- Kin Lane — <info@apievangelist.com> — [apievangelist.com](https://apievangelist.com)
