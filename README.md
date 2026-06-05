# CrewAI Cloud (crewai-cloud)

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
