# **Karmada \- Adopter Interview Questions (Bloomberg 3\)**

Date: 06/17/2026

Attendees:

* Joe Nathan Abellard (Bloomberg, Cloud Compute Services platform engineering — runs the shared managed Karmada clusters)
* Zhuyu Li (Bloomberg, Cloud Compute Services platform engineering — runs the shared managed Karmada clusters)
* Ahmed Bebars (TOC)
* Chad Beaudin (TOC)

This template provides the **example set of questions** the TOC leverages in conducting adopter interviews for projects seeking to move levels. The TOC may use all, some, additional questions, or a combination thereof. This template may be linked to for scheduling interviews so that adopters know what to expect.

TOC members will summarize responses to the questions asked in a separate, non-public document until the Adopter approves the content. Once approval is received, the summarized content is copied into the Due Diligence document. Linking to the summary is NOT recommended as it may convey identifying information in the history if not properly access controlled which will circumvent anonymity assurances.

## **Setting expectations**

The intent of these interviews is to ascertain the maturity and adoption of the project by adopters of the project. They may be public or private.

Expectations conveyance with interviewers: "I'll record raw notes here, then the notes will be cleaned up and shared with you for your review, correction, and final approval. Once approved, they'll go into Karmada's due diligence document."

## **Questions**

1. How long has your organization used the project?

   Data center redundancy to maintain continuity of service in disaster scenarios is an organizational mandate at Bloomberg. Multi-cluster orchestration has evolved as a key enabler for achieving that at scale, and they adopted Karmada as the multi-cluster orchestrator for their platform team.

   The first team to adopt Karmada did so "the hard way" about two and a half years ago, setting up and maintaining all infrastructure themselves. Given that other platform teams were interested — and they didn't want each team to repeat that effort — they built a fully managed multi-cluster platform atop Karmada to serve all use cases, enabling platform teams to ship applications without needing deep multi-cluster expertise.

   Each tenant goes through an onboarding journey that culminates in production maturity for their specific use case. The first team to reach production maturity on the managed platform did so in March 2026.

2. What were the main motivations to adopt the project and which key features do you use today?

   The major motivation is meeting Bloomberg's requirements for high availability and disaster recovery across distributed infrastructure. They also want teams to onboard to Karmada infrastructure without needing deep multi-cluster knowledge.

   Key features highlighted:
   - **Cluster failover** — critical for DR testing; if a cluster goes unhealthy, workloads are rescheduled to other member clusters.
   - **Federated resource quota** — governs resource quota usage for tenants with workloads running across different clusters.
   - **Policy-driven placement** — declarative approach to propagating workloads across clusters.
   - **Resource Interpreter Framework** — allows Karmada to understand Bloomberg's internal CRDs for different workload types.

3. Compared with other products and projects in this space (proprietary and open) what drew you to the project?

   Evaluated KubeFleet, Kubistella, and Armada. Karmada differentiated itself with:
   - Kubernetes-native API enabling seamless integration with the K8s toolchain and ecosystem.
   - Policy-driven placement for declarative resource scheduling.
   - Cluster failover support for handling disaster scenarios.

   But the most important differentiator was **CNCF governance and a very collaborative community** willing to work with them to address gaps identified during adoption. It has been a very positive experience — they have addressed gaps for running stateful applications (e.g., Flink deployments across clusters) and operational gaps in the Karmada operator used to provision control plane infrastructure for tenants.

4. What is the current level of usage (pre-production, production) and scale?

   The managed service is generally available for production users. They support many tenants, each going through the onboarding journey. Currently have tenants running production workflows on the managed platform.

5. What version of the project is currently in use and what is your update cadence with the project?

   Karmada follows a version support policy similar to Kubernetes — the most recent 3 minor releases are actively supported. The managed platform follows the same policy: for every new Karmada release, they validate it on the managed platform before adding support for tenants. The platform team handles upgrades so tenants don't have to deal with it.

6. Can you walk me through what your experience was in either adopting it outright or integrating it with your existing services and applications? What challenges did you experience with the project?

   To run the managed platform, they rely on the upstream Karmada operator for provisioning control plane infrastructure for all tenants. In addition, they've built custom operators that integrate with internal systems — such as a cluster inventory API and token exchange servers — to fully automate member cluster registration for tenants.

   Where they've identified gaps in upstream components, they've worked closely with the community to address them. A concrete example: to meet Bloomberg's mandate for HA and DR, they run all control planes stretched across a cohort of host clusters spanning multiple data centers, integrated with their DNS-based service discovery platform to provide one unified ingress endpoint. Making that work required using the same TLS certificate to provision the stretched instance across host clusters, which required adding support to the Karmada operator — something they worked on closely with the community.

7. Did you find the information in the repo or the project docs valuable to your implementation? If so, where did you find the information and what specifically was useful?

   Very useful. The documentation provides a good foundation when first learning the project with enough detail. When diving deep into specific features (failover, propagation policy), it has very detailed documentation to explore and try things independently.

   They are also contributing back documentation for areas they found missing but helpful — specifically around availability and scalability, which are focus areas for satisfying Bloomberg's needs.

8. Did you need to engage with the community members or maintainers? If so what was the context of the engagement, which communication channels did you use and did it reach an acceptable outcome?

   Yes. Primary channels:
   - **GitHub issues** — very responsive; as long as issues have good descriptions and proposals, replies are very quick.
   - **Bi-weekly community meetings** — opportunity to provide more information and have deeper discussions.

   Overall, community engagement has been very positive with good outcomes for all interactions.

9. Has your implementation of the project provided measurable value? Such as reducing manual activities, faster integrations, supported federation/multi-cloud, ease of use, cost savings, etc.

   Yes, great measurable outcomes:
   - **Day-one setup time:** Managing multi-cluster infrastructure "the hard way" takes weeks. With the managed platform, teams can set up within minutes.
   - **Day-two operational savings:** Significant time saved across all platform teams for ongoing infrastructure maintenance.
   - **Production-grade observability:** All tenants get observability and alerting out of the box when onboarded onto the platform.

10. If the project were to be archived now or in the future, what level of difficulty would your organization experience to remove it from your environments? If that were to happen, would you fork and maintain the project to keep functionality, step into a maintainership role within the project, or something else?

    They already have a fork and have maintainers on the project. Removal would be very difficult.

11. Is there something you feel that holds the project back from reaching its ultimate potential?

    Gaps around **operational resilience** for platform teams. It's one thing to set up infrastructure, but day-two operations (observability, alerting, testing new releases) need more maturity. These gaps could hold back wider adoption. They are currently working with the community on scalability testing and conformance testing initiatives, drawing from established Kubernetes community patterns.

12. In your opinion, what could the project improve?

    Strong signals about project maturity are missing:
    - **Automated scalability testing** — like the Kubernetes project has — so teams running at very large scale can be assured of support without doing the validation work themselves.
    - **Conformance test suite** — like the Kubernetes project has — so platform teams can run it to validate each new version before supporting it for tenants. This would greatly simplify their upgrade process.

    These improvements are important because they follow Karmada's 3-version support policy and need efficient ways to validate new releases for their tenants across diverse use cases (AI, streaming analytics, general compute).

13. What are the overall strengths of the project?

    The collaborative community and CNCF governance were highlighted as the most important strengths — both for Bloomberg and for the project itself.

14. Do you have any future plans regarding the project? More involvement, feature requests, expansion, etc.

    They want to continue engaging with the community and deepen the relationship. Specific future work is driven by need — when new tenants onboard with unique use cases that expose gaps, they will work with the community on their behalf to address those.

    Additionally, they are interested in submitting a **CNCF reference architecture** for how they built a managed multi-cluster platform on top of Karmada. The TOC encouraged this submission, noting no existing reference architectures focus on multi-cluster management.

### **Maturity Level Survey**

The following set of questions goes beyond the scope of the specific project adoption.

Their goal is to benefit from having access to CNCF project adopters and survey their understanding of the CNCF project maturity levels and any reliance on their meaning for decision making. This information should allow the TOC to better document maturity levels targeting adopters.

1. Do you feel you have a good understanding on the meaning of each maturity level for CNCF projects?

   *(Not explicitly answered in this interview.)*

2. Is there information missing regarding the meaning of each different level?

   *(Not explicitly answered in this interview.)*

3. Do you rely on those levels internally in any way, and if yes how?

   *(Not explicitly answered in this interview.)*

---

*Interview conducted 06/17/2026. Answers summarized from Zoom transcript. Pending review and approval by Joe Nathan Abellard and Zhuyu Li / Bloomberg before public release.*
