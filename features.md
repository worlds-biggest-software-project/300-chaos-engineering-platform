# Chaos Engineering Platform — Feature & Functionality Survey

> Candidate #300 · Researched: 2026-05-03

## Solutions Analysed

| Tool | Type | Licence / Model | URL |
|------|------|-----------------|-----|
| Gremlin | Commercial SaaS | Proprietary | https://www.gremlin.com |
| AWS Fault Injection Service (FIS) | Cloud-managed service | Proprietary | https://aws.amazon.com/fis/ |
| Azure Chaos Studio | Cloud-managed service | Proprietary | https://azure.microsoft.com/en-us/products/chaos-studio/ |
| LitmusChaos | Open source | Apache 2.0 | https://litmuschaos.io |
| Chaos Monkey | Open source | Apache 2.0 | https://netflix.github.io/chaosmonkey/ |
| Steadybit | Commercial SaaS | Proprietary | https://steadybit.com |
| Harness Chaos Engineering | Commercial SaaS (embedded) | Proprietary | https://www.harness.io/products/chaos-engineering |
| Chaos Toolkit | Open source | Apache 2.0 | https://chaostoolkit.org |
| Pumba | Open source | Apache 2.0 | https://github.com/alexei-led/pumba |
| Grafana k6 with xk6-disruptor | Open source (extension) | AGPL / Proprietary | https://k6.io |

## Feature Analysis by Solution

### Gremlin

**Core features**
- Fault injection across diverse infrastructure types (AWS, Azure, GCP, Kubernetes, VMs, bare metal)
- Pre-built experiment templates covering CPU failures, disk/memory exhaustion, network issues, container failures, clock synchronization, DNS failures, and cloud service faults
- Granular blast radius controls enabling targeting down to specific nodes, services, or cloud regions
- SLO-based experiment gating with automatic rollback if SLIs degrade beyond thresholds
- Real-time monitoring integration with Datadog, Prometheus, PagerDuty, New Relic
- Role-based access control (RBAC) and compliance-ready audit logging
- Reliability scoring — standardized forward-looking reliability metrics based on active failure testing

**Differentiating features**
- Resilience scoring as a primary KPI, replacing lagging uptime metrics
- Enterprise-grade integration with incident management workflows
- Specialist customer success and compliance support for regulated industries (recent federal/public sector expansion)
- Passive risk detection and dependency mapping alongside active fault injection

**UX patterns**
- Dashboard-driven experiment creation and management
- Shared reports for demonstrating reliability improvements to stakeholders
- Granular safety controls reducing operational risk vs. manual fault injection

**Integration points**
- Deep integrations with monitoring platforms (Datadog, Prometheus, New Relic, PagerDuty)
- Multi-cloud API support (AWS, Azure, GCP)
- Incident management workflow hooks

**Known gaps**
- High pricing ($20k–$100k+/year) limits adoption in mid-market and startups
- Smaller than peer platforms at enterprise scale
- Limited self-service onboarding compared to open-source alternatives

**Licence / IP notes**
- Proprietary commercial software; no known patent concerns flagged in public domain

---

### AWS Fault Injection Service (FIS)

**Core features**
- Fully managed fault injection for AWS-hosted workloads
- Agent-free architecture requiring no additional software installation
- Pre-built experiment scenarios including AZ outages, power interruptions, cross-Region connectivity disruption, and partial failures
- Managed fault actions: instance termination, API throttling, database failover, and others
- CloudWatch integration for real-time metric monitoring during experiments
- IAM-based access control and experiment targeting via AWS resource tags
- API, CLI, and AWS Management Console access

**Differentiating features**
- Tight AWS-native integration with no multi-cloud overhead
- Scenario library reducing manual experiment design effort
- Low operational overhead due to fully managed service

**UX patterns**
- AWS Management Console-centric workflow
- Tag-based targeting enabling infrastructure-as-code experiment definition

**Integration points**
- CloudWatch Alarms for stop conditions
- AWS CloudTrail audit logging
- AWS SDKs for programmatic experiment management
- AWS CLI and REST API

**Known gaps**
- Limited to AWS-hosted workloads; no cross-cloud support
- Smaller fault library compared to Gremlin or Steadybit
- No Kubernetes-native abstractions; primarily compute and managed services focus

**Licence / IP notes**
- Proprietary AWS service; no known IP encumbrances

---

### Azure Chaos Studio

**Core features**
- Managed chaos engineering service for Azure resources and Azure Kubernetes Service (AKS)
- Support for VMs, AKS, App Service, Cosmos DB, Key Vault, Network Security Groups
- Fault types spanning CPU stress, network latency, complete service outages
- Azure Monitor integration for real-time metric observation
- Azure DevOps and CI/CD pipeline integration
- REST API and Azure Portal for experiment management
- Pay-per-action-minute pricing model

**Differentiating features**
- Native Azure service integration without additional agent deployment
- CI/CD pipeline integration for automated resilience validation
- Intuitive portal UI for experiment design and execution

**UX patterns**
- Azure Portal-based workflow aligned with Azure ecosystem tools
- Streamlined experiment scoping and resource selection

**Integration points**
- Azure Monitor for observability
- Azure DevOps for CI/CD automation
- Azure Kubernetes Service (AKS) for Kubernetes chaos
- Azure REST API for programmatic access

**Known gaps**
- Limited cross-cloud support (Azure-focused)
- Smaller feature set relative to Gremlin and Steadybit
- No open-source extensibility for custom faults

**Licence / IP notes**
- Proprietary Azure service; no known IP encumbrances

---

### LitmusChaos

**Core features**
- Cloud-native Kubernetes operator pattern using custom resources (ChaosEngine, ChaosExperiment, ChaosResult)
- ChaosHub: pre-built experiment repository covering pod-level (pod-delete, container-kill, pod-cpu-hog, pod-network-loss) and infra-level (node-drain, disk-loss, node-cpu-hog) experiments
- Declarative experiment definition via Kubernetes CRs
- Steady-state hypothesis validation using Litmus probes (HTTP, command execution, Prometheus query probes)
- Experiment chaining in sequence or parallel within Workflow objects
- Prometheus metrics export for real-time impact quantification
- ChaosCenter (web UI) for visual experiment management

**Differentiating features**
- CNCF-incubating project providing governance and community standards
- Kubernetes-native design with CRD-based orchestration
- Pluggable probe framework for custom steady-state validation
- Integration with CI/CD via Kubernetes events and webhooks

**UX patterns**
- GitOps-friendly YAML/CR-based configuration
- Progressive disclosure of experiment complexity through chaining and probe composition
- Community-driven extension framework

**Integration points**
- Kubernetes API and operators
- Prometheus for metrics and dashboards
- CI/CD tools via Kubernetes event triggers
- Pluggable chaos library framework for extensibility

**Known gaps**
- ChaosCenter UI still maturing; simpler than commercial platforms
- Requires Kubernetes cluster; limited to container orchestration (not bare metal or traditional VMs)
- Community-maintained libraries may lag behind commercial fault coverage
- No built-in incident correlation or blast-radius prediction

**Licence / IP notes**
- Apache 2.0 open-source licence, CNCF-incubating project; no known IP encumbrances

---

### Chaos Monkey (Netflix)

**Core features**
- Random instance termination in production to force engineer resilience mindset
- Time-based scheduling (typically business hours) for controlled testing windows
- Tag-based filtering to target only eligible systems
- Simple, focused scope: randomly shuts down VM instances or containers

**Differentiating features**
- Foundational reference implementation; historical importance in chaos engineering adoption
- Minimal operational complexity due to narrow scope
- Forced architectural resilience; by design, does not allow teams to ignore failure tolerance

**UX patterns**
- Lightweight deployment requiring minimal configuration
- Predictable, narrow failure mode focuses teams on redundancy design

**Integration points**
- Minimal integrations; operates directly on compute infrastructure
- Automation frameworks can trigger based on scheduled windows

**Known gaps**
- Limited fault scope (instance termination only); does not cover network faults, disk failures, or application-level issues
- No real-time observability or experiment observability built-in
- Superseded conceptually by Simian Army; modern chaos requires broader fault injection
- No blast-radius controls or safety mechanisms; relies on architectural redundancy to prevent cascades

**Licence / IP notes**
- Apache 2.0 open-source licence; no known IP encumbrances

---

### Steadybit

**Core features**
- Visual drag-and-drop experiment builder with timeline-based canvas
- Attack library covering AWS, Kubernetes, and JVM targets
- Landscape Explorer providing visual infrastructure topology discovery and grouping
- Blast radius controls enabling granular targeting and automated rollbacks
- Pre-built experiment templates for common use cases
- Extension framework allowing custom attacks and integrations
- Open-source extension architecture enabling community contributions

**Differentiating features**
- Modern UX with timeline-based visual experiment design; easier than CLI-based tools
- Landscape Explorer for pre-experiment topology visualization and resource grouping
- Open extension framework vs. Gremlin's proprietary approach
- Recently introduced MCP Server for LLM-based experiment insights (as of June 2025)

**UX patterns**
- Drag-and-drop experiment builder with visual feedback
- Infrastructure topology visualization enabling confident experiment scoping
- Progressive disclosure through timeline-based interface
- Extensibility framework for teams with custom requirements

**Integration points**
- AWS, Kubernetes, JVM attack libraries
- Custom attack extensions via open framework
- MCP Server for AI/LLM-based workflows
- Monitoring platform integrations (implied via visual builder)

**Known gaps**
- Smaller enterprise customer base than Gremlin
- Pricing and feature tiering less transparent than competitors
- Smaller community and ecosystem relative to Gremlin or open-source alternatives

**Licence / IP notes**
- Proprietary commercial software; extension framework is open-source compatible. No known patent concerns.

---

### Harness Chaos Engineering

**Core features**
- 200+ pre-built faults across Kubernetes, cloud platforms (AWS/Azure/GCP), Linux, Windows, and application runtimes
- Parallel fault execution (e.g., CPU fault + Memory fault simultaneously) to mimic real-world cascading failures
- Parallel experiment execution for testing complex multi-failure scenarios
- GitOps and CI/CD integration with declarative YAML experiment definitions
- Resilience probes for programmatic steady-state observation via APM and application integrations
- Resilience scoring for tracking and tuning experiment impact
- GameDay feature for team-based resilience exercises with repeatable templates
- Automatic microservice dependency discovery and coverage gap identification
- Advanced guardrails: ChaosGuard and Admission Controllers to prevent unsafe experiments
- OPA and custom policy enforcement for organizational controls

**Differentiating features**
- Embedded module within broader Harness platform (CI/CD, Feature Flags, etc.); convenient for existing Harness customers
- Automatic dependency discovery reducing manual topology mapping
- GameDay feature for team resilience training
- Advanced policy enforcement via OPA

**UX patterns**
- Declarative YAML-based experiment definition for GitOps workflows
- Integrated pipeline approvals and notifications
- Parallel execution canvas reducing experiment execution time

**Integration points**
- CI/CD pipelines (native Harness integration)
- APM and application monitoring tools
- Policy as Code (OPA) for governance
- Kubernetes and cloud platform operators

**Known gaps**
- Less specialist than Gremlin or Steadybit if using Harness solely for chaos
- Smaller than Gremlin at enterprise scale
- Learning curve for teams new to Harness ecosystem

**Licence / IP notes**
- Proprietary commercial software; no known IP encumbrances

---

### Chaos Toolkit

**Core features**
- Declarative experiment definition using YAML/JSON files enabling version control and GitOps workflows
- Modular action and probe framework supporting reusable fault definitions
- Steady-state hypothesis specification for expected system behavior under normal conditions
- Open API enabling extensibility for any system via custom drivers
- Multi-platform support with drivers for Kubernetes, AWS, Google Cloud, Azure, and other tools (including Gremlin)
- Randomization and scheduling for recurring automated stress testing
- Rollback section for post-fault cleanup and recovery
- Lightweight Python implementation

**Differentiating features**
- Highly scriptable and code-centric approach; experiments are YAML/JSON files in version control
- Extensibility at all levels (actions, probes, drivers) via Open API
- No proprietary UI or vendor lock-in; pure declaration and CLI-based execution
- Integration with heterogeneous systems through pluggable driver architecture

**UX patterns**
- Code-first development model; experiments authored as YAML/JSON alongside application code
- Minimal operational overhead due to lightweight architecture
- Requires significant engineering effort; designed for platform engineers and SREs

**Integration points**
- Kubernetes operators and APIs
- Cloud provider APIs (AWS, Azure, GCP) via pluggable drivers
- Gremlin and other chaos tools via extension drivers
- Monitoring and observability via custom probe definitions

**Known gaps**
- No built-in UI; requires command-line and YAML authoring
- Lacks commercial support and vendor roadmap commitments
- Requires significant self-service engineering effort to build fault libraries and integrations
- No blast-radius prediction or real-time safety mechanisms built-in; safety relies on hypothesis validation

**Licence / IP notes**
- Apache 2.0 open-source licence; no known IP encumbrances

---

### Pumba

**Core features**
- Container chaos targeting Docker, containerd, and Podman
- Container lifecycle operations: kill, stop, pause, remove containers
- Network fault injection: delays, packet loss, bandwidth limitations using Linux tc (traffic control) with netem queueing discipline
- Resource stress testing: CPU, memory, and disk I/O stress on containers
- Lightweight binary deployment or containerized execution
- Tag-based container selection for targeted testing

**Differentiating features**
- Focused scope on container-level chaos; extremely lightweight and fast
- Network emulation via Linux kernel tc, providing realistic network failure simulation
- Runs as standalone binary or within Docker without external dependencies

**UX patterns**
- CLI-based command execution; simple, direct control
- No UI or declarative files; immediate, ad-hoc testing capability

**Integration points**
- Docker API and socket
- Linux kernel networking (tc/netem) for fault injection
- Minimal integrations with external observability tools

**Known gaps**
- Scope limited to Docker container network and resource faults
- No Kubernetes-native abstractions; requires Docker daemon access
- No built-in monitoring or observability integration
- No pre-built scenarios or experiment templates
- Community-maintained; smaller feature velocity than commercial platforms

**Licence / IP notes**
- Apache 2.0 open-source licence; no known IP encumbrances

---

### Grafana k6 with xk6-disruptor

**Core features**
- Load testing and fault injection combined in a single JavaScript-based test framework
- xk6-disruptor: extension providing fault injection for HTTP and gRPC requests
- Fault types: error injection and latency injection into Kubernetes Pods or Services
- JavaScript API for test authoring, enabling fault patterns to be expressed alongside load scenarios
- Integration with k6's performance testing features and reporting
- No separate agent or operator fleet required; disruptor runs within k6 test execution

**Differentiating features**
- Unique combination of load testing and chaos in a single tool
- JavaScript authoring model familiar to modern developers
- Direct request-level fault injection without separate infrastructure components
- Lightweight compared to platform-based solutions

**UX patterns**
- JavaScript test scripts defining both load and chaos patterns
- Familiar JavaScript/Node.js development model
- Minimal operational overhead due to agent-free architecture

**Integration points**
- Kubernetes Pods and Services for fault targeting
- k6 cloud and reporting infrastructure
- Grafana dashboards for k6 metrics

**Known gaps**
- Kubernetes-only; no support for other infrastructure types (VMs, cloud managed services)
- Focus on request-level faults; no OS-level or infrastructure-level fault injection
- Community-maintained extension; less mature than Gremlin or Steadybit
- Limited blast-radius controls or enterprise safety features
- Smaller ecosystem compared to dedicated chaos engineering platforms

**Licence / IP notes**
- xk6-disruptor is AGPL-licensed open-source; k6 core is proprietary with open-source SDKs. Licensing combinations may be complex for commercial deployment.

---

## Cross-Cutting Feature Themes

### Table-Stakes Features

- **Fault injection across diverse failure types**: All platforms support multiple fault categories (network, compute, storage, application-level)
- **Pre-built experiment templates or libraries**: Essential for reducing setup time and educating teams on relevant faults
- **Targeting and blast radius controls**: All platforms offer tag-based or resource-based experiment scoping to limit impact
- **Real-time observability during experiments**: Monitoring integration (CloudWatch, Prometheus, Datadog, etc.) is a baseline expectation
- **Experiment result tracking and reporting**: Dashboards, result summaries, and pass/fail indicators are standard
- **Multi-cloud or multi-infrastructure support** (or clear positioning for cloud/Kubernetes/Docker specificity)
- **Safety mechanisms**: Stop conditions, automatic rollbacks, or RBAC to prevent runaway faults

### Differentiating Features

- **Visual, no-code experiment builders** (Gremlin, Steadybit, Azure Chaos Studio): Enable non-specialists to design experiments; significantly improve adoption
- **Dependency discovery and topology mapping** (Gremlin, Harness, Steadybit): Automatically infer blast radius and uncover hidden service dependencies
- **Resilience scoring and forward-looking KPIs** (Gremlin, Harness): Replace lagging uptime metrics with predictive reliability measurement
- **Open extension frameworks** (LitmusChaos, Chaos Toolkit, Steadybit): Allow organizations to add custom faults or integrations without vendor lock-in
- **GitOps and CI/CD automation** (Chaos Toolkit, Harness, LitmusChaos): Enable automated resilience validation in deployment pipelines as a "test gate"
- **GameDay and team-based exercises** (Harness): Structured organizational resilience training beyond automated testing
- **Advanced policy enforcement** (Harness via OPA, Gremlin with RBAC): Governance and compliance at organizational scale

### Underserved Areas / Opportunities

- **AI-driven experiment hypothesis generation**: No platform currently uses LLMs or ML to automatically propose high-impact chaos experiments based on system architecture and incident history
- **Intelligent blast-radius prediction**: Existing platforms rely on manual topology mapping or passive discovery; predictive blast-radius modeling before experiment execution would enable safer, broader testing
- **Failure mode discovery for AI-native systems**: LLM-based components, vector DBs, multi-model orchestration, and RAG pipelines have entirely new failure modes (hallucination cascades, token exhaustion, tool-call loops) not yet covered by existing chaos libraries
- **Autonomous game day orchestration**: No platform offers an AI agent that plans, executes, and interprets a full game day scenario end-to-end with real-time scope adjustment
- **Continuous resilience regression testing**: Post-deployment automated re-running of relevant chaos experiments to detect resilience regressions before they reach production (only Harness has partial CI/CD automation)
- **Developer-friendly local chaos simulation**: Most platforms target infrastructure or SRE teams; opportunities for developer-local chaos testing (e.g., embedded in test suites)
- **Cross-cloud chaos orchestration**: No platform orchestrates chaos uniformly across AWS, Azure, and GCP without vendor-specific configuration; this is valuable for multi-cloud deployments
- **Real-time experiment adaptation**: Existing platforms run static experiments; adapting fault parameters in real-time based on observed system responses would enable more efficient testing

### AI-Augmentation Candidates

- **Automatic experiment proposal**: Given system dependency graphs, service inventory, and historical incidents, generate ranked lists of high-impact chaos experiments
- **Intelligent probe authoring**: AI-generated steady-state hypothesis probes based on service SLOs, API contracts, and monitoring metrics
- **Blast-radius modeling**: Pre-execution prediction of customer-facing impact (latency, error rate, availability) for proposed experiments
- **Experiment result interpretation**: Summarize and explain experiment outcomes, correlate observed failures with architectural weaknesses, and recommend mitigations
- **Failure mode synthesis**: Identify novel failure combinations likely to expose system weaknesses based on dependency analysis and incident patterns
- **Automatic incident -> experiment conversion**: Automatically convert post-mortems and incident data into reproducible chaos experiments to prevent recurrence

---

## Legal & IP Summary

All commercial platforms (Gremlin, Steadybit, Harness, AWS FIS, Azure Chaos Studio) operate under standard proprietary software licences with no patent claims flagged in publicly available sources. LitmusChaos, Chaos Toolkit, Chaos Monkey, and Pumba are Apache 2.0 open-source projects with no known IP encumbrances, though LitmusChaos is governed by the CNCF as an incubating project, adding governance and community standards without IP restrictions. Grafana k6's xk6-disruptor extension is AGPL-licensed, which may introduce copyleft obligations in commercial deployments; careful licence review is recommended if bundling k6-based tooling into a proprietary product.

No significant patent risks, copyright conflicts, or licence compatibility issues were identified during research. All licences are compatible with standard open-source project creation.

---

## Recommended Feature Scope

### Must-have (MVP)

- **Fault injection engine** supporting 10–15 core failure types (pod/container/instance termination, network latency/packet loss, CPU/memory resource exhaustion, disk I/O stress) across at least Kubernetes and one major cloud (AWS or Azure)
- **Declarative experiment definition** (YAML/JSON) enabling GitOps workflows and version control
- **Experiment orchestration** allowing sequential and parallel fault execution within a single scenario
- **Steady-state hypothesis validation** via probes (HTTP, command execution, custom metrics)
- **Real-time monitoring integration** with Prometheus and/or CloudWatch to observe fault impact
- **Blast radius controls** (tag-based or resource-based targeting) to scope experiments safely
- **Experiment result reporting** with pass/fail verdicts, metric comparisons, and audit logs
- **Role-based access control** (RBAC) for team-based usage and compliance

### Should-have (v1.1)

- **Web UI for visual experiment design** (timeline or canvas-based builder) reducing authoring complexity for non-engineers
- **Pre-built experiment library** (Chaos Hub equivalent) covering common failure scenarios by domain
- **Dependency discovery and topology mapping** to automatically infer services and their relationships
- **Resilience scoring** for forward-looking reliability metrics tracking improvement over time
- **CI/CD integration** enabling automated chaos testing as a pipeline gate or post-deployment validation
- **Open extension framework** allowing custom faults, probes, and integrations without vendor lock-in
- **Stop conditions** (CloudWatch Alarms or custom thresholds) to halt runaway experiments

### Nice-to-have (backlog)

- **AI-driven experiment proposal** using system architecture and incident history to recommend high-impact scenarios
- **Autonomous game day orchestration** for team-based resilience exercises
- **Cross-cloud chaos** (simultaneous faults across AWS, Azure, GCP) for multi-cloud deployments
- **Advanced policy enforcement** via OPA or policy-as-code for organizational compliance
- **Real-time experiment adaptation** adjusting fault parameters based on observed system response
- **Failure mode discovery for AI-native systems** (LLM components, vector DBs, RAG pipelines)
- **Developer-local chaos simulation** embedded in test suites for CI/CD and development workflows

---

## Sources

- [Gremlin — Chaos Engineering Platform](https://www.gremlin.com/chaos-engineering)
- [AWS Fault Injection Service Features](https://aws.amazon.com/fis/features/)
- [Azure Chaos Studio — Chaos Engineering Experimentation](https://azure.microsoft.com/en-us/products/chaos-studio/)
- [LitmusChaos — Open Source Chaos Engineering Platform](https://litmuschaos.io/)
- [Chaos Monkey — Netflix](https://netflix.github.io/chaosmonkey/)
- [Steadybit — Chaos Engineering Tool](https://steadybit.com/)
- [Harness Chaos Engineering Features](https://www.harness.io/products/chaos-engineering/features)
- [Chaos Toolkit — The Chaos Engineering Toolkit](https://chaostoolkit.org/)
- [Pumba — Chaos Testing for Containers](https://github.com/alexei-led/pumba)
- [Grafana k6 — xk6-disruptor Extension](https://k6.io/blog/democratize-chaos-testing/)
