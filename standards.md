# Standards & API Reference

> Project: Chaos Engineering Platform · Generated: 2026-05-03

## Industry Standards & Specifications

### ISO Standards

| Standard | Title | Relevance |
|----------|-------|-----------|
| ISO 26262 | Functional Safety for Electrical/Electronic/Programmable Systems | Establishes fault injection as a required validation technique for safety-critical systems; specifies failure rate thresholds (e.g., < 10 FIT for ASIL D systems). Relevant for chaos engineering applied to regulated industries (automotive, aerospace, medical devices). |
| ISO 25010:2023 | Software Product Quality Model | Defines software quality characteristics including reliability and robustness; chaos engineering directly addresses reliability metrics. Provides framework for measuring quality impact of chaos testing. |

### W3C & IETF Standards

| Standard | Title | Relevance | URL |
|----------|-------|-----------|-----|
| RFC 7231 | Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content | Foundational HTTP semantics standard for REST-based chaos experiment APIs. | https://datatracker.ietf.org/doc/html/rfc7231 |
| RFC 6749 | OAuth 2.0 Authorization Framework | Authentication and authorization standard for chaos platform APIs, essential for multi-tenant SaaS platforms. | https://datatracker.ietf.org/doc/rfc6749/ |
| RFC 6750 | OAuth 2.0 Bearer Token Usage | Bearer token authentication pattern for REST API access to chaos experiments and results. | https://datatracker.ietf.org/doc/html/rfc6750 |
| OAuth 2.1 (draft) | OAuth 2.1 Authorization Framework | Modern OAuth standard addressing security improvements; recommended for new API implementations. | https://datatracker.ietf.org/doc/draft-ietf-oauth-v2-1/ |
| RFC 9700 | OAuth 2.0 Security Best Current Practice | Security guidance for OAuth 2.0 implementations, including token handling and attack prevention. | https://datatracker.ietf.org/doc/rfc9700/ |
| RFC 8252 | OAuth 2.0 for Native Apps | Authentication patterns for native application clients accessing chaos platform APIs. | https://datatracker.ietf.org/doc/html/rfc8252 |

### Data Model & API Specifications

| Standard | Description | Relevance | URL |
|----------|-------------|-----------|-----|
| OpenAPI 3.2 | RESTful API specification standard | Industry-standard for documenting chaos experiment APIs; enables automated client generation and integration testing. OpenAPI 3.1+ includes full JSON Schema 2020-12 compatibility. | https://spec.openapis.org/oas/v3.2.0.html |
| JSON Schema Draft 2020-12 | JSON data validation specification | Define and validate chaos experiment definitions, steady-state hypothesis structures, and fault configurations. Integrated with OpenAPI 3.1+. | https://json-schema.org/draft/2020-12/json-schema-validation |
| Kubernetes Custom Resource Definitions (CRDs) | Kubernetes API extension mechanism | Foundation for Kubernetes-native chaos platforms (e.g., LitmusChaos). CRDs enable declarative experiment management via kubectl and GitOps workflows. | https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/ |
| GraphQL | Query language for APIs | Alternative to REST for chaos experiment APIs; enables flexible querying of experiment results and metadata. Less common in chaos platforms but emerging. | https://graphql.org/ |

### Security & Authentication Standards

| Standard | Description | Relevance | URL |
|----------|-------------|-----------|-----|
| OWASP Web Security Testing Guide (WSTG) | Comprehensive security testing methodology | Framework for security-focused chaos engineering; highlights vulnerabilities and failure modes to test. | https://owasp.org/www-project-web-security-testing-guide/ |
| OWASP Application Security Verification Standard (ASVS) | Security control verification framework | Defines security requirements that chaos experiments can validate (e.g., failover, graceful degradation). | https://owasp.org/www-project-application-security-verification-standard/ |
| NIST Cybersecurity Framework | Organizational cybersecurity guidance | Includes "Resilience" pillar; chaos engineering is an operational practice supporting NIST's resilience testing. | https://www.nist.gov/cyberframework |

### Cloud-Native & Observability Standards

| Standard | Description | Relevance | URL |
|----------|-------------|-----------|-----|
| Principles of Chaos Engineering | Foundational methodology | Defines chaos engineering principles: hypothesis-driven experiments, minimal blast radius, production testing. Community standard published by Netflix and practitioners. | https://principlesofchaos.org/ |
| CNCF Chaos Engineering Landscape | Curated tool ecosystem | CNCF maintains an official chaos engineering working group and landscape. LitmusChaos is a CNCF-incubating project, signalling mainstream adoption in Kubernetes ecosystem. | https://www.cncf.io/blog/2019/11/06/cloud-native-chaos-engineering-enhancing-kubernetes-application-resiliency/ |
| OpenTelemetry (OTel) | Vendor-neutral observability standard | Industry standard for collecting metrics, traces, and logs; essential for real-time monitoring during chaos experiments. Supports 12+ languages and integrates with all major observability platforms. | https://opentelemetry.io/ |
| Prometheus Exposition Format / OpenMetrics | Metrics collection standard | De-facto standard for exposing metrics in cloud-native systems; chaos platforms must integrate with Prometheus-compatible endpoints for experiment monitoring. | https://prometheus.io/docs/specs/om/open_metrics_spec/ |

---

## Similar Products — Developer Documentation & APIs

### Gremlin

- **Description:** Enterprise-grade chaos engineering platform with commercial SaaS model. Provides fault injection across AWS, Azure, GCP, Kubernetes, VMs, and bare metal with granular blast-radius controls and reliability scoring.
- **API Documentation:** https://www.gremlin.com/docs
- **Developer Tutorial:** https://www.gremlin.com/community/tutorials/getting-started-with-gremlins-api
- **SDKs/Libraries:** REST API with Python, JavaScript, Go, and Java client libraries via community integrations; also integrates with Chaos Toolkit.
- **Developer Guide:** https://www.gremlin.com/community/tutorials/using-observability-to-automatically-generate-chaos-experiments
- **Standards:** REST API with JSON payloads; OpenAPI documentation available for all endpoints.
- **Authentication:** API Key authentication; JWT tokens for service-to-service communication.

### Steadybit

- **Description:** Modern chaos engineering platform featuring visual drag-and-drop experiment builder and topology discovery. Offers AWS, Kubernetes, and JVM attack libraries with open extension framework.
- **API Documentation:** https://docs.steadybit.com/
- **SDKs/Libraries:** REST API with CLI tooling; open-source extension framework for custom integrations.
- **Developer Guide:** https://docs.steadybit.com/ (comprehensive documentation)
- **Standards:** REST API with JSON; supports state checks via REST API calls during experiments. Recently introduced MCP Server for LLM-based experiment insights (June 2025).
- **Authentication:** API Key authentication.

### AWS Fault Injection Service (FIS)

- **Description:** Fully managed chaos engineering service integrated into AWS ecosystem. Provides pre-built fault scenarios for AWS-native workloads including EC2, RDS, Lambda, and managed services.
- **API Documentation:** https://docs.aws.amazon.com/fis/latest/APIReference/
- **Actions Reference:** https://docs.aws.amazon.com/fis/latest/userguide/fis-actions-reference.html
- **SDKs/Libraries:** 
  - Python (Boto3): https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/fis.html
  - Go SDK: https://docs.aws.amazon.com/sdk-for-go/api/service/fis/
  - Java, Node.js, .NET, and Ruby via AWS SDKs
- **Developer Guide:** https://docs.aws.amazon.com/fis/latest/userguide/
- **Standards:** AWS REST API conventions; integrates with CloudWatch for monitoring and CloudTrail for audit logging.
- **Authentication:** AWS IAM roles and policies; AWS credentials and STS tokens.

### Azure Chaos Studio

- **Description:** Microsoft's managed chaos engineering service for Azure resources. Supports Azure VMs, AKS, managed databases, and other Azure services with intuitive Azure Portal UI.
- **API Documentation:** https://learn.microsoft.com/en-us/rest/api/chaosstudio/
- **REST API Reference:** https://learn.microsoft.com/en-us/rest/api/chaosstudio/
- **SDKs/Libraries:** .NET, Python, Java, JavaScript SDKs available via Azure SDKs. REST API available via curl, Postman, or native HTTP clients.
- **Developer Guide:** https://learn.microsoft.com/en-us/azure/chaos-studio/chaos-studio-samples-rest-api
- **Standards:** Azure REST API conventions; OpenAPI 3.0 specification compatible. API version 2023-11-01 (with newer versions like 2025-01-01 in preview).
- **Authentication:** Azure AD (Entra ID) authentication; service principals and managed identities.

### LitmusChaos

- **Description:** CNCF-incubating open-source chaos engineering platform purpose-built for Kubernetes. Uses Kubernetes custom resource definitions (CRDs) for declarative experiment management with ChaosCenter visual UI.
- **API Documentation:** https://docs.litmuschaos.io/
- **GitHub Repository:** https://github.com/litmuschaos/chaos-operator
- **ChaosHub (Experiment Library):** https://hub.litmuschaos.io/
- **SDKs/Libraries:** Native Kubernetes operator (written in Go); YAML/JSON for CRD definitions; no language-specific SDKs (Kubernetes-native approach).
- **Developer Guide:** Getting Started: https://docs.litmuschaos.io/docs/introduction/what-is-litmus
- **Standards:** Kubernetes CRD API conventions; experiments defined as YAML. OpenAPI v3 schema validation for CRDs. Prometheus metrics export.
- **Authentication:** Kubernetes RBAC; no separate authentication required for in-cluster operations.

### Harness Chaos Engineering

- **Description:** Chaos engineering module embedded in the Harness platform. Provides 200+ pre-built faults, GitOps integration, resilience scoring, and GameDay features for team-based resilience training.
- **API Documentation:** https://apidocs.harness.io/chaos.html
- **Developer Hub:** https://developer.harness.io/docs/chaos-engineering/
- **CLI Tool (HCE CLI):** https://developer.harness.io/docs/chaos-engineering/api-reference/hce-cli/
- **SDKs/Libraries:** JavaScript/TypeScript, Python, Go, and Java SDKs via Harness SDKs. REST API with JSON payloads.
- **Developer Guide:** https://developer.harness.io/docs/chaos-engineering/quickstart/
- **Standards:** REST API following OpenAPI conventions; YAML for experiment definitions (GitOps support). Integrates with Prometheus for metrics.
- **Authentication:** API Key token or JWT token in request headers; created via Harness platform's API Keys section.

### Chaos Toolkit

- **Description:** Open-source, code-centric chaos engineering framework with declarative YAML/JSON experiment definitions. Highly extensible with pluggable drivers for multi-cloud and heterogeneous infrastructure.
- **API Documentation:** https://chaostoolkit.org/
- **GitHub Repository:** https://github.com/chaostoolkit
- **Open API Specification:** https://chaostoolkit.org/reference/api/experiment/
- **SDKs/Libraries:** Python library (chaostoolkit-lib); extensibility via Python plugins. Drivers available for Kubernetes, AWS, Azure, GCP, and other tools including Gremlin.
- **Developer Guide:** https://chaostoolkit.org/reference/usage/run/
- **Standards:** Declarative YAML/JSON experiment format; no built-in UI; CLI-based execution. Open API enables extension.
- **Authentication:** No built-in authentication; relies on underlying platform credentials (e.g., kubectl, AWS profiles, Azure CLI).

---

## Notes

### Emerging Standards and Future Directions

1. **Model Context Protocol (MCP) for Chaos**: Steadybit recently launched an MCP Server for chaos engineering (June 2025), enabling LLM-based agents to query experiment insights and plan chaos scenarios. This represents an emerging standard for AI-driven chaos automation.

2. **AI-Native Chaos Experiment Definitions**: No standardized format yet exists for AI-generated chaos hypotheses or LLM-driven experiment planning. This is an open opportunity for standardization as the field evolves.

3. **Chaos Engineering Metrics Standards**: While Prometheus/OpenMetrics provides metric exposition, there is no consensus standard for representing "resilience scores" across different chaos platforms. Gremlin and Harness each define proprietary resilience scoring models.

4. **Cross-Cloud Chaos Orchestration**: No standard exists for expressing chaos experiments uniformly across multiple cloud providers. Each platform (AWS FIS, Azure Chaos Studio, GCP) has provider-specific APIs, limiting multi-cloud orchestration.

5. **LLM Integration Standards**: As chaos engineering platforms integrate with AI agents (e.g., via MCP), standards for representing experiment results, failure analysis, and recommendations are still evolving.

### Compliance and Regulatory Considerations

- **GDPR/CCPA**: Chaos experiments in production must respect data privacy regulations. Some platforms (e.g., Gremlin) explicitly support compliance audit logging.
- **PCI DSS**: Chaos engineering is referenced in PCI DSS v4.0 as a recommended security validation technique.
- **ISO 27001**: Information security management; chaos testing supports operational resilience evidence for ISO 27001 compliance.
- **SOC 2 Type II**: Chaos engineering demonstrates operational control and resilience, supporting SOC 2 Type II attestations.

### Integration Patterns

All surveyed platforms support one or more integration patterns:
- **CI/CD Integration**: Most platforms provide API hooks for automated post-deployment chaos testing (Harness, Chaos Toolkit, AWS FIS, Azure Chaos Studio).
- **Monitoring Integration**: All platforms integrate with Prometheus, Datadog, New Relic, or CloudWatch for real-time experiment monitoring.
- **Incident Management**: Gremlin, Steadybit, and Harness integrate with PagerDuty, Jira, and incident management systems.
- **GitOps**: LitmusChaos, Harness, and Chaos Toolkit support YAML-based, version-controlled experiment definitions.

### SDK and Library Ecosystem

Modern chaos platforms provide language-specific SDKs for:
- **Python**: Boto3 (AWS), Harness SDK, Chaos Toolkit
- **JavaScript/TypeScript**: Harness SDK
- **Go**: AWS SDK, Harness SDK
- **Java**: AWS SDK, Harness SDK

Open-source platforms (LitmusChaos, Chaos Toolkit) prioritize Kubernetes-native and declarative approaches, reducing language-specific SDK requirements.

---

## Recommended Alignment with Standards

For project 300 (Chaos Engineering Platform):

1. **REST API Design**: Adopt OpenAPI 3.2+ specification with JSON Schema Draft 2020-12 for experiment definitions.
2. **Authentication**: Implement OAuth 2.0 (or OAuth 2.1) for multi-tenant SaaS or API Key + JWT for simpler architectures.
3. **Observability**: Leverage OpenTelemetry (metrics, traces, logs) and expose Prometheus-compatible `/metrics` endpoints.
4. **Kubernetes Support**: If targeting Kubernetes, design Custom Resource Definitions (CRDs) aligned with Kubernetes API conventions.
5. **Declarative Experiments**: Use JSON or YAML-based experiment definitions compatible with GitOps workflows.
6. **Security**: Follow OWASP ASVS for API security and OWASP WSTG for testing practices.
7. **Compliance**: Document support for ISO 26262, PCI DSS, GDPR, and SOC 2 compliance scenarios through chaos experiments.

---

## Sources

- [RFC 7231 — HTTP/1.1 Semantics and Content](https://datatracker.ietf.org/doc/html/rfc7231)
- [RFC 6749 — OAuth 2.0 Authorization Framework](https://datatracker.ietf.org/doc/rfc6749/)
- [RFC 6750 — OAuth 2.0 Bearer Token Usage](https://datatracker.ietf.org/doc/html/rfc6750)
- [OpenAPI Specification 3.2.0](https://spec.openapis.org/oas/v3.2.0.html)
- [JSON Schema Draft 2020-12](https://json-schema.org/draft/2020-12/json-schema-validation)
- [Kubernetes Custom Resource Definitions](https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [OWASP Application Security Verification Standard](https://owasp.org/www-project-application-security-verification-standard/)
- [Principles of Chaos Engineering](https://principlesofchaos.org/)
- [OpenTelemetry — Observability Framework](https://opentelemetry.io/)
- [OpenMetrics Specification](https://prometheus.io/docs/specs/om/open_metrics_spec/)
- [Gremlin Documentation](https://www.gremlin.com/docs)
- [Steadybit Documentation](https://docs.steadybit.com/)
- [AWS FIS API Reference](https://docs.aws.amazon.com/fis/latest/APIReference/)
- [Azure Chaos Studio REST API](https://learn.microsoft.com/en-us/rest/api/chaosstudio/)
- [LitmusChaos Documentation](https://docs.litmuschaos.io/)
- [Harness Chaos Engineering Documentation](https://developer.harness.io/docs/chaos-engineering/)
- [Chaos Toolkit — Chaos Engineering Framework](https://chaostoolkit.org/)
