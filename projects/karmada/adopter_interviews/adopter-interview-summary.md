# Karmada Adopter Interview Summary

## Interviewees

| Name | Company | Team/Domain | Interview Date |
|------|---------|-------------|----------------|
| Yuzhui Liu | Bloomberg | GPU batch workloads / HPC scheduling | 05/29/2026 |
| Michael Szacillo | Bloomberg | Streaming platform (Apache Flink) | 06/09/2026 |
| Da Huo | Bloomberg | Streaming platform (Apache Flink) | 06/09/2026 |
| Joe Nathan Abellard | Bloomberg | Cloud Compute Services — managed Karmada platform | 06/17/2026 |
| Zhuyu Li | Bloomberg | Cloud Compute Services — managed Karmada platform | 06/17/2026 |
| Zongqing Li | Trip.com | Multi-cluster orchestration | 05/29/2026 |
| HF Yue | Trip.com | Multi-cluster orchestration | 05/29/2026 |

TOC Interviewers: Ahmed Bebars, Chad Beaudin

---

## Adoption Timeline & Scale

**Bloomberg (GPU/HPC team):** Evaluated late 2023, production mid-2024. Running an internal fork to fast-track priority/preemption scheduling features pending upstream merge. Upgrades quarterly; urgent patches as needed.

**Bloomberg (Streaming team):** Research mid-2024, POC Q3 2024. Currently on v1.17 (March release). Aligned with Karmada's quarterly release schedule. Migrated dev instances onto the managed Karmada platform run by Joe's team.

**Bloomberg (Managed Platform team):** First Bloomberg team adopted Karmada ~2.5 years ago "the hard way." The managed multi-cluster platform was built to avoid each team repeating that effort. First tenant reached production maturity on the managed platform in March 2026. Follows Karmada's 3-version support policy; validates each new release before offering it to tenants. Multiple tenants now running production workflows.

**Trip.com:** 4 years in use, 3 years in production. Internal fork based on v1.5.1 with ~10 internal releases per year. Scale: 40 total clusters, largest Karmada instance managing 25 clusters, 10K applications, 1M cores, 400K objects.

---

## Use Cases

### Bloomberg — GPU Batch Scheduling
- Multi-cluster scheduler for GPU-intensive model training across HPC clusters
- Shifted quota model from GPU-count to GPU-time, revealing over-provisioning
- Cluster federation enabling seamless maintenance without user impact
- Priority and preemption scheduling (contributed upstream)

### Bloomberg — Streaming Platform
- Cross-cluster disaster recovery for stateful Apache Flink workloads
- Failover between regions without restarting stream processing
- Federated resource quota for capacity planning across clusters
- Multiple pod-template support (co-developed with Karmada)
- Workload anti-affinity

### Bloomberg — Managed Multi-Cluster Platform
- Fully managed Karmada-as-a-service for internal platform teams (AI, streaming, general compute)
- Tenant onboarding journey from intake through POC to production maturity
- Control planes stretched across host clusters spanning multiple data centers for HA/DR
- DNS-based service discovery providing unified ingress endpoint to stretched control planes
- Custom operators integrating with internal cluster inventory API and token exchange for automated member cluster registration
- Production-grade observability and alerting provided out of the box to all tenants
- Reduces multi-cluster infrastructure setup from weeks to minutes

### Trip.com — Multi-Cluster Orchestration
- Multi-cluster HPA extending across 40 clusters
- Seamless cluster migration/retirement without application changes
- Distributed multi-cluster HPA built on Karmada's object contract layer
- Migrated 300K stateless workloads across clusters

---

## Why Karmada Over Alternatives

| Alternative | Why It Was Rejected |
|-------------|-------------------|
| Armada | Pod-level scheduling only; no CRD support; dwindling project activity |
| Kueue / MultiKueue | Not production-ready in 2023 |
| KubeFed | APIs differ from single-cluster model; no longer active |
| ClusterNet | APIs differ from single-cluster model; not active |
| KubeFleet | Evaluated by Bloomberg platform team; Karmada's community and CNCF governance were stronger differentiators |
| Kubistella | Evaluated by Bloomberg platform team; lacked Karmada's community responsiveness |

**Key differentiators:** Karmada's Kubernetes-native API compatibility (no application changes required), CRD support, CNCF governance, and — most importantly per the platform team — a collaborative community willing to work with adopters to address gaps.

---

## Highlights

- **Kubernetes-native API model** — single-cluster APIs work unchanged, zero application-side modifications needed (all interviews emphasized this)
- **CRD support via Resource Interpreter Framework** — critical for Bloomberg; lets Karmada understand custom internal workload types
- **Collaborative community** — the most important differentiator per the platform team; responsive to issues, willing to co-develop features, positive outcomes in all engagements
- **Production-validated at scale** — large Chinese companies plus Bloomberg running it in production provides confidence in stability
- **Full-time maintainers** — bug fixes are very fast; GitHub issues get very quick replies
- **Comprehensive feature set** — cluster failover, federated quota, policy-driven placement, health monitoring, stateful failover, anti-affinity, multiple pod templates
- **High extensibility** — Trip.com built distributed HPA on top; Bloomberg built a full managed platform
- **In-person community engagement** — architecture sessions at KubeCon, annual maintainer meetings, bi-weekly community calls
- **Measurable cost savings** — Bloomberg avoided unnecessary GPU hardware purchases; multi-cluster setup reduced from weeks to minutes
- **Operational efficiency** — eliminated manual tenant onboarding, cluster maintenance no longer requires tenant coordination
- **Documentation quality** — architecture docs, concept pages, propagation policy docs, failover docs, and linked examples all called out as valuable; provides good foundation for learning and deep dives
- **CNCF governance** — gives adopters confidence in project longevity and neutrality
- **Production-grade observability** — managed platform provides alerting and monitoring out of the box

---

## Lowlights

- **Limited North America/international presence** — all Bloomberg interviews raised this; timezone friction for PR reviews, community meetings, and KubeCon NA representation
- **Slow review process for large contributions** — Bloomberg's priority/preemption feature took a very long time from proposal to merge
- **Performance at scale** — Trip.com hit performance issues as cluster count and object count grew; removed the Work object entirely from their internal fork
- **Multi-cluster scheduling complexity** — distributing instances across clusters while accounting for capacity needs improvement
- **Internal fork necessity** — Bloomberg (GPU team) and Trip.com maintain internal forks due to upstream feature/performance gaps; Trip.com's fork is 13+ versions behind
- **Anti-affinity needs improvement** — Bloomberg's streaming team wants enhancements
- **Day-two operational maturity gaps** — observability, alerting, and release testing processes need more maturity for platform teams running Karmada as a managed service
- **No conformance test suite** — platform teams need an automated way to validate new versions before rolling them out to tenants (like Kubernetes has)
- **No automated scalability testing** — teams running at very large scale can't easily verify new releases meet their performance requirements

---

## Community Engagement

All adopters actively engage with the Karmada community:
- Bloomberg team members are project maintainers
- Trip.com has a maintainer (Zach) on the project
- Communication channels: GitHub issues (primary, very responsive), bi-weekly community meetings, KubeCon meetings (primarily EU), US adopter community meetings, ad-hoc calls, Slack
- Bloomberg's streaming team attended KubeCon EU specifically to evaluate multi-cluster options; Kevin's K8s scheduler background gave Karmada architectural credibility
- Bloomberg's platform team works with community on behalf of their tenants to address feature gaps
- Community contributed back: priority/preemption scheduling, Karmada operator enhancements (TLS cert support for stretched control planes), documentation for availability and scalability

---

## Removal Difficulty

All adopters said removing Karmada would be very difficult:
- **Bloomberg:** Would maintain internal fork if archived; already have maintainers on the project
- **Trip.com:** Would take more than 1–2 years to remove

---

## Future Plans

- **Bloomberg (GPU):** Contribute priority/preemption upstream, then drop internal fork
- **Bloomberg (Streaming):** Contribute scalability improvements, conformance testing, publish end-user story
- **Bloomberg (Platform):** Continue deepening community relationship; address gaps as new tenant use cases emerge; considering submitting a CNCF reference architecture for managed multi-cluster platforms
- **Trip.com:** Expand internal Karmada usage; no new feature needs currently

---

## CNCF Maturity Level Perception

Adopters who discussed maturity levels understand them and use them in decision-making:
- Graduated projects are preferred first choice
- Incubating projects considered if on a clear graduation path
- Pragmatic approach: will adopt lower-maturity projects if critically needed and help them mature
- Sandbox vs. Incubating distinction can be unclear at first glance
- Higher maturity indicates the features you need are more likely present
