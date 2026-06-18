# Karmada Graduation Due Diligence

- Link to [Graduation application issue](https://github.com/cncf/toc/issues/1572)

<!-- This template provides the TOC with the outline for completing due diligence of a project to move levels. This universal template is designed to capture all criteria so the TOC may ensure prior level criteria do not regress. As part of completing the due diligence, the TOC member should update the template to convey the level the project applied for the criteria by bolding the level indicated where the criteria is relevant. -->

## Graduation Evaluation Summary for Karmada

### Criteria Evaluation

Chad Beaudin and Ahmed Bebars conducted the due diligence of Karmada who applied for Graduation. The project has completed the criteria that show its maturity at Graduation. Noteworthy strengths include strong multi-org maintainer diversity (8 maintainers across 6 organizations with a documented rule that no single organization can hold more than 50% of the maintainer seats), a completed third-party security audit with all high/medium findings resolved, and a consistent 3-month release cadence. The following actions were provided to the project that were considered blocking but since resolved: the 2023 governance review identified a single CoC concern that has been rectified (now a single canonical CODE_OF_CONDUCT.md pointing to the CNCF CoC). The following recommendations were provided to the project that are non-blocking in the TOC's assessment but should be completed to ensure continued viability: (1) move the 4 inactive maintainers identified in the 2023 governance review to emeritus status, (2) resolve inconsistencies in OWNERS files across repos, and (3) continue work on automated certificate rotation to reduce operational burden at scale.

### Adoption Evaluation

The adopter interviews reflect a project in production use and at scale commensurate for graduation. Interviews span diverse industries and geographies including finance (Bloomberg), travel (Trip.com), and large-scale internet platforms, demonstrating that Karmada is being used for real multi-cluster workload management in production environments. <!-- TODO verify: third interview (Xiaohongshu/Bilibili) not yet completed -->

### Final Assessment

The TOC has found the project to have satisfied the criteria for Graduation. Karmada has clearly matured since incubation (Dec 2023) with improved governance diversity, a completed security audit, strong adoption growth across industries, and a maintained release cadence. No fundamental blockers remain.

### Criteria

## Application Process Principles

### Suggested

Maintainers file should be kept up to date.

### Required

- [x] **Engage with the domain specific TAG(s) to increase awareness through a presentation or completing a General Technical Review.**
  - A General Technical Review was completed on 21-Apr-2026 by @brandtkeller via [PR #2133](https://github.com/cncf/toc/pull/2133). The GTR Q&A document is available at [projects/karmada/tech-review/2026-04-21.md](https://github.com/brandtkeller/toc/blob/1769_karmada_technical_review/projects/karmada/tech-review/2026-04-21.md).

The GTR confirmed that Karmada's control plane architecture (karmada-apiserver, karmada-controller-manager, karmada-scheduler, karmada-webhook, karmada-agent) provides clear separation of concerns for multi-cluster management. Two areas were called out:

1. **Certificate management is manual.** Certificates for cluster registration are stored in Kubernetes ConfigMaps/Secrets and must be provisioned and rotated by cluster administrators. At scale (dozens of clusters), this adds operational burden. The project has active work to address this: [PR #5037](https://github.com/karmada-io/karmada/pull/5037) (automatic cert rotation) and [PR #6553](https://github.com/karmada-io/karmada/pull/6553) (cert rotation on helm upgrade). Known limitation with a tracked improvement path; not a graduation blocker.
1. **Upgrade/downgrade/upgrade path was not tested.** Not significant, but noted for completeness.

- [x]  **All project metadata and resources are [vendor-neutral](https://contribute.cncf.io/maintainers/community/vendor-neutrality/).**

  Communication channels (Slack, mailing list, GitHub) are neutral. The project is hosted under the CNCF umbrella with no single-vendor branding. Adopter interviews repeatedly highlighted the responsiveness and strength of the projects' community.

- [x] **Review and acknowledgement of expectations for [Sandbox](sandbox.cncf.io) projects and requirements for moving forward through the CNCF Maturity levels.**		
   - [x] Met during Project's application on 26-Mar-2025. Application triaged 03-Sep-2025 by @jeremyrickard who confirmed it was sufficient for DD.

- [ ] **Due Diligence Review.**

Completion of this due diligence document, resolution of concerns raised, and presented for public comment satisfies the Due Diligence Review criteria.

- [x] **Additional documentation as appropriate for project type, e.g.: installation documentation, end user documentation, reference implementation and/or code samples.**

  Installation documentation, tutorials, and contributor guides are all publicly available at [karmada.io/docs](https://karmada.io/docs/). The project provides multiple installation methods (Helm, karmadactl, binary) with step-by-step guides. API reference documentation and example configurations are maintained alongside the codebase.

## Governance and Maintainers

A governance review was conducted in August 2023 and documented at [governance-review/2023-08-29.md](governance-review/2023-08-29.md). The review identified three must-fix items: inactive maintainers, conflicting OWNERS files, and conflicting Codes of Conduct. Since then, the CoC has been rectified to a single canonical document pointing to the CNCF CoC. The OWNERS file inconsistencies have been raised as a [comment on the DD issue](https://github.com/cncf/toc/issues/1572#issuecomment-4452003587) and should be resolved.

However, the inactive maintainer issue remains outstanding with 4 maintainers flagged in 2023 (@mrlihanbo, @carmark, @zoroyouxi, @lfbear) have not been moved to emeritus, and a [comment](https://github.com/cncf/toc/issues/1572#issuecomment-4451663241) was made requesting this be addressed. The project can improve the accuracy of their MAINTAINERS.md to reflect actual activity levels.

Overall the project has good governance and a diverse set of maintainers.

### Suggested

- [x]  **Governance has continuously been iterated upon by the project as a result of their experience applying it, with the governance history demonstrating evolution of maturity alongside the project's maturity evolution.**

  The project's governance has evolved since incubation. Key improvements include diversifying maintainership across 6 organizations, establishing the 50% cap rule, rectifying the CoC, and expanding community roles. The git history of governance documents shows iterative refinement over time.

### Required

- [x] **Clear and discoverable project governance documentation.**

  Governance documentation is publicly available in the [karmada-io/community](https://github.com/karmada-io/community) repository, including maintainer roles, decision-making processes, and community membership ladder. Governance links are discoverable from the main project README. 

- [x] **Governance is up to date with actual project activities, including any meetings, elections, leadership, or approval processes.**

  Community meetings are held regularly (bi-weekly) and recorded. Meeting notes are publicly available. The maintainer list reflects current active contributors, though the 4 inactive maintainers flagged in 2023 still need to be moved to emeritus (open PR for this). 

- [x] **Governance clearly documents [vendor-neutral](https://contribute.cncf.io/maintainers/community/vendor-neutrality/) of project direction.**

  Governance values include a documented maintainer cap rule (see "Project maintainers from at least 2 organizations" below). Communication channels are vendor-neutral (CNCF Slack, GitHub, mailing list). No single vendor controls project direction. 

- [x] **Document how the project makes decisions on leadership, contribution acceptance, requests to the CNCF, and changes to governance or project goals.**

  Decision-making processes are documented in the community governance docs. Contributions follow a standard PR review process with maintainer approval. Leadership changes follow the documented maintainer lifecycle. The project uses lazy consensus for routine decisions and formal votes for significant governance changes. 

- [x] **Document how role, function-based members, or sub-teams are assigned, onboarded, and removed for specific teams (example: Security Response Committee).**

  The community membership document defines roles (member, reviewer, approver, maintainer) with clear requirements for each level. The security team is documented in [karmada-io/community/security-team](https://github.com/karmada-io/community/tree/main/security-team) with defined membership and responsibilities. Onboarding and removal criteria are specified for each role.

- [x] **Document a complete maintainer lifecycle process (including roles, onboarding, offboarding, and emeritus status).**

  Documented in the project governance. However, the offboarding/emeritus path has not been actively demonstrated. Innactive members should be moved to emeritus. A [comment](https://github.com/cncf/toc/issues/1572#issuecomment-4451663241) was made on the DD issue requesting this be addressed.

- [x] **Demonstrate usage of the maintainer lifecycle with outcomes, either through the addition or replacement of maintainers as project events have required.**

 The 2023 governance review identified 4 inactive maintainers who remain listed. Resolution of this is tracked as a DD action item.

- [x] **Document complete list of current maintainers, including names, contact information, domain of responsibility, and affiliation.**

  MAINTAINERS.md in the main repository lists all current maintainers with GitHub handles and organizational affiliations. The 8 maintainers span 6 organizations (Huawei, ByteDance, Moore Threads, DaoCloud, ICBC, VIPKID).

- [x] **A number of active maintainers which is appropriate to the size and scope of the project.**

  8 maintainers is appropriate for a project of Karmada's scope (multi-cluster orchestration with multiple components). The maintainer count has grown since incubation and represents sufficient coverage across the project's subsystems.

- [x] **Project maintainers from at least 2 organizations that demonstrates survivability.**

  8 maintainers from 6 organizations: Huawei, ByteDance, Moore Threads, DaoCloud, ICBC, VIPKID. A documented 50% cap rule prevents any single organization from holding majority maintainership. This is a meaningful improvement from the 2023 review which flagged Huawei-heavy maintainership.

- [x] **Code and Doc ownership in Github and elsewhere matches documented governance roles.**

  OWNERS files exist across repos.

- [x] **Document adoption and adherence to the CNCF Code of Conduct or the project's CoC which is based off the CNCF CoC and not in conflict with it.**

  CoC issue from the 2023 governance review has been rectified. The project now has a single canonical CODE_OF_CONDUCT.md pointing to the CNCF CoC.

- [x] **CNCF Code of Conduct is cross-linked from other governance documents.**

  The CNCF CoC is referenced from the community repository and contribution guidelines.

- [x] **All subprojects, if any, are listed.**

  Subprojects are listed in the [karmada-io GitHub organization](https://github.com/karmada-io), including karmada (core), dashboard, community, and website repositories.

- [x] **If the project has subprojects: subproject leadership, contribution, maturity status documented, including add/remove process.**

  Each repository under the karmada-io organization has OWNERS files defining approvers and reviewers. The community repo documents the overall governance structure that applies across subprojects. 

## Contributors and Community

Note: this section may be augmented by the completion of a Governance Review from the Project Reviews subproject.

### Suggested

- [x] **Contributor ladder with multiple roles for contributors.**

  The project defines a clear contributor ladder: contributor, member, reviewer, approver, and maintainer. Each level has documented requirements and responsibilities in the community membership documentation. 

### Required

- [x] **Clearly defined and discoverable process to submit issues or changes.**

  Issues are tracked via GitHub Issues on the main karmada repository. The CONTRIBUTING.md documents the process for submitting issues, feature requests, and pull requests. Issue templates are provided for bugs and feature requests. 

- [x] **Project must have, and document, at least one public communications channel for users and/or contributors.**

  The project maintains multiple public channels: CNCF Slack (#karmada), community meetings, GitHub Discussions, and a mailing list. All are linked from the project's community documentation. 

- [x] **List and document all project communication channels, including subprojects (mail list/slack/etc.).  List any non-public communications channels and what their special purpose is.**

  Documented channels include: CNCF Slack (#karmada), bi-weekly community meetings (with recorded sessions), GitHub Issues/Discussions, and the karmada-io mailing list. The security team has a private mailing list (cncf-karmada-security@lists.cncf.io) for vulnerability reports, which is appropriate and documented. 

- [x] **Up-to-date public meeting schedulers and/or integration with CNCF calendar.**

  Bi-weekly community meetings are listed on the CNCF community calendar. Meeting details (time, Zoom link, agenda doc) are documented in the community repository. 

- [x] **Documentation of how to contribute, with increasing detail as the project matures.**

  CONTRIBUTING.md provides a comprehensive guide covering development environment setup, coding conventions, PR process, and testing requirements. The contributor ladder documentation shows increasing responsibility with maturity. 

- [x] **Demonstrate contributor activity and recruitment.**

  The project shows healthy contributor activity per [CNCF DevStats](https://karmada.devstats.cncf.io/). Contributors span multiple organizations and the project has grown its maintainer base from a Huawei-dominated set to 6 organizations since incubation. Regular community meetings and active GitHub issue/PR activity demonstrate ongoing recruitment and engagement. 

## Engineering Principles

### Suggested

N/A

### Required

- [x] **Document project goals and objectives that illustrate the project’s differentiation in the Cloud Native landscape as well as outlines how this project fulfills an outstanding need and/or solves a problem differently. _This requirement may also be satisfied by completing a General Technical Review._**
  - A General Technical Review was completed on 21-Apr-2026 by @brandtkeller, and can be discovered at [PR #2133](https://github.com/cncf/toc/pull/2133).

  Karmada differentiates itself as a Kubernetes-native multi-cluster management system that extends the Kubernetes API to work across clusters without requiring changes to existing workload definitions. The GTR confirmed this differentiation and the project's unique position in the CNCF landscape for multi-cluster orchestration.

- [x] **Document what the project does, and why it does it - including viable cloud native use cases. _This requirement may also be satisfied by completing a General Technical Review._**
  - A General Technical Review was completed on 21-Apr-2026, and can be discovered at [PR #2133](https://github.com/cncf/toc/pull/2133).

- [x] **Document and maintain a public roadmap or other forward looking planning document or tracking mechanism.**

  A public roadmap is maintained in the community repository and referenced from the project website. GitHub milestones track upcoming releases and planned features.

- [x] **Roadmap change process is documented.**

  Roadmap items are proposed and discussed through GitHub issues and community meetings. Significant changes are reviewed by maintainers before inclusion. 

- [x] **Document overview of project architecture and software design that demonstrates viable cloud native use cases, as part of the project's documentation.  *This requirement may also be satisfied by completing a General Technical Review and capturing the output in the project's documentation.***
  - A General Technical Review was completed on 21-Apr-2026, and can be discovered at [PR #2133](https://github.com/cncf/toc/pull/2133).

  The GTR confirmed that the architecture (karmada-apiserver, karmada-controller-manager, karmada-scheduler, karmada-webhook, karmada-agent) provides clear separation of concerns. Both push and pull modes for cluster management are well-designed for different network topology requirements.

- [x] **Document the project's release process and guidelines publicly in a RELEASES.md or equivalent file that defines:** 

  - [x] Release expectations (scheduled or based on feature implementation)
  - [x] Tagging as stable, unstable, and security related releases
  - [x] Information on branch and tag strategies
  - [x] Branch and platform support and length of support
  - [x] Artifacts included in the release.
  - Additional information on topics such as LTS and edge releases are optional. Release expectations are a social contract between the project and its end users and hence changes to these should be well thought out, discussed, socialized and as necessary agreed upon by project leadership before getting rolled out.

  The project follows a 3-month release cadence with semantic versioning. Support policy covers the 3 most recent minor releases (~9 months of patches). Release artifacts (binaries, container images, Helm charts) and supported platforms are documented. The release process is publicly described in the community repository. 

- [x] **History of regular, quality releases.**

  Regular 3-month release cadence with semantic versioning. Clear support policy: 3 most recent minor releases supported (~9 months of patches). Well-documented artifacts and platform support. 

## Security

Note: this section may be augmented by a joint-assessment performed by TAG Security and Compliance.

### Suggested

- [x] **Achieving OpenSSF Best Practices silver or gold badge.**

  The project has achieved the passing level badge. Silver/gold level work is in progress. The passing badge demonstrates commitment to security best practices including vulnerability disclosure, signed releases, and static analysis. 

### Required

- [x] **Clearly defined and discoverable process to report security issues.**

  Security vulnerability reporting process is documented in [SECURITY.md](https://github.com/karmada-io/community/blob/main/security-team/SECURITY.md). Researchers can report vulnerabilities confidentially via email to cncf-karmada-security@lists.cncf.io with a 2-business-day acknowledgment SLA. 

- [x] **Enforcing Access Control Rules to secure the code base against attacks (Example: two factor authentication enforcement, and/or use of ACL tools.)**

  The project is hosted under the karmada-io GitHub organization with branch protection rules on the main branch. Maintainers are required to use 2FA on their GitHub accounts. OWNERS files control merge approval authority across repos. 

- [x] **Document assignment of security response roles and how reports are handled.**

  The security team is documented in the community repository at [security-team/](https://github.com/karmada-io/community/tree/main/security-team). Vulnerability reports go to cncf-karmada-security@lists.cncf.io with a 2-business-day acknowledgment SLA. The team triages, coordinates fixes privately, and discloses after patches are available. 

- [x] **Document Security Self-Assessment.**

  A security self-assessment was completed as part of the TAG Security [Security Pals](https://github.com/cncf/tag-security/issues/1102) process, including a [STRIDE threat model](https://github.com/cncf/tag-security/blob/main/assessments/projects/karmada/threatmodeling.md). 

- [x] **Third Party Security Review.**

  A third-party security audit was performed by [Shielder](https://www.shielder.com) (commissioned by OSTIF) against Karmada v1.11.0 in September-October 2024. The [final report](https://github.com/karmada-io/community/blob/main/security-team/assessments/OSTIF-Karmada-Report.pdf) was published January 9, 2025. Six findings were identified:

  | ID | Finding | Severity | Status |
  | -- | ------- | -------- | ------ |
  | 1 | Insecure Design of Pull Mode | HIGH | Closed ([PR #5793](https://github.com/karmada-io/karmada/pull/5793), v1.12.0) |
  | 2 | Multiple TarSlips in CRDs Archive Extraction | MEDIUM | Closed ([PR #5703](https://github.com/karmada-io/karmada/pull/5703), [PR #5713](https://github.com/karmada-io/karmada/pull/5713), v1.12.0) |
  | 3 | Insecure Default Configuration | LOW | Closed ([PR #5739](https://github.com/karmada-io/karmada/pull/5739), v1.12.0) |
  | 4 | Bootstrap Token Leaked in Command Output | INFORMATIONAL | Closed ([PR #5714](https://github.com/karmada-io/karmada/pull/5714), v1.12.0) |
  | 5 | Denial of Service (DoS) in LuaVM Package | LOW | Open (upstream dependency - gopher-lua maintainer unresponsive) |
  | 6 | K8s Pods Executed with Unnecessary Privileges | INFORMATIONAL | Open |

  All high and medium findings were resolved in Karmada v1.12.0 (released November 30, 2024). The two remaining open items are low/informational severity: Finding 5 is blocked on an unresponsive upstream dependency (gopher-lua), and Finding 6 is a hardening recommendation for pod security contexts.

  - [x] Moderate and low findings from the Third Party Security Review are planned/tracked for resolution as well as overall thematic findings. The low-severity LuaVM DoS (Finding 5) is tracked and blocked on an upstream fix. The informational pod-privileges item (Finding 6) is a hardening recommendation with no immediate security impact. 

- [x] **Achieve the Open Source Security Foundation (OpenSSF) Best Practices passing badge.**

  Karmada has achieved the passing level: [OpenSSF Best Practices Badge #5301](https://www.bestpractices.dev/en/projects/5301). 

## Ecosystem

### Suggested

N/A

### Required

- [x] **Publicly documented list of adopters, which may indicate their adoption level (dev/trialing, prod, etc.)**

  30+ public production adopters listed at [karmada.io/adopters](https://karmada.io/adopters) spanning diverse industries: finance (ICBC, Bloomberg), travel (Trip.com), social media (Xiaohongshu), video (Bilibili), cloud (Huawei), and more. 

- [x] **Used in appropriate capacity by at least 3 independent + indirect/direct adopters, (these are not required to be in the publicly documented list of adopters)**

  7 adopters submitted via the TOC interview form. Interviews targeted across industries:

  - Bloomberg — GPU/HPC scheduling team (production since mid-2024)
  - Bloomberg — Streaming platform team (production 2024)
  - Bloomberg — Cloud Compute Services / managed Karmada platform (first tenant production March 2026)
  - Trip.com — Multi-cluster orchestration (3 years in production, 40 clusters, 1M cores)

The project provided the TOC with a list of adopters for verification of use of the project at the level expected, i.e. production use for graduation, dev/test for incubation.

- [x] **TOC verification of adopters.**

  Adopter interviews were conducted across multiple industries to verify production use. Bloomberg (finance), Trip.com (travel), and additional large-scale adopters Bilibili (large-scale Chinese internet) (TODO)  confirmed production deployments managing multi-cluster workloads at scale.

Refer to the Adoption portion of this document.

- [x] **Clearly documented integrations and/or compatibility with other CNCF projects as well as non-CNCF projects.**

  12+ documented integrations including: Argo CD, Flux, Istio, Kyverno, Velero, Prometheus, Submariner, Gatekeeper, and others. 

#### Adoption

##### Adopter 1 - Bloomberg / Finance

Large financial services company using Karmada for multi-cluster workload management across their infrastructure. Western company providing geographic and industry diversity in the adopter pool.

##### Adopter 2 - Trip.com / Online Travel

Major online travel platform that migrated from KubeFed to Karmada for cross-cluster auto-scaling and multi-cluster resource management in production.

##### Adopter 3 - TBD / Large-scale Internet

Xiaohongshu or Bilibili (large-scale Chinese internet platform) - interview pending.
