# Chaos Engineering Platform

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An AI-native, open-source chaos engineering platform for fault injection, blast-radius analysis, and forward-looking resilience scoring across cloud, Kubernetes, and AI-native systems.

The Chaos Engineering Platform helps SRE teams, platform engineers, and engineering leaders validate the resilience of distributed systems through hypothesis-driven failure experiments. It combines a multi-infrastructure fault injection engine with predictive blast-radius modelling and AI-generated experiment hypotheses, targeting both conventional cloud workloads and the new failure modes introduced by LLM-based components.

---

## Why Chaos Engineering Platform?

- **Commercial leaders are expensive.** Gremlin typically costs $20,000–$100,000+/year, putting mature chaos engineering out of reach for mid-market and startup teams.
- **Cloud-native services are siloed.** AWS Fault Injection Service and Azure Chaos Studio offer low-overhead managed chaos but lock teams into a single cloud and provide smaller fault libraries than Gremlin or Steadybit.
- **Open-source tooling demands heavy lifting.** LitmusChaos, Chaos Toolkit, and Pumba are free and flexible, but require significant self-service engineering effort, with maturing UIs and limited blast-radius prediction.
- **Existing platforms have no AI-native coverage.** No incumbent uses LLMs to propose experiments, predict blast radius, or test failure modes specific to LLM-based components, vector DBs, and RAG pipelines.
- **Resilience scoring is becoming the executive KPI.** Forward-looking reliability scores based on active failure testing are replacing lagging uptime metrics — but this capability is concentrated in the most expensive commercial tiers.

---

## Key Features

### Fault Injection & Experiment Orchestration

- Fault injection across 10–15 core failure types: pod, container, and instance termination; network latency and packet loss; CPU, memory, and disk I/O stress
- Coverage spanning Kubernetes plus at least one major cloud (AWS or Azure) at MVP, with an extension path to multi-cloud
- Sequential and parallel fault execution within a single scenario to mimic real-world cascading failures
- Declarative experiment definition in YAML/JSON for GitOps workflows and version control

### Safety, Targeting & Governance

- Tag-based and resource-based blast-radius controls to scope experiments precisely
- Stop conditions tied to monitoring thresholds (e.g. CloudWatch Alarms, Prometheus queries) to halt runaway experiments
- Steady-state hypothesis validation via HTTP, command execution, and custom metric probes
- Role-based access control (RBAC) for team usage and compliance audit logging

### Observability & Reporting

- Real-time monitoring integration with Prometheus and CloudWatch during experiments
- Experiment result reporting with pass/fail verdicts, metric comparisons, and audit logs
- Resilience scoring as a forward-looking reliability KPI tracked across deployments

### Developer & Platform Workflows

- CI/CD integration enabling chaos experiments as deployment gates or post-deploy validation
- Web UI for visual, timeline-based experiment design alongside YAML authoring
- Pre-built experiment library (Chaos Hub equivalent) covering common failure scenarios
- Dependency discovery and topology mapping to surface hidden service relationships

### Extensibility

- Open extension framework for custom faults, probes, and integrations
- Pluggable driver architecture for new infrastructure targets without vendor lock-in

---

## AI-Native Advantage

The platform uses AI to close gaps that no incumbent currently addresses: analysing system architecture, dependency graphs, and historical incident data to **automatically propose ranked chaos experiments**; modelling downstream dependencies to **predict blast radius before execution**; running an **autonomous game day orchestrator** that plans, executes, and interprets full scenarios end-to-end with real-time scope adjustment; and providing **purpose-built experiments for AI-native systems** — prompt injection cascades, context-window exhaustion, and tool-call error propagation in LLM-based components.

---

## Tech Stack & Deployment

The platform is designed for self-hosted deployment on Kubernetes with declarative experiment definitions managed as code. It aligns with the **Principles of Chaos Engineering** (chaosengineering.io), supports **GameDays** as a first-class organisational practice, and integrates with **SRE error-budget and SLO** workflows. Architectural inspiration is drawn from CNCF chaos engineering projects (notably LitmusChaos, which uses a Kubernetes operator pattern with ChaosEngine, ChaosExperiment, and ChaosResult custom resources). Integrations target Prometheus, CloudWatch, and standard CI/CD tooling.

---

## Market Context

The chaos engineering tools market was valued at approximately **$2.37 billion in 2025** and is projected to reach **$2.56 billion in 2026**, with long-range forecasts of 8–24% CAGR through 2030–2033 (Cognitive Market Research; MarketsandMarkets, 2026). Incumbent pricing ranges from custom enterprise contracts at $20,000–$100,000+/year (Gremlin) to pay-per-action-minute cloud services (AWS FIS, Azure Chaos Studio) and free open-source tools that require significant engineering investment. Primary buyers are SRE teams at high-availability services (fintech, eCommerce, streaming), platform engineers embedding chaos into CI/CD, and CTOs in regulated industries demonstrating operational resilience for compliance audits.

---

## Project Status

> This project is in the **research and specification phase**.  
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context.
