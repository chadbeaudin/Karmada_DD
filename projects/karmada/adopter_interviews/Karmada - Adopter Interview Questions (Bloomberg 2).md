# **Karmada \- Adopter Interview Questions (Bloomberg 2\)**

Date: 06/09/2026

Attendees:

* Michael Szacillo( Bloomberg)  
* Da Huo (Bloomberg)  
* Ahmed Bebars (TOC)  
* Chad Beaudin (TOC)

This template provides the **example set of questions** the TOC leverages in conducting adopter interviews for projects seeking to move levels. The TOC may use all, some, additional questions, or a combination thereof. This template may be linked to for scheduling interviews so that adopters know what to expect.

TOC members will summarize responses to the questions asked in a separate, non-public document until the Adopter approves the content. Once approval is received, the summarized content is copied into the Due Diligence document. Linking to the summary is NOT recommended as it may convey identifying information in the history if not properly access controlled which will circumvent anonymity assurances.

## **Setting expectations**

The intent of these interviews is to ascertain the maturity and adoption of the project by adopters of the project. They may be public or private.

Expectations conveyance with interviewers: “I’ll record raw notes here, then the notes will be cleaned up and shared with you for your review, correction, and final approval. Once approved, they’ll go into Karmada’s due diligence document.”

## **Questions**

1. How long has your organization used the project?  
   1. This team is the streaming platform.  Apache Flink to different teams within Bloomberg.  High volume real time analytics.  
   2. Mid 2024 started researching Karmada. POC Q3 2024  
   3. Identified feature gaps they would need to fulfill.  
   4. Submitted MVP feature requests to Karmada  
   5. Karmada community engagement sold them on Karmada and they decided to roll forward.  
   6. Interested specifically in their DR rollover from one cluster to another in a different region.  They have lots of stateful apps and starting processing over after a failover would be catastrophic.  
   7. 

2. What were the main motivations to adopt the project and which key features do you use today?  
   1. Covered above. Especially community engagement  
   2. Key Features today: stateful cross-cluster failover, federated resource quota.  This allowed them to capacity plan across clusters.  
   3. Multiple pod-template support (They helped work with Karmada on this)  
   4. Workload anti-affinity   
3. Compared with other products and projects in this space (proprietary and open) what drew you to the project?  
   1. Looked at Armada was CNCF sandbox.  Only designed to support pod scheduling.  They deal only with CRDs.  dwindling project support  
   2. MultiKueue.

4. What is the current level of usage (pre-production, production) and scale?  
   1. Production.  
   2. 

5. What version of the project is currently in use and what is your update cadence with the project?  
   1. They stay aligned with the Karmada quarterly release schedule  
   2. 1.17 from March

6. Can you walk me through what your experience was in either adopting it outright or integrating it with your existing services and applications? What challenges did you experience with the project?  
   1. Started with a POC.  Quickly discovered limitations for Bloomberg specific use cases  
   2. They intertwine with Joe A (from Bloomberg) and their use case here.  
      1. They migrated their dev instances over to Joe’s managed Karmada  
   3. They jumped in as contributors to drive the implementation of these new features.  
   4. 

7. Did you find the information in the repo or the project docs valuable to your implementation? If so, where did you find the information and what specifically was useful?  
   1. Dedicated architecture section describing the responsibility for each section.  
   2. Useful documentation that contained all of what they needed.

8. Did you need to engage with the community members or maintainers? If so what was the context of the engagement, which communication channels did you use and did it reach an acceptable outcome?  
   1. 2024 Kubecon EU, they talked with Karmada.  They attended Kubecon specifically to learn about any other multi-cluster organization.  They talked with Hongcai and Kevin after their Kubecon talk and   
   2. Kevin’s work on K8s scheduler lent a certain amount of “Street Cred” that Karmada was implementing things in an architecturally sound way.  
   3. 

9. Has your implementation of the project provided measurable value? Such as reducing manual activities, faster integrations, supported federation/multi-cloud, ease of use, cost savings, etc.  
   1. The biggest value comes from ease of maintenance.  Cluster maintenance used to require lots of tenant involvement to move to a different cluster.  Karmada has reduced much of that.

10. If the project were to be archived now or in the future, what level of difficulty would your organization experience to remove it from your environments? If that were to happen, would you fork and maintain the project to keep functionality, step into a maintainership role within the project, or something else?  
    1. They are already maintainers and have their own fork for testing purposes.  
    2. It would be very difficult to remove Karmada

11. Is there something you feel that holds the project back from reaching its ultimate potential?  
    1. Project involvement at Kubecon NA.  Hard to find representatives in US based events and time zones.  
    2. 

12. In your opinion, what could the project improve?  
    1. Add improvements to existing features.  
    2. Anti-affinity  
    3. North America based time zone representation.

13. What are the overall strengths of the project?  
    1. Comprehensive list of supported features  
       1. Cluster health monitoring  
       2. Stateful failover  
       3. CRD Support  
       4. Multiple pod template support  
       5. Workload anti-affinity  
       6. How active the community is (this is why they started using in the first place)  
       7. Strong list of adopters (this is why they started using in the first place)  
14. Do you have any future plans regarding the project? More involvement, feature requests, expansion, etc.  
    1. Contribute scalability  
    2. Conformance testing  
    3. Working on publishing end user story

### **Maturity Level Survey**

The following set of questions goes beyond the scope of the specific project adoption.

Their goal is to benefit from having access to CNCF project adopters and survey their understanding of the CNCF project maturity levels and any reliance on their meaning for decision making. This information should allow the TOC to better document maturity levels targeting adopters.

1. Do you feel you have a good understanding on the meaning of each maturity level for CNCF projects?  
   1. Yes  
   2. The higher you go towards graduation means the project is more mature.  Not necessarily focused just the amount of users.

2. Is there information missing regarding the meaning of each different level?  
   1. no

3. Do you rely on those levels internally in any way, and if yes how?  
   1. No, don’t use them strictly internally.  However, usually more inclined to use Incubating or Graduated because often the features you want are more likely in those more mature projects.

