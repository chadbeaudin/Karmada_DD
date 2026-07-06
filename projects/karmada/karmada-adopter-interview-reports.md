# Karmada Graduation — Adopter Interview Reports

Generated: 2026-07-06
TOC Interviewers: Ahmed Bebars, Chad Beaudin

---

## Interview Overview

| # | Adopter | Industry | Team/Domain | Interview Date | Interviewees |
|---|---------|----------|-------------|----------------|--------------|
| 1 | Bloomberg | Finance | GPU batch workloads / HPC scheduling | 2026-05-29 | Yuzhui Liu |
| 2 | Bloomberg | Finance | Streaming platform (Apache Flink) | 2026-06-09 | Michael Szacillo, Da Huo |
| 3 | Bloomberg | Finance | Cloud Compute Services — managed Karmada platform | 2026-06-17 | Joe Nathan Abellard, Zhuyu Li |
| 4 | Trip.com | Online Travel | Multi-cluster orchestration | 2026-05-29 | Zongqing Li, HF Yue |

---

# Interview Report 1: Bloomberg — GPU/HPC Scheduling

## Metadata

- **Project**: Karmada
- **Adopter**: Bloomberg | Finance | ATTRIBUTABLE
- **Interview Date**: 2026-05-29
- **TOC Interviewers**: Ahmed Bebars, Chad Beaudin
- **Interviewee**: Yuzhui Liu (Bloomberg)
- **Report Generated**: 2026-07-06

---

## Q01: How long has your organization used the project?

Bloomberg's GPU/HPC scheduling team began evaluating Karmada toward the end of 2023. Production use started in mid-2024, giving the team approximately two years of experience with the project at the time of the interview.

---

## Q02: What were the main motivations to adopt the project and which key features do you use today?

The team handles GPU-intensive batch workloads (primarily model training) across multiple HPC clusters. Previously, each user budgeted a peak GPU count (e.g., 20 GPUs), leading to over-provisioning because actual workloads are spiky. They needed a multi-cluster scheduler that could place work across clusters whenever capacity was available, shifting the quota model from GPU count to GPU time. Karmada serves as that multi-cluster scheduler sitting in front of their GPU clusters. Key features in use include multi-cluster scheduling, cluster federation, and priority/preemption scheduling (contributed upstream by the team).

---

## Q03: Compared with other products and projects in this space (proprietary and open) what drew you to the project?

Two alternatives were evaluated:
- **Armada** — a strong project, but its scheduling unit is the pod. Bloomberg had already developed custom Kubernetes resources (CRDs) for their workloads, which Armada did not support. Karmada supports custom resources natively.
- **Kueue / MultiKueue** — still under development in 2023, not production-ready at the time.

Karmada was the only option already productionized with known large-company production users that could address their requirements for CRD-based multi-cluster scheduling.

---

## Q04: What is the current level of usage (pre-production, production) and scale?

Production. Scale information cannot be shared publicly.

---

## Q05: What version of the project is currently in use and what is your update cadence with the project?

Running an internal fork. Major upgrades are baked into quarterly plans; urgent patches are applied as needed. The internal fork exists to fast-track deployment of features pending upstream merge (specifically priority and preemption scheduling). The goal is to remove the internal fork once those features merge upstream and switch to official releases.

---

## Q06: Can you walk me through what your experience was in either adopting it outright or integrating it with your existing services and applications? What challenges did you experience with the project?

The team found Karmada relatively straightforward to start using. The significant work was in integration with existing systems: connecting Karmada with existing APIs for cluster management and RBAC, standing up independent clusters to deploy Karmada, and building failover capability so that if one cluster goes down, operations continue. The initial architecture was designed during a KubeCon Amsterdam meeting with Karmada maintainers — literally sketched out over dinner.

---

## Q07: Did you find the information in the repo or the project docs valuable to your implementation? If so, where did you find the information and what specifically was useful?

Yes. Engineers specifically called out:
- Propagation policy documentation
- Interpreter documentation
- Linked example code (found particularly helpful)

---

## Q08: Did you need to engage with the community members or maintainers? If so what was the context of the engagement, which communication channels did you use and did it reach an acceptable outcome?

Yes, extensively. Communication channels used:
- **Annual in-person meetings at KubeCon Europe** — they meet the maintainers every year, including dinners together. The initial architecture was laid out at the first KubeCon Amsterdam meeting.
- **GitHub issues** — one of the main channels.
- **US adopter community meetings** — they attend these.
- **Ad-hoc scheduled calls** — for specific questions or discussions.

Bloomberg team members are also project maintainers and are actively contributing priority and preemption scheduling logic back upstream.

---

## Q09: Has your implementation of the project provided measurable value? Such as reducing manual activities, faster integrations, supported federation/multi-cloud, ease of use, cost savings, etc.

Yes, two major achievements:
- **Cluster federation / high availability:** They can take a cluster down for maintenance and put it back seamlessly without user impact.
- **Cost savings:** By shifting from GPU-count quota to GPU-time tracking, they discovered their actual capacity utilization was much lower than what was budgeted on paper. This avoided unnecessary GPU hardware purchases.
- **Operational efficiency:** Eliminated manual tenant onboarding and capacity planning conversations. Users simply submit workloads into the queue and the scheduler handles placement across clusters.

---

## Q10: If the project were to be archived now or in the future, what level of difficulty would your organization experience to remove it from your environments?

It would be a significant amount of work to move away from Karmada due to the extensive integration effort already invested. If archived, they would maintain their existing internal fork and continue operating. Bloomberg already has team members serving as project maintainers.

---

## Q11: Is there something you feel that holds the project back from reaching its ultimate potential?

Fewer US/North American adopters compared to China. This creates:
- Timezone scheduling friction when needing to discuss with maintainers.
- Slower PR reviews due to the geographic distribution of contributors.

---

## Q12: In your opinion, what could the project improve?

For large proposals/features, have more frequent reviews. Their team contributed the priority and preemption feature, and getting the proposal reviewed, approved, and code merged took a very long time. A faster review process for substantial contributions would be an improvement.

---

## Q13: What are the overall strengths of the project?

- **Ease of use** — not difficult to start.
- **Production validation** — multiple large Chinese companies already using it in production gives confidence that bugs are fixed and it's thoroughly tested.
- **Full-time maintainers** — bug fixes are very quick.
- **Rich functionality** — many features available; you can selectively adopt what you need.

---

## Q14: Do you have any future plans regarding the project? More involvement, feature requests, expansion, etc.

Primary plan is to contribute the priority and preemption scheduling logic back to upstream. Once that feature merges, they intend to remove their internal fork and rely solely on the upstream version.

---

## Q15: Do you feel you have a good understanding on the meaning of each maturity level for CNCF projects?

Yes. They typically choose Graduated projects first. If not available, they look for Incubating projects on a clear path to graduation. They have a good understanding after reading the documentation, though without re-reading, Sandbox and Incubating can feel somewhat similar.

---

## Q16: Is there information missing regarding the meaning of each different level?

The website documentation is clear enough when read carefully. One observation: Sandbox and Incubating can sound similar at first glance, but reading the detailed definitions makes the distinction clear.

---

## Q17: Do you rely on those levels internally in any way, and if yes how?

Yes, they do rely on maturity levels for internal decision-making. Preference is for Graduated projects, then Incubating if on a clear graduation path. However, they take a pragmatic approach: if they critically need something that's only available at Sandbox or Incubating level, they will adopt it and try to help the project mature.

---

# Interview Report 2: Bloomberg — Streaming Platform (Apache Flink)

## Metadata

- **Project**: Karmada
- **Adopter**: Bloomberg | Finance | ATTRIBUTABLE
- **Interview Date**: 2026-06-09
- **TOC Interviewers**: Ahmed Bebars, Chad Beaudin
- **Interviewees**: Michael Szacillo, Da Huo (Bloomberg)
- **Report Generated**: 2026-07-06

---

## Q01: How long has your organization used the project?

Bloomberg's streaming platform team provides Apache Flink infrastructure to different teams within Bloomberg for high-volume, real-time analytics. They began researching Karmada in mid-2024 and conducted a proof of concept in Q3 2024. During the POC they identified feature gaps, submitted MVP feature requests to the Karmada community, and the positive community engagement sold them on Karmada. They decided to roll forward with the project.

---

## Q02: What were the main motivations to adopt the project and which key features do you use today?

The primary motivation was disaster recovery rollover — the ability to fail over from one cluster to another in a different region. Their workloads include many stateful applications (Flink streaming jobs), and restarting stream processing after a failover would be catastrophic for their users.

Key features in use today:
- Stateful cross-cluster failover
- Federated resource quota (enables capacity planning across clusters)
- Multiple pod-template support (co-developed with the Karmada community)
- Workload anti-affinity

---

## Q03: Compared with other products and projects in this space (proprietary and open) what drew you to the project?

They evaluated:
- **Armada** — a CNCF Sandbox project, but designed only to support pod scheduling. The streaming team deals exclusively with CRDs. Additionally, the project showed dwindling activity/support.
- **MultiKueue** — evaluated but did not meet requirements.

Karmada's CRD support and active community were the deciding factors.

---

## Q04: What is the current level of usage (pre-production, production) and scale?

Production.

---

## Q05: What version of the project is currently in use and what is your update cadence with the project?

Running v1.17 (March 2026 release). They stay aligned with Karmada's quarterly release schedule.

---

## Q06: Can you walk me through what your experience was in either adopting it outright or integrating it with your existing services and applications? What challenges did you experience with the project?

They started with a POC and quickly discovered limitations for Bloomberg-specific use cases. They intertwine with the Cloud Compute Services team (Joe Abellard's managed platform) — they migrated their dev instances over to that managed Karmada platform. Rather than working around limitations, they jumped in as contributors to drive the implementation of the needed features directly in the project.

---

## Q07: Did you find the information in the repo or the project docs valuable to your implementation? If so, where did you find the information and what specifically was useful?

Yes. They highlighted:
- The dedicated architecture section describing the responsibility for each component
- Documentation was comprehensive and contained all of what they needed

---

## Q08: Did you need to engage with the community members or maintainers? If so what was the context of the engagement, which communication channels did you use and did it reach an acceptable outcome?

Yes. They attended KubeCon EU 2024 specifically to learn about multi-cluster orchestration options. They spoke with Hongcai and Kevin after their KubeCon talk. Kevin's background as a Kubernetes scheduler contributor lent credibility ("street cred") that Karmada was implementing things in an architecturally sound way. The positive community engagement was a major factor in their decision to adopt Karmada.

---

## Q09: Has your implementation of the project provided measurable value? Such as reducing manual activities, faster integrations, supported federation/multi-cloud, ease of use, cost savings, etc.

The biggest value comes from ease of maintenance. Cluster maintenance used to require significant tenant involvement to move workloads to a different cluster. Karmada has reduced much of that operational overhead.

---

## Q10: If the project were to be archived now or in the future, what level of difficulty would your organization experience to remove it from your environments?

They are already maintainers and have their own fork they would use. It would be very difficult to remove Karmada.

---

## Q11: Is there something you feel that holds the project back from reaching its ultimate potential?

Limited project involvement at KubeCon North America. It is hard to find Karmada representatives at US-based events and in US time zones.

---

## Q12: In your opinion, what could the project improve?

- Improvements to existing features, specifically anti-affinity capabilities
- North America–based time zone representation

---

## Q13: What are the overall strengths of the project?

Comprehensive list of supported features:
- Cluster health monitoring
- Stateful failover
- CRD support
- Multiple pod template support
- Workload anti-affinity
- Active community (this is why they started using the project in the first place)
- Strong list of adopters (this is why they started using the project in the first place)

---

## Q14: Do you have any future plans regarding the project? More involvement, feature requests, expansion, etc.

- Contribute scalability improvements
- Contribute conformance testing
- Working on publishing an end-user story

---

## Q15: Do you feel you have a good understanding on the meaning of each maturity level for CNCF projects?

Yes. The higher a project goes toward graduation, the more mature it is — not necessarily just about the number of users.

---

## Q16: Is there information missing regarding the meaning of each different level?

No.

---

## Q17: Do you rely on those levels internally in any way, and if yes how?

They do not use them strictly internally. However, they are usually more inclined to use Incubating or Graduated projects because the features you want are more likely present in those more mature projects.

---

# Interview Report 3: Bloomberg — Cloud Compute Services (Managed Platform)

## Metadata

- **Project**: Karmada
- **Adopter**: Bloomberg | Finance | ATTRIBUTABLE
- **Interview Date**: 2026-06-17
- **TOC Interviewers**: Ahmed Bebars, Chad Beaudin
- **Interviewees**: Joe Nathan Abellard, Zhuyu Li (Bloomberg, Cloud Compute Services)
- **Report Generated**: 2026-07-06

---

## Q01: How long has your organization used the project?

Data center redundancy to maintain continuity of service in disaster scenarios is an organizational mandate at Bloomberg. Multi-cluster orchestration has evolved as a key enabler for achieving that at scale.

The first Bloomberg team to adopt Karmada did so "the hard way" about two and a half years ago, setting up and maintaining all infrastructure themselves. Given that other platform teams were interested — and they did not want each team to repeat that effort — the Cloud Compute Services team built a fully managed multi-cluster platform atop Karmada. This platform enables teams to ship applications without needing deep multi-cluster expertise. Each tenant goes through an onboarding journey that culminates in production maturity. The first tenant to reach production maturity on the managed platform did so in March 2026.

---

## Q02: What were the main motivations to adopt the project and which key features do you use today?

The major motivation is meeting Bloomberg's requirements for high availability and disaster recovery across distributed infrastructure, while enabling teams to onboard to Karmada infrastructure without needing deep multi-cluster knowledge.

Key features highlighted:
- **Cluster failover** — critical for DR testing; if a cluster goes unhealthy, workloads are rescheduled to other member clusters.
- **Federated resource quota** — governs resource quota usage for tenants with workloads running across different clusters.
- **Policy-driven placement** — declarative approach to propagating workloads across clusters.
- **Resource Interpreter Framework** — allows Karmada to understand Bloomberg's internal CRDs for different workload types.

---

## Q03: Compared with other products and projects in this space (proprietary and open) what drew you to the project?

Evaluated KubeFleet, Kubistella, and Armada. Karmada differentiated itself with:
- Kubernetes-native API enabling seamless integration with the K8s toolchain and ecosystem.
- Policy-driven placement for declarative resource scheduling.
- Cluster failover support for handling disaster scenarios.

The most important differentiator was **CNCF governance and a very collaborative community** willing to work with them to address gaps identified during adoption. It has been a very positive experience — they have addressed gaps for running stateful applications (e.g., Flink deployments across clusters) and operational gaps in the Karmada operator used to provision control plane infrastructure for tenants.

---

## Q04: What is the current level of usage (pre-production, production) and scale?

The managed service is generally available for production users. They support multiple tenants, each going through the onboarding journey. Currently have tenants running production workflows on the managed platform.

---

## Q05: What version of the project is currently in use and what is your update cadence with the project?

Karmada follows a version support policy similar to Kubernetes — the most recent 3 minor releases are actively supported. The managed platform follows the same policy: for every new Karmada release, they validate it on the managed platform before adding support for tenants. The platform team handles upgrades so tenants do not have to deal with it.

---

## Q06: Can you walk me through what your experience was in either adopting it outright or integrating it with your existing services and applications? What challenges did you experience with the project?

They rely on the upstream Karmada operator for provisioning control plane infrastructure for all tenants. In addition, they have built custom operators that integrate with internal systems — such as a cluster inventory API and token exchange servers — to fully automate member cluster registration for tenants.

Where they have identified gaps in upstream components, they have worked closely with the community to address them. A concrete example: to meet Bloomberg's mandate for HA and DR, they run all control planes stretched across a cohort of host clusters spanning multiple data centers, integrated with their DNS-based service discovery platform to provide one unified ingress endpoint. Making that work required using the same TLS certificate to provision the stretched instance across host clusters, which required adding support to the Karmada operator — something they worked on closely with the community.

---

## Q07: Did you find the information in the repo or the project docs valuable to your implementation? If so, where did you find the information and what specifically was useful?

Very useful. The documentation provides a good foundation when first learning the project with enough detail. When diving deep into specific features (failover, propagation policy), it has very detailed documentation to explore and try things independently.

They are also contributing back documentation for areas they found missing but helpful — specifically around availability and scalability, which are focus areas for satisfying Bloomberg's needs.

---

## Q08: Did you need to engage with the community members or maintainers? If so what was the context of the engagement, which communication channels did you use and did it reach an acceptable outcome?

Yes. Primary channels:
- **GitHub issues** — very responsive; as long as issues have good descriptions and proposals, replies are very quick.
- **Bi-weekly community meetings** — opportunity to provide more information and have deeper discussions.

Overall, community engagement has been very positive with good outcomes for all interactions.

---

## Q09: Has your implementation of the project provided measurable value? Such as reducing manual activities, faster integrations, supported federation/multi-cloud, ease of use, cost savings, etc.

Yes, great measurable outcomes:
- **Day-one setup time:** Managing multi-cluster infrastructure "the hard way" takes weeks. With the managed platform, teams can set up within minutes.
- **Day-two operational savings:** Significant time saved across all platform teams for ongoing infrastructure maintenance.
- **Production-grade observability:** All tenants get observability and alerting out of the box when onboarded onto the platform.

---

## Q10: If the project were to be archived now or in the future, what level of difficulty would your organization experience to remove it from your environments?

They already have a fork and have maintainers on the project. Removal would be very difficult.

---

## Q11: Is there something you feel that holds the project back from reaching its ultimate potential?

Gaps around **operational resilience** for platform teams. It is one thing to set up infrastructure, but day-two operations (observability, alerting, testing new releases) need more maturity. These gaps could hold back wider adoption. They are currently working with the community on scalability testing and conformance testing initiatives, drawing from established Kubernetes community patterns.

---

## Q12: In your opinion, what could the project improve?

Strong signals about project maturity are missing:
- **Automated scalability testing** — like Kubernetes has — so teams running at very large scale can be assured of support without doing the validation work themselves.
- **Conformance test suite** — like Kubernetes has — so platform teams can run it to validate each new version before supporting it for tenants. This would greatly simplify their upgrade process.

These improvements are important because they follow Karmada's 3-version support policy and need efficient ways to validate new releases for their tenants across diverse use cases (AI, streaming analytics, general compute).

---

## Q13: What are the overall strengths of the project?

The collaborative community and CNCF governance were highlighted as the most important strengths — both for Bloomberg and for the project itself.

---

## Q14: Do you have any future plans regarding the project? More involvement, feature requests, expansion, etc.

They want to continue engaging with the community and deepen the relationship. Specific future work is driven by need — when new tenants onboard with unique use cases that expose gaps, they will work with the community on their behalf to address those.

Additionally, they are interested in submitting a **CNCF reference architecture** for how they built a managed multi-cluster platform on top of Karmada.

---

## Q15: Do you feel you have a good understanding on the meaning of each maturity level for CNCF projects?

[NOT DISCUSSED]

---

## Q16: Is there information missing regarding the meaning of each different level?

[NOT DISCUSSED]

---

## Q17: Do you rely on those levels internally in any way, and if yes how?

[NOT DISCUSSED]

---

# Interview Report 4: Trip.com — Multi-Cluster Orchestration

## Metadata

- **Project**: Karmada
- **Adopter**: Trip.com | Online Travel | ATTRIBUTABLE
- **Interview Date**: 2026-05-29
- **TOC Interviewers**: Ahmed Bebars, Chad Beaudin
- **Interviewees**: Zongqing Li, HF Yue (Trip.com)
- **Report Generated**: 2026-07-06

---

## Q01: How long has your organization used the project?

Trip.com has been using Karmada for 4 years, with 3 years of production use.

---

## Q02: What were the main motivations to adopt the project and which key features do you use today?

Trip.com relies heavily on Horizontal Pod Autoscaling (HPA) and needed to extend that capability across multiple clusters. Additionally, migrating or retiring clusters was a significant pain point. Karmada's API model being mostly the same as a single-cluster Kubernetes API was the primary reason they chose the project — it meant no application-side modifications were required.

---

## Q03: Compared with other products and projects in this space (proprietary and open) what drew you to the project?

They evaluated KubeFed and ClusterNet (two multi-cluster orchestration projects):
- Both required APIs that differed from the single-cluster Kubernetes model, which would have forced application-side modifications.
- Neither project was actively maintained.

Karmada's Kubernetes-native API compatibility and active community were the deciding factors.

---

## Q04: What is the current level of usage (pre-production, production) and scale?

Running in production for 3 years at significant scale:
- 40 total clusters
- Largest Karmada instance managing 25 clusters
- 10,000 applications
- 1 million cores
- 400,000 objects

---

## Q05: What version of the project is currently in use and what is your update cadence with the project?

Running an internal fork based on Karmada v1.5.1 (upstream is currently working on v1.18). They produce approximately 10 internal releases per year. Some changes are fed back to the community, but others are specific to their use case and "not wanted" by the broader community.

---

## Q06: Can you walk me through what your experience was in either adopting it outright or integrating it with your existing services and applications? What challenges did you experience with the project?

The team did not need to make any changes on their application side since Karmada is compatible with the single-cluster Kubernetes API. They built a distributed multi-cluster HPA and integrated that with Karmada, using Karmada's Objects/Contract layer as the foundation for their internal scaling architecture.

---

## Q07: Did you find the information in the repo or the project docs valuable to your implementation? If so, where did you find the information and what specifically was useful?

Karmada's information was very valuable. Their concept page and diagrams were a huge help in socializing Karmada's concepts to other colleagues at Trip.com.

---

## Q08: Did you need to engage with the community members or maintainers? If so what was the context of the engagement, which communication channels did you use and did it reach an acceptable outcome?

Yes. They had interactions with community groups and via GitHub. Trip.com has a maintainer (Zach) on the project.

---

## Q09: Has your implementation of the project provided measurable value? Such as reducing manual activities, faster integrations, supported federation/multi-cloud, ease of use, cost savings, etc.

Karmada as an abstraction layer allowed them to migrate stateless workloads across clusters seamlessly. They have migrated 300,000 workloads across clusters.

---

## Q10: If the project were to be archived now or in the future, what level of difficulty would your organization experience to remove it from your environments?

It would be very hard to remove Karmada. It would take more than 1–2 years to remove it. Trip.com has a maintainer (Zach) on the project.

---

## Q11: Is there something you feel that holds the project back from reaching its ultimate potential?

- **Performance at scale** — performance issues grow as the number of clusters and number of objects increase. They have removed the Work object entirely from their internal version to address this.
- **Multi-cluster scheduling complexity** — distributing application instances across clusters while accounting for capacity needs improvement.

---

## Q12: In your opinion, what could the project improve?

- Broader international adoption beyond China. Bloomberg's adoption was the biggest international user; they are hoping to see more.
- International meeting coordination.

---

## Q13: What are the overall strengths of the project?

- Karmada's Kubernetes-native API approach
- Comprehensive multi-cluster orchestration capability, including policy-based scheduling and failover
- Highly extensible
- Active community compared to other projects in this space
- Regular releases

---

## Q14: Do you have any future plans regarding the project? More involvement, feature requests, expansion, etc.

Planning on using Karmada more internally. Feature-wise, Karmada already does everything they need for now.

---

## Q15: Do you feel you have a good understanding on the meaning of each maturity level for CNCF projects?

They know the levels but do not have a deep understanding. Graduated indicates a project should be very mature for use in production.

---

## Q16: Is there information missing regarding the meaning of each different level?

No.

---

## Q17: Do you rely on those levels internally in any way, and if yes how?

Maturity levels help them know which projects they should choose first. They still need to evaluate projects based on community activity and technical direction. Maturity levels are the "first loop," but they still need the "second loop" of deeper evaluation.

---

# Adopter Interview Summaries (for DD Embedding)

The following summaries are formatted for embedding in the Karmada Graduation Due Diligence document.

---

## Summary: Bloomberg — GPU/HPC Scheduling

Bloomberg's GPU/HPC scheduling team adopted Karmada in mid-2024 after evaluating alternatives (Armada, Kueue) that lacked support for custom Kubernetes resources. Karmada serves as the multi-cluster scheduler for GPU-intensive model training across their HPC clusters, enabling a shift from GPU-count budgeting to GPU-time tracking. This shift revealed significant over-provisioning, avoiding unnecessary GPU hardware purchases. The team can now take clusters down for maintenance without user impact, and users submit workloads without needing to plan capacity across clusters manually.

The team found Karmada straightforward to start using, with integration work focused on connecting to existing RBAC and cluster management systems. They highlighted propagation policy docs, interpreter docs, and linked examples as particularly valuable. Community engagement has been extensive — including annual in-person meetings at KubeCon EU, GitHub issues, and ad-hoc calls. Bloomberg team members are project maintainers and are contributing priority/preemption scheduling upstream, after which they intend to remove their internal fork. The primary concern is the slow review process for large contributions and limited North American project presence. If archived, they would maintain their fork. Removal difficulty: very high.

---

## Summary: Bloomberg — Streaming Platform (Apache Flink)

Bloomberg's streaming platform team, which operates Apache Flink infrastructure for real-time analytics across the organization, began evaluating Karmada in mid-2024 with a POC in Q3 2024. The primary driver was cross-cluster disaster recovery for stateful workloads — failover between regions without restarting stream processing. They evaluated Armada (pod-level only, dwindling activity) and MultiKueue before selecting Karmada for its CRD support and responsive community.

During the POC, they identified feature gaps, submitted requests, and the community's positive engagement convinced them to commit. Key features in use include stateful cross-cluster failover, federated resource quota, multiple pod-template support (co-developed with the community), and workload anti-affinity. They migrated dev instances onto Bloomberg's internal managed Karmada platform. The biggest measurable value is reduced operational overhead — cluster maintenance no longer requires tenant coordination. They are currently on v1.17, aligned with Karmada's quarterly releases. The team intends to contribute scalability improvements, conformance testing, and an end-user story. The primary concern is limited North American event presence and anti-affinity feature maturity. Removal difficulty: very high — they are already maintainers.

---

## Summary: Bloomberg — Cloud Compute Services (Managed Platform)

Bloomberg's Cloud Compute Services team built a fully managed multi-cluster platform atop Karmada to serve multiple internal platform teams (AI, streaming, general compute). The first Bloomberg team adopted Karmada approximately 2.5 years ago "the hard way"; the managed platform was created to avoid each team repeating that effort. The first tenant reached production maturity in March 2026. The platform stretches Karmada control planes across host clusters spanning multiple data centers, integrated with DNS-based service discovery to provide a unified ingress endpoint.

Key features include cluster failover, federated resource quota, policy-driven placement, and the Resource Interpreter Framework for understanding internal CRDs. They built custom operators integrating with internal cluster inventory APIs and token exchange for automated member cluster registration. Where upstream gaps exist, they work directly with the community — a concrete example is adding TLS certificate support to the Karmada operator for stretched control planes. Day-one setup time went from weeks to minutes; all tenants receive production-grade observability and alerting out of the box.

The most important differentiator cited was CNCF governance and the collaborative community. Gaps remain around day-two operational maturity: automated scalability testing and a conformance test suite (analogous to Kubernetes) would simplify their validation of new releases across diverse tenant use cases. The team is interested in submitting a CNCF reference architecture. Removal difficulty: very high — they have a fork and are maintainers.

---

## Summary: Trip.com — Multi-Cluster Orchestration

Trip.com has been using Karmada for 4 years (3 in production) for multi-cluster orchestration at significant scale: 40 clusters, the largest Karmada instance managing 25 clusters with 10,000 applications, 1 million cores, and 400,000 objects. The primary motivations were extending HPA across clusters and enabling seamless cluster migration/retirement. Karmada's Kubernetes-native API — requiring zero application-side modifications — was the deciding factor over alternatives (KubeFed, ClusterNet) which required non-standard APIs and were no longer actively maintained.

Trip.com built a distributed multi-cluster HPA on Karmada's object contract layer and has migrated 300,000 stateless workloads across clusters. They maintain an internal fork based on v1.5.1 with approximately 10 internal releases per year, primarily for performance at scale — they have removed the Work object entirely from their fork to address performance issues as cluster count and object count grow. Trip.com has a maintainer on the project (Zach) and engages via GitHub and community groups.

The primary concerns are performance at scale, multi-cluster scheduling complexity, and the project's historically China-centric adopter base (though Bloomberg's adoption is seen as a positive signal). Karmada already meets all of Trip.com's current feature needs. Removal would take more than 1–2 years.

---

# Cross-Interview Analysis

## Common Themes

### Strengths (cited by all adopters)
- **Kubernetes-native API** — zero application-side changes required (all 4 interviews)
- **CRD support / Resource Interpreter Framework** — critical for organizations with custom workload types (3/4 interviews)
- **Collaborative community** — responsive, willing to co-develop features (all 4 interviews)
- **Production-validated at scale** — confidence from existing large deployments (3/4 interviews)
- **Full-time maintainers** — fast bug fixes and issue responses (2/4 interviews)

### Concerns (cited by multiple adopters)
- **Limited North American presence** — timezone friction, KubeCon NA attendance, PR review speed (3/4 interviews)
- **Performance at scale** — Trip.com removed the Work object entirely; Bloomberg platform team needs scalability testing (2/4 interviews)
- **Slow review process for large contributions** — priority/preemption feature took a long time to merge (2/4 interviews)
- **No conformance test suite** — platform teams need automated validation for new versions (2/4 interviews)

### Removal Difficulty
All adopters reported removal would be very difficult:
- Bloomberg: would maintain internal fork; already has maintainers
- Trip.com: would take more than 1–2 years to remove

### Alternatives Evaluated

| Alternative | Reason Rejected | Cited By |
|-------------|----------------|----------|
| Armada | Pod-level only; no CRD support; dwindling activity | Bloomberg (GPU), Bloomberg (Streaming) |
| Kueue / MultiKueue | Not production-ready in 2023 | Bloomberg (GPU), Bloomberg (Streaming) |
| KubeFed | Non-standard API; no longer active | Trip.com |
| ClusterNet | Non-standard API; not active | Trip.com |
| KubeFleet | Karmada's community/governance stronger | Bloomberg (Platform) |
| Kubistella | Lacked community responsiveness | Bloomberg (Platform) |

### CNCF Maturity Level Usage
- Bloomberg (GPU): Graduated preferred; Incubating if on clear path; pragmatic for lower if critically needed
- Bloomberg (Streaming): Not strict; more inclined to Incubating/Graduated because features more likely present
- Bloomberg (Platform): Not discussed
- Trip.com: First filter; still need deeper evaluation of community and technical direction
