# Metal3.io Incubation Due Diligence

- Link to [Incubation application issue](https://github.com/cncf/toc/issues/1365)

<!-- This template provides the TOC with the outline for completing due diligence of a project to move levels. This universal template is designed to capture all criteria so the TOC may ensure prior level criteria do not regress. As part of completing the due diligence, the TOC member should update the template to convey the level the project applied for the criteria by bolding the level indicated where the criteria is relevant. -->

## Incubation Evaluation Summary for Metal3.io

### Criteria Evaluation

[Ricardo Rocha](https://github.com/rochaporto) conducted both due diligence and adopter interviews for Incubation. The project has completed the criteria that shows its maturity at the applied level.

The TOC would like to highlight some areas from the project review:

The following required incubation items were raised and implemented by the project during the review period:

Other items suggested for incubation were taken as issues in the project and have also been followed up:

### Adoption Evaluation

The adopter interviews showed project usage at a level compatible with CNCF incubation. Adopters integrate Metal3 to manage baremetal cluster deployments and the hardware lifecycle for a variety use cases, with the Telco area being particularly popular.

Adopters highlight the consistency across layers and the close integration with the ClusterAPI as one of its main strengths, as well as its reactive community and the solidity and maturity of Ironic as its core component. Adopters also mentioned the support for multiple different environments and ease of adoption of existing infrastructure as core capabilities. Adopters see the potential for further project growth through an effort of advertising more widely end users and scales of existing deployments.

Adopters see opportunities in allowing declaritive network configurations for environments without DHCP, a way to better separate baremetal operators from consumers with support for multiple baremetal host resources, and support for hardware management without administrator access. Adopters would also like to see support for multi-architecture and multi-tenancy, further abstractions of the underlying Ironic component better exposing internal status and error conditions, reducing the need for detailed debugging outside of the operator functionality. Failure handling is another area where extended focus could bring benefits.

### Final Assessment

The TOC has found the project to have satisfied the criteria for Incubation.

## Application Process Principles

### Suggested

N/A

### Required

- [x] **Give a presentation and engage with the domain specific TAG(s) to increase awareness**

The project [has recently presented](https://www.youtube.com/watch?v=YhGOd9jhWog&t=932s) at TAG-Runtime.

- [ ] **TAG provides insight/recommendation of the project in the context of the landscape**

- [x] **All project metadata and resources are [vendor-neutral](https://contribute.cncf.io/maintainers/community/vendor-neutrality/).**

No issues were found during due diligence, both code and documentation are vendor neutral.

- [x] **Review and acknowledgement of expectations for [Sandbox](sandbox.cncf.io) projects and requirements for moving forward through the CNCF Maturity levels.**		

Done during the project's apllication, onboarding completed [Sep 8, 2020](https://github.com/cncf/toc/pull/408).

- [x] **Due Diligence Review.**

The initial application was initially submitted July 05, 2024.

The project submitted initial DD information along with [the application](https://github.com/cncf/toc/issues/1365).

Project maintainers were responsive throughout the process.

The process satisfies the due diligence review criteria.

- [x] **Additional documentation as appropriate for project type, e.g.: installation documentation, end user documentation, reference implementation and/or code samples.**

Metal3's [documentation](https://book.metal3.io/introduction.html) is extensive providing a complete user guide, as well as an overview of the core concepts, individual components, installation and configuration. It also includes the required information for [development](https://book.metal3.io/developer_environment/tryit) and [contributions](https://metal3.io/contribute.html).

A minor improvement would be to consolidate the contributing links in the project's website, with [an issue] being opened for this purpose.

TODO
https://metal3.io/contribute.html
https://github.com/metal3-io/community/blob/main/CONTRIBUTING.md
https://github.com/metal3-io/baremetal-operator/blob/main/CONTRIBUTING.md

## Governance and Maintainers

### Suggested

- [x] **Clear and discoverable project governance documentation.**

OpenYurt's governance is documented under the project's github repo, under [GOVERNANCE.md](https://github.com/metal3-io/community/blob/main/GOVERNANCE.md). The information provided includes extensive details on the [different roles](https://github.com/metal3-io/community/blob/main/CONTRIBUTOR-ROLE.md) and [ladder](https://github.com/metal3-io/community/blob/main/CONTRIBUTOR-LADDER.md). 

- [x] **Governance has continuously been iterated upon by the project as a result of their experience applying it, with the governance history demonstrating evolution of maturity alongside the project's maturity evolution.**

The last update happened 2 years ago and looks complete, but a review with TAG-CS could be helpful before applying to the next maturity level.

- [x] **Governance is up to date with actual project activities, including any meetings, elections, leadership, or approval processes.**

Governance is up to date with actual practices.

- [x] **Governance clearly documents [vendor-neutral](https://contribute.cncf.io/maintainers/community/vendor-neutrality/) of project direction.**

The project documents its commitment to [vendor neutrality](https://github.com/metal3-io/community/blob/main/VENDOR_NEUTRALITY.md).

- [x] **Document how the project makes decisions on leadership, contribution acceptance, requests to the CNCF, and changes to governance or project goals.**

The project has documentation regarding its [contributor ladder](https://github.com/metal3-io/community/blob/main/CONTRIBUTOR-LADDER.md), as well as how [changes to the policy](https://github.com/metal3-io/community/blob/main/maintainers/README.md#changing-the-policy) can be done - requiring two thirds of existing maintainers.

- [x] **Document how role, function-based members, or sub-teams are assigned, onboarded, and removed for specific teams (example: Security Response Committee).**

The different community roles are [well documented](https://github.com/metal3-io/community/blob/main/CONTRIBUTOR-ROLE.md) with additional information on onboarding and offboarding.

- [x] **Document a complete maintainer lifecycle process (including roles, onboarding, offboarding, and emeritus status).**

Roles are [well documented](https://github.com/metal3-io/community/blob/main/maintainers/README.md) including information on how to deal with inactive members.

- [x] **Demonstrate usage of the maintainer lifecycle with outcomes, either through the addition or replacement of maintainers as project events have required.**

The current list of maintainers is [well maintained](https://github.com/metal3-io/community/blob/main/OWNERS) with a [list of individuals](https://github.com/metal3-io/community/blob/main/OWNERS_ALIASES) but no emeritus members are currently listed.

- [ ] **If the project has subprojects: subproject leadership, contribution, maturity status documented, including add/remove process.**

N/A

### Required

- [ ] **Document complete list of current maintainers, including names, contact information, domain of responsibility, and affiliation.**

The full list of maintainers is present in a [MAINTAINERS.md](https://github.com/metal3-io/community/blob/main/OWNERS_ALIASES) file but does not currently list affiliation.

maintainers: 4 redhat, 3 ericsson

TODO

- [x] **A number of active maintainers which is appropriate to the size and scope of the project.**

As of March 2025, the list of maintainers and diversity (7 for the core operator project, from 2 organizations) is appropriate to this maturity level.

- [ ] **Code and Doc ownership in Github and elsewhere matches documented governance roles.**

- [x] **Document agreement that project will adopt CNCF Code of Conduct.**

The code of conduct is [linked](https://github.com/metal3-io/community/blob/main/CODE_OF_CONDUCT.md) and is listed as a requirement from the [community page](https://github.com/metal3-io/community?tab=readme-ov-file).

TODO: better link from https://metal3.io/contribute.html (this page needs improvement and to link to the github page in https://github.com/metal3-io/community )

- [x] **CNCF Code of Conduct is cross-linked from other governance documents.**

A specific [code of conduct](https://github.com/metal3-io/community/blob/main/CODE_OF_CONDUCT.md) links to the [CNCF code of conduct](https://github.com/cncf/foundation/blob/main/code-of-conduct.md).


- [x] **All subprojects, if any, are listed.**

  N/A

## Contributors and Community

### Suggested

- [ ] **Contributor ladder with multiple roles for contributors.**

### Required

- [ ] **Clearly defined and discoverable process to submit issues or changes.**


- [ ] **Project must have, and document, at least one public communications channel for users and/or contributors.**


- [ ] **List and document all project communication channels, including subprojects (mail list/slack/etc.).  List any non-public communications channels and what their special purpose is.**


- [ ] **Up-to-date public meeting schedulers and/or integration with CNCF calendar.**


- [ ] **Documentation of how to contribute, with increasing detail as the project matures.**


- [ ] **Demonstrate contributor activity and recruitment.**


## Engineering Principles

### Suggested

- [ ] **Roadmap change process is documented.**


- [ ] **History of regular, quality releases.**


### Required 

- [ ] **Document project goals and objectives that illustrate the project’s differentiation in the Cloud Native landscape as well as outlines how this project fulfills an outstanding need and/or solves a problem differently.**


- [ ] **Document what the project does, and why it does it - including viable cloud native use cases.**


- [ ] **Document and maintain a public roadmap or other forward looking planning document or tracking mechanism.**


- [ ] **Document overview of project architecture and software design that demonstrates viable cloud native use cases, as part of the project's documentation.**


- [ ] **Document the project's release process.**


## Security

Note: this section may be augmented by a joint-assessment performed by TAG Security.

### Suggested

N/A

### Required

- [ ] **Clearly defined and discoverable process to report security issues.**


- [ ] **Enforcing Access Control Rules to secure the code base against attacks (Example: two factor authentication enforcement, and/or use of ACL tools.)**


- [ ] **Document assignment of security response roles and how reports are handled.**


- [ ] **Document Security Self-Assessment.**

- [ ] **Achieve the Open Source Security Foundation (OpenSSF) Best Practices passing badge.**


## Ecosystem

### Suggested

N/A

### Required

- [ ] **Publicly documented list of adopters, which may indicate their adoption level (dev/trialing, prod, etc.)**


- [ ] **Used in appropriate capacity by at least 3 independent + indirect/direct adopters, (these are not required to be in the publicly documented list of adopters)**


- [ ] **TOC verification of adopters.**


- [ ] **Clearly documented integrations and/or compatibility with other CNCF projects as well as non-CNCF projects.**



#### Adoption

##### Ericsson

Kaisa Kettunen, head of cloud container distribution inside Ericsson, Ganesh Vasudevan.

###### Usage

Ericsson started using Metal3 around 2019-20 when considering baremetal deployments with the ClusterAPI - previous systems were purely VM based. Usage has been increasing steadily since then.

Ericsson's main motivation was to offer baremetal provisioning of Kubernetes clusters at scale, hardening its security layers and performance related items, in particular cluster management operations. Ericsson is happy with the current offering of Metal3 in this area.

At the time Ericsson considered adopting Metal3 there were not many alternatives available, but Ericsson did consider alternatives that could serve the expectations of Telco deployments lifecycle. In particular, Ericsson considered the ability to do so at scale. Ericsson still follows the landscape in this area, but considers Metal3 to be the most robust option.

###### Perception and Feeling

Ericsson started adoption taking as a limitation a single cluster configuration, with no clear idea if the project would evolve to support all possible configurations, especially when considering integration with commercial deployments. The community took this over and these requirements are now covered thanks to multiple improvements.

Ericsson considers the releases and the release cycle to be well announced and documented. This is considered to be of particular importance as there are strong dependencies with the releases of Kubernetes and of the ClusterAPI. The process is more streamlined than it was years ago.

Ericsson relies mostly on slack discussions, GitHub issues, discussions and patches. The experience has shown the community to be very responsive to requests.

Ericsson remains engaged in ensuring the community continues to drive the project forward. If needed it could consider getting more active in upstream work, but until now this has not been necessary.

###### Strenghts and Improvements

Ericsson highlights the liveness of the community as one of its main strenghts, as well as being a battle proven solution. Ericsson sees here potential to better advertise its potential to end users and increasing the visibility on project growth and the scale of deployments in recent years across multiple organizations.

Ericsson stresses that stability has to remain a key focus. In particular, the stability and reliability of the CI is of particular importance.

##### Telekom DE

Jakob Shretennbrunner, Max Rink, Vuk Gojnic

###### Usage

Telekom DE started using Metal3 in mid-2020, with the first production setup being deployed one year later. Part of the required work in this period was around custom tooling to interact with the project.

At the time of adoption Telekom DE did not see any viable alternative, although both Tinkerbell and Talos were considered but seen as significantly less mature - building an in-house solution was seen as the only other option. The target was to build a L3 only infrastructure, provide integration with Redfish and integration with the ClusterAPI. Telekom DE did look into EKS anywhere (supporters of Tinkerbell) but the project lacks the advanced networking features required and available in Metal3.

Telekom DE currently has 300 clusters in total, out of which 200 are based on the ClusterAPI/Metal3 and cover testing, staging and production. In total these clusters have around 2300 nodes. The usage includes the production 5G deployments for Telekom DE in Germany.

Telekom DE is confortable with keeping releases up to date with the upstream releases, seeing very little risk with upgrades and even rollbacks when needed. Internally there are monthly releases for patches, slower for minor releases which often sync with updates to the ClusterAPI.

Telekom DE has an ongoing initiative to harmonize the available Kubernetes platforms across all EU countries, which will not be based on Metal3. Metal3 will stay in use as the "legacy" platform, meaning it will have to be maintained for at least 3 more years.

Reasons stated for moving out include: the complexity of the stack, in particular Ironic which is very good to support heterogeneous environments but not justified when the dependency is mostly on Redfish; operating Ironic is a non-trivial task, even if the operator abstracts most of it but experience shows the need to still debug directly in Ironic; the need for an external database which adds an extra dependency on an external service. An internal effort has been ongoing to have a custom cloud provider implementation, based on Redfish/Virtualmedia only, making things homogeneous and enabling a simplification of the stack. Telekom DE adds that as of today Metal3 is still their most reliable solution.

###### Perception and Feeling

Telekom DE did not require significant interaction with upstream to get things up and running quickly. They found the development environment to be tricky to setup when requiring custom tools or changes. Documentation was good enough, but not at the level of the ClusterAPI docs, although it has significantly improved over the years.

Telekom DE interacts with the project and community mostly on slack, and have been present occasionaly during the project office hours. GitHub is used for interactions around the IPAM component, and they see the reaction being very good for any feature that is seen as valuable by the community. On the down side, examples where traction is not good in the community (example for cross namespace referencing of nodes) do not get strong follow up.

###### Strenghts and Improvements

Telekom DE sees the main strengths of the project being the solidity and maturity of Ironic, the support for multiple different environments and the ease of adoption for existing baremetal infrastructure.

Telekom DE sees the complexity required to achieve this as one of the weaknesses. Some welcome improvements would be in better exposing internal status and error conditions, which did improve but are still not at the level of what is expected by the ClusterAPI - meaning accessing Ironic directly is often still required. Failure handling of physical hardware also regularly requires manual intervention, which is especially an issue for larger infrastructures.

##### Orange

Aurelien Sollaud, Thomas Morin

###### Usage

Orange started looking at the project in 2020 for research purposes, with 2021 bringing a trial of a 5G deployment relying on Metal3. They launched in 2022 an internal product based on this platform, with a large number of lab and development environments. 2024 saw the first pre-production environment, and they expected the first production setup in 2025.

Orange chose Metal3 as it is an open source tool and provides a mature integration with the ClusterAPI. The maturity of Ironic and its capabilities to hide the diversity in the underlying hardware were also a key feature, as well as being feature complete with regards to the lifecycle management of the hardware.

When selecting a project in 2022 Orange already had significant experience with Metal3 so they did not consider any alternative.

Orange relies on Metal3 for its internal product validation center, which requires involvement of multiple operators for testing and counts 5 platforms relying on baremetal clusters. In total there are 16 platforms across multiple regions, running customer production workloads. The internal GitLab CI is also running on clusters managed by Metal3.

Orange relies on SUSE packages and helm charts. Currently they stay less than 6 months behind the upstream releases and they follow closely the upstream work. The main branch of their internal tools relies on the latest upstream release.

###### Perception and Feeling

Orange's highlights that managing baremetal deployments is complex and messy in itself, and from previous experiences meant they expected challenges during early adoption. They found the development environment not to be particularly easy to use, so they ended up creating their own based on Kind. Other initial challenges included having a declaritive way to define the environments and the efficiency and reliability of the resource cleanup process (where they contributed multiple fixes). Both were solved in the meantime.

Orange finds the documentation appropriate even if not perfect. In some cases the documentation is available directly in the component repositories or even in the code. Internally this is not a significant issue since they have experience interacting with open source projects and can adapt.

Orange engages with the project and community via slack discussions, interactions at Kubecon and participating in the project's monthly calls. PRs for bug fixes were very well followed by the community and maintainers.

Orange has a heavy reliance on Metal3 and has built multiple integrations on top of it, meaning there would be a high cost to switch projects. There is a strong interest to keep Metal3 healthy and they see the same in the general community and the partners they work with. As an example, Orange mentions OpenBAO which they have started contributing to recently but they don't see any similar issue happening with Metal3 in the near future. Orange also highlights there is no similar project with the same level of maturity available today.

###### Strenghts and Improvements

Orange sees a big benefit from virtualizing the vendor network functions, which were previously done in dedicated components.

Orange highlights improvements possible in the documentation, where in some cases access to the component repositories or even the code is required. They also see navigability as an area to improve. In addition to documentation, Orange would like to see improvements in the area of network configuration, with the ability to deploy nodes without DHCP and a consistent way to declare the network configuration - something the community is aware and already focusing on. The baremetal allocation workflow could also be improved, better distinguishing the baremetal operator from the consumer - something not possible today as there is only one baremetal host resource. An existing proposal to improve this area already exists.

##### RedHat

Ramon Acedo Rodriguez, PM in area of infrastructure (previous OpenStack, focus on baremetal) working with OpenShift cloud installers and baremetal.

###### Usage

RedHat started using Metal3 in 2020, focusing on managing and deployment baremetal OpenShift in an opinionated way. RedHat quickly move half of the installers to this new method shortly after. Production deployments in 2021 started with small clusters (few dozens of nodes) but grew to 250 node clusters the same year and 500 the year after. Current usage includes adoption for internal CI, with validation being done with deployments of up to 2000 nodes. Achieving this size for clusters required several improvements in networking (OVN and other components).

RedHat did not consider any alternative in depth, only Tinkerbell was briefly looked at.

RedHat usually releases every 4 months, staying close to the latest Metal3 release and aligning with the Kubernetes releases.

RedHat's main motivation for adoption of Metal3 included:
* Previous experience with the Ironic project on OpenStack, with the required internal expertise already available
* The ease of deployment and scale of baremetal deployments in cloud environments, in particular the consistency with other platforms via the integration with the ClusterAPI and MachineAPI
* The consistency offered to manage heterogeneous hardware, especially with Redfish

RedHat plans to expand usage of Metal3 to manage nodes with different operating systems. Support exists in Ironic but is not yet integrated internally.

###### Perception and Feeling

RedHat reported that in the early years of usage (2020-22) the main challenges were from issues managing baremetal nodes due to infrastructure requirements - around IP access, proper configuration of the BMCs, network gateways, VPNs and others. Workarounds were required for misbehaviors against the expected Redfish specification, which made this task time consuming at start - opening and following issues upstream. These issues were also seen by other adopters and were smoothed out with time.

RedHat found the documentation to be lacking in 2020-21 but has seen it was significantly improved and is now in a good state. In particular, RedHat highlighted the focus on having a good entrypoint for new end users and adopters.

RedHat's engagement with the community and maintainers has been a good experience, with timely fixes even for complex requests.

###### Strenghts and Improvements

RedHat sees the core strengths of the project being the consistency across the multiple layers, making it easy to deploy and distribute Metal3 in any Kubernetes distribution. Another strong point is in the ease of use for simpler use cases, which covers the integration with other components in the ecosystem and the onboarding of specific hardware deployments.

RedHat would like to see the hardware management no longer requiring administrator access, which would be particular useful for deployments in public cloud providers. In addition it would be good for the project to add support for multi-tenancy and better self serving capabilities.

##### SUSE

Tim Irnich, production manager/owner for the internal Telco baremetal offering. Steven Hardy, engineering director at the edge team for Tecol products (previously in the Metal3 team).

###### Usage

SUSE start using Metal3 in April 2022 in a lab environment, performing due diligence on the project during this period. The main motivation for choosing the project was the integration with the ClusterAPI for baremetal deployments.

SUSE considered Tinkerbell at that time, but chose Metal3 following its own internal due diligence. As the initial results from Metal3 usage were positive, including feedback from early consumers, other options were not followed through.

SUSE productizes Metal3 into its own offering, and deploys the project in multiple environments. The first version of its internal offering was in April 2024 with two releases after that. The size of the deployments goes from very small clusters with 3 nodes or less to 10s of nodes. In SUSE's customer base clusters with 100s of nodes are not common, and they see a trend in Telco to prefer multiple smaller clusters with a management layer on top.

SUSE releases internally every 4 months, including an update of both Metal3 and the ClusterAPI releases. The same is valid for OpenStack dependencies. SUSE finds the upstream stable branches to be reliable and safe to consume, and the current project cadence fits their use cases.

SUSE is mainly deploying Metal3 for Telco use cases but is considering extending its usage for other types of customers and expanding the adoption of the project.

###### Perception and Feeling

SUSE sees the addition of stable branches as a major improvement from the time it initially adopted the project. The Metal3 book has also improved significantly in the last year.

SUSE uses slack for design discussions, as well as the upstream documentation repository. GitHub issues have shown to be effective and get fast reaction and engagement from community and maintainers. In some cases, SUSE engages directly with other end users such as Ericsson that have similarly strategic interests in the project, including discussions about potential contributions.

SUSE sees a healthy community around the project and does not see any sustainability issue in the medium term, especially since it became a strategic component for multiple organizations. SUSE also highlights the problem of management of baremetal will not go away, so even in case of sustainability issues the community would gather and move together.

###### Strenghts and Improvements

SUSE is seeing significant growth where Metal3 is being used, which is an indication the project is doing its job well. Part of it also comes from the success of the ClusterAPI. Maturity (including that of Ironic) and overall adoption are the two main strengths of the project.

SUSE is considering contributing for some developments it sees as benefitial to the project. The two main features being looked at include: improved IPAM management, which is already being picked up by the community; multi-architecture support, also recognized in the community but with no traction yet.

According to SUSE, the project should also consider consolidate the different deployment options - current an operator and kustomize - as this is complex component to manage. In addition to that, given the close link to the ClusterAPI any significant changes to its API need to stay very closely followed.
