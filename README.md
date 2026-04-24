# Chaos Mesh (chaos-mesh)

Chaos Mesh is a CNCF graduated cloud-native chaos engineering platform that orchestrates chaos experiments on Kubernetes to test system resilience and reliability. It exposes Kubernetes Custom Resource Definitions (CRDs) for a wide range of chaos kinds (network, pod, IO, stress, DNS, time, kernel, JVM, HTTP), along with a Chaos Dashboard web UI backed by a REST API for creating, managing, and monitoring chaos experiments and workflows. Chaos Mesh integrates with Kubernetes, Argo Workflows, Prometheus, Grafana, and CI/CD pipelines to run experiments safely in staging and production environments.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/chaos-mesh/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** Open Source
- **x-type:** opensource

## Tags

- Chaos Engineering, Cloud Native, CNCF, Fault Injection, Kubernetes, Observability, Open Source, Reliability, Resilience, Testing

## Timestamps

- **Created:** 2025-01-01
- **Modified:** 2026-04-23

## APIs

### Chaos Mesh API

Chaos Mesh provides Kubernetes Custom Resources and a REST API for orchestrating chaos experiments including network faults, pod failures, IO chaos, stress testing, kernel chaos, DNS chaos, time chaos, JVM chaos, and HTTP request injection. The Chaos Dashboard exposes a REST API for creating, running, scheduling, and observing experiments and multi-step workflows, with RBAC and event auditing.

**Human URL:** [https://chaos-mesh.org/docs/](https://chaos-mesh.org/docs/)

#### Tags

- Chaos Engineering, CRDs, Dashboard, Experiments, Fault Injection, Kubernetes, Workflows

#### Properties

- [Documentation](https://chaos-mesh.org/docs/)
- [Getting Started](https://chaos-mesh.org/docs/quick-start/)
- [GitHub Repository](https://github.com/chaos-mesh/chaos-mesh)
- [OpenAPI](openapi/chaos-mesh-dashboard-api-openapi.yml)
- [JSON Schema](json-schema/chaos-mesh-experiment-schema.json)
- [JSON-LD Context](json-ld/chaos-mesh-context.jsonld)

## Common Properties

- [Website](https://chaos-mesh.org/)
- [Documentation](https://chaos-mesh.org/docs/)
- [Getting Started](https://chaos-mesh.org/docs/quick-start/)
- [Blog](https://chaos-mesh.org/blog/)
- [Change Log](https://github.com/chaos-mesh/chaos-mesh/blob/master/CHANGELOG.md)
- [GitHub Organization](https://github.com/chaos-mesh)
- [GitHub Repository](https://github.com/chaos-mesh/chaos-mesh)
- [Community](https://chaos-mesh.org/community/)
- [License](https://github.com/chaos-mesh/chaos-mesh/blob/master/LICENSE)
- [CNCF Project Page](https://www.cncf.io/projects/chaos-mesh/)
- [Slack (CNCF)](https://slack.cncf.io/)
- [X](https://x.com/chaos_mesh)
- [JSON-LD](json-ld/chaos-mesh-context.jsonld)
- [JSON Schema](json-schema/chaos-mesh-experiment-schema.json)

## Features

Pod Chaos, Network Chaos, IO Chaos, Stress Chaos, Kernel Chaos, Time Chaos, DNS Chaos, JVM Chaos, HTTP Chaos, AWS Chaos, GCP Chaos, Azure Chaos, Block Chaos, Physical Machine Chaos, Workflows, Schedules, Chaos Dashboard, Kubernetes CRDs, REST API, RBAC, Audit Events, Safe Mode, Status Monitoring

## Use Cases

Resilience Testing, Disaster Recovery Drills, SRE Game Days, Canary Validation, Production Reliability Testing, Multi-Region Failover Testing, Performance Bottleneck Discovery, Observability Validation, Continuous Chaos in CI/CD, Microservices Dependency Testing, Database Fault Tolerance Testing

## Integrations

Kubernetes, EKS, GKE, AKS, OpenShift, Rancher, Argo Workflows, Argo CD, Prometheus, Grafana, OpenTelemetry, Jaeger, Datadog, Litmus, GitHub Actions, GitLab CI, Jenkins, Tekton, Helm, AWS, Google Cloud, Azure

## Chaos Kinds

PodChaos, NetworkChaos, IOChaos, TimeChaos, KernelChaos, StressChaos, DNSChaos, HTTPChaos, JVMChaos, AWSChaos, GCPChaos, AzureChaos, BlockChaos, PhysicalMachineChaos, Schedule, Workflow

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
