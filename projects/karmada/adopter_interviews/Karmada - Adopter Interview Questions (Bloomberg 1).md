# **Karmada \- Adopter Interview Questions (Bloomberg 1\)**

Date: 05/29/2026

Attendees:

* Yuzhui Liu ( Bloomberg)  
* Ahmed Bebars (TOC)  
* Chad Beaudin (TOC)

This template provides the **example set of questions** the TOC leverages in conducting adopter interviews for projects seeking to move levels. The TOC may use all, some, additional questions, or a combination thereof. This template may be linked to for scheduling interviews so that adopters know what to expect.

TOC members will summarize responses to the questions asked in a separate, non-public document until the Adopter approves the content. Once approval is received, the summarized content is copied into the Due Diligence document. Linking to the summary is NOT recommended as it may convey identifying information in the history if not properly access controlled which will circumvent anonymity assurances.

## **Setting expectations**

The intent of these interviews is to ascertain the maturity and adoption of the project by adopters of the project. They may be public or private.

Expectations conveyance with interviewers: “I’ll record raw notes here, then the notes will be cleaned up and shared with you for your review, correction, and final approval. Once approved, they’ll go into Karmada’s due diligence document.”

## **Questions**

1. How long has your organization used the project?

   Started evaluation towards end of 2023. Production use began mid-2024.

2. What were the main motivations to adopt the project and which key features do you use today?

   Bloomberg's team handles GPU-intensive batch workloads (primarily model training) across multiple HPC clusters. Previously, each user budgeted peak GPU count (e.g., 20 GPUs), which led to over-provisioning because actual workloads are spiky. They needed a multi-cluster scheduler that could schedule across clusters whenever capacity was available, shifting the quota model from GPU count to GPU time. Karmada serves as that multi-cluster scheduler sitting in front of their GPU clusters.

3. Compared with other products and projects in this space (proprietary and open) what drew you to the project?

   They evaluated two alternatives:
   - **Armada** — a strong project, but its scheduling unit is the pod. Bloomberg had already developed custom Kubernetes resources for their workloads, which Armada did not support. Karmada supports custom resources natively.
   - **Kueue** — still under development in 2023, not production-ready at the time.

   Karmada was the only option already productionized with known large-company production users that could address their requirements.

4. What is the current level of usage (pre-production, production) and scale?

   Production. Scale information cannot be shared publicly.

5. What version of the project is currently in use and what is your update cadence with the project? (do not share version information publicly)

   *(Version information is not for public disclosure.)* Running an internal fork. Major upgrades are baked into quarterly plans; urgent patches are applied as needed. The internal fork exists to fast-track deployment of features pending upstream merge (specifically priority and preemption scheduling). The goal is to remove the internal fork once those features merge upstream and switch to official releases.

6. Can you walk me through what your experience was in either adopting it outright or integrating it with your existing services and applications? What challenges did you experience with the project?

   Overall, they found Karmada relatively straightforward to start using. The significant work was in integration with existing systems: connecting Karmada with existing APIs for cluster management and RBAC, standing up independent clusters to deploy Karmada, and building failover capability so that if one cluster goes down, operations continue. The initial architecture was designed during a KubeCon Amsterdam meeting with Karmada maintainers (literally sketched out over dinner/drinks).

7. Did you find the information in the repo or the project docs valuable to your implementation? If so, where did you find the information and what specifically was useful?

   Yes. Their engineers specifically called out:
   - Propagation policy documentation
   - Interpreter documentation
   - Linked example code (found particularly helpful)

8. Did you need to engage with the community members or maintainers? If so what was the context of the engagement, which communication channels did you use and did it reach an acceptable outcome?

   Yes, extensively. Communication channels used:
   - **Annual in-person meetings at KubeCon Europe** — they meet the maintainers every year, including dinners together. The initial architecture was laid out at the first KubeCon Amsterdam meeting.
   - **GitHub issues** — one of the main channels.
   - **US adopter community meetings** — they attend these.
   - **Ad-hoc scheduled calls** — for specific questions or discussions.

   Bloomberg team members are also project maintainers and are actively contributing priority and preemption scheduling logic back upstream.

9. Has your implementation of the project provided measurable value? Such as reducing manual activities, faster integrations, supported federation/multi-cloud, ease of use, cost savings, etc.

   Yes, two major achievements:
   - **Cluster federation / high availability:** They can take a cluster down for maintenance and put it back seamlessly without user impact.
   - **Cost savings:** By shifting from GPU-count quota to GPU-time tracking, they discovered their actual capacity utilization was much lower than what was budgeted on paper. This avoided unnecessary GPU hardware purchases.
   - **Operational efficiency:** Eliminated manual tenant onboarding and capacity planning conversations. Users simply submit workloads into the queue and the scheduler handles placement across clusters.

10. If the project were to be archived now or in the future, what level of difficulty would your organization experience to remove it from your environments? If that were to happen, would you fork and maintain the project to keep functionality, step into a maintainership role within the project, or something else?

    It would be a significant amount of work to move away from Karmada due to the extensive integration effort already invested. If archived, they would maintain their existing internal fork and continue operating. Bloomberg already has team members serving as project maintainers.

11. Is there something you feel that holds the project back from reaching its ultimate potential?

    Fewer US adopters compared to China. This creates:
    - Timezone scheduling friction when needing to discuss with maintainers.
    - Slower PR reviews due to the geographic distribution of contributors.

12. In your opinion, what could the project improve?

    For large proposals/features, have more frequent reviews. Their team contributed the priority and preemption feature, and getting the proposal reviewed, approved, and code merged took a very long time. A faster review process for substantial contributions would be an improvement.

13. What are the overall strengths of the project?

    - **Ease of use** — not difficult to start.
    - **Production validation** — multiple large Chinese companies already using it in production gives confidence that bugs are fixed and it's thoroughly tested.
    - **Full-time maintainers** — bug fixes are very quick.
    - **Rich functionality** — many features available; you can selectively adopt what you need.

14. Do you have any future plans regarding the project? More involvement, feature requests, expansion, etc.

    Primary plan is to contribute the priority and preemption scheduling logic back to upstream. Once that feature merges, they intend to remove their internal fork and rely solely on the upstream version.

### **Maturity Level Survey**

The following set of questions goes beyond the scope of the specific project adoption.

Their goal is to benefit from having access to CNCF project adopters and survey their understanding of the CNCF project maturity levels and any reliance on their meaning for decision making. This information should allow the TOC to better document maturity levels targeting adopters.

1. Do you feel you have a good understanding on the meaning of each maturity level for CNCF projects?

   Yes. They typically choose Graduated projects first. If not available, they look for Incubating projects that are on a clear path to graduation. They have a good understanding after reading the documentation, though without re-reading, Sandbox and Incubating can feel somewhat similar.

2. Is there information missing regarding the meaning of each different level?

   The website documentation is clear enough when read carefully. One observation: Sandbox and Incubating can sound similar at first glance, but reading the detailed definitions makes the distinction clear.

3. Do you rely on those levels internally in any way, and if yes how?

   Yes, they do rely on maturity levels for internal decision-making. Preference is for Graduated projects, then Incubating if on a clear graduation path. However, they take a pragmatic approach: if they critically need something that's only available at Sandbox or Incubating level, they will adopt it and try to help the project mature.

---

*Interview conducted 05/29/2026. Answers summarized from Zoom transcript. Pending review and approval by Yuzhui Liu / Bloomberg PR team before public release.*
