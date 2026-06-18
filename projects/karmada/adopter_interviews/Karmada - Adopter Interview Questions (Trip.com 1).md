# **Karmada \- Adopter Interview Questions (Trip.com 1\)**

Date: 05/29/2026

Attendees:

* Zongqing Li ([Trip.com](http://Trip.com))  
* HF Yue ([Trip.com](http://Trip.com))  
* Ahmed Bebars (TOC)  
* Chad Beaudin (TOC)

This template provides the **example set of questions** the TOC leverages in conducting adopter interviews for projects seeking to move levels. The TOC may use all, some, additional questions, or a combination thereof. This template may be linked to for scheduling interviews so that adopters know what to expect.

TOC members will summarize responses to the questions asked in a separate, non-public document until the Adopter approves the content. Once approval is received, the summarized content is copied into the Due Diligence document. Linking to the summary is NOT recommended as it may convey identifying information in the history if not properly access controlled which will circumvent anonymity assurances.

## **Setting expectations**

The intent of these interviews is to ascertain the maturity and adoption of the project by adopters of the project. They may be public or private.

Expectations conveyance with interviewers: “I’ll record raw notes here, then the notes will be cleaned up and shared with you for your review, correction, and final approval. Once approved, they’ll go into Karmada’s due diligence document.”

## **Questions**

1. How long has your organization used the project?  
   1. 4 years  
2. What were the main motivations to adopt the project, and which key features do you use today?  
   1. They rely heavily on HPA and extend across multiple clusters  
   2. Migrating or retiring clusters was a pain.  
   3. Karmada API model is mostly the same as a single cluster.  This was the primary reason they chose Karmada

3. Compared with other products and projects in this space (proprietary and open), what drew you to the project?  
   1. [KubeFed](https://github.com/kubernetes-retired/kubefed)  [ClusterNet](https://github.com/clusternet/clusternet) (2 Projects for Multi-Cluster Orchestrations)  
      1. Their APIs were not the same as those of the single-cluster model.  This would have forced them to modify their side  
      2. Not active

4. What is the current level of usage (pre-production, production) and scale?  
   1. Running in prod for 3 years.  
   2. Biggest cluster is running 10K applications, 1M cores, 400K objects  
   3. 40 total clusters.  The biggest Karmada instance is managing 25 clusters

5. What version of the project is currently in use, and what is your update cadence with the project?  
   1. Internal fork based on 1.5.1 (Karmada is currently working on 1.18)  
      1. They do 10 releases a year internally	  
      2. They feed back some changes, but others are “not wanted” by the broader community

6. Can you walk me through what your experience was in either adopting it outright or integrating it with your existing services and applications? What challenges did you experience with the project?  
   1. The team didn’t need to make any changes on their end since it is compatible with a single cluster API.  
   2. They built a distributed multi-cluster HPA and integrated that with Karmada. Using Karmada Objects/Contract as a layer for internal scaling architecture.  

7. Did you find the information in the repo or the project docs valuable to your implementation? If so, where did you find the information and what specifically was useful?  
   1. Karmada’s information was very valuable.  Their concept page and diagrams were a huge help in socializing Karmada’s concepts to other colleagues at Trip.com

8. Did you need to engage with the community members or maintainers? If so what was the context of the engagement, which communication channels did you use and did it reach an acceptable outcome?  
   1. Yes.  They had interactions with groups and github

9. Has your implementation of the project provided measurable value? Such as reducing manual activities, faster integrations, supported federation/multi-cloud, ease of use, cost savings, etc.  
   1. Karmada as an abstraction layer allowed them to migrate stateless workloads across clusters.  Migrated 300K workloads across clusters.  
   2. 

10. If the project were to be archived now or in the future, what level of difficulty would your organization experience to remove it from your environments? If that were to happen, would you fork and maintain the project to keep functionality, step into a maintainership role within the project, or something else?  
    1. It would be very hard to remove Karmada.  It would take more than 1-2 years to remove it.  
    2. Zach is one of the maintainers.

11. Is there something you feel that holds the project back from reaching its ultimate potential?  
    1. Performance and complexity of the multi-cluster scheduling.  
    2. Performance issues scales as the number of clusters and \# of objects in the cluster  
    3. They have removed the work object entirely from their internal version.  
    4. Scheduling.  Needs to distribute application instances across clusters and account for capacity.

12. In your opinion, what could the project improve?  
    1. Karmada was started in China by a chinese team.  Bloomberg's adoption was the biggest international user and they are hoping to see more  
    2. International meeting coordination

13. What are the overall strengths of the project?  
    1. Karmada’s K8s native approach  
    2. Karmada has a comprehensive multi-cluster orchestration capability, including policy based scheduling and failover.  
    3. Highly extensible  
    4. Active community compared to other projects in this space  
    5. Regular releases

14. Do you have any future plans regarding the project? More involvement, feature requests, expansion, etc.  
    1. Planning on using Karmada more internally.   
    2. Features:  Karmada already does everything they need for now.

### **Maturity Level Survey**

The following set of questions goes beyond the scope of the specific project adoption.

Their goal is to benefit from having access to CNCF project adopters and survey their understanding of the CNCF project maturity levels and any reliance on their meaning for decision making. This information should allow the TOC to better document maturity levels targeting adopters.

1. Do you feel you have a good understanding on the meaning of each maturity level for CNCF projects?  
   1. They know the levels, but not a deep understanding.  
   2. Graduated indicates a project should be very mature for use in production

2. Is there information missing regarding the meaning of each different level?  
   1. No

3. Do you rely on those levels internally in any way, and if yes how?  
   1. Helps them know which projects they *should* choose first.  
   2. Still need to find out which projects they need based on community activity or project's technical direction.  
   3. Maturity levels is the first loop, but still need the second loop.

