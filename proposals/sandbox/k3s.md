# K3s CNCF Sandbox Project Proposal

Authors: 
- Darren Shepherd, Rancher Labs, CTO
- Craig Jellick, Rancher Labs, Directory of Engineering


## Background

Link to Presentation - Coming soon!

[**Link to GitHub project**](https://github.com/rancher/k3s)

### Project Goal

k3s's goal is to provide a CNCF certified, production-grade Kubernetes distribution that is lightweight and easy to configure and operate. In doing so, k3s seeks to promote and improve the adoption of Kubernetes for the following usecases:
- Edge
- IoT
- CI Pipelines
- Development-to-production consistent environments
- ARM devices
- Embedding k8s in software appliances

### Current Status
k3s reached GA quality in November of 2019. It maintains a release cadence consistent with upstream Kubernetes, seeking to release within one month of upstream for the three most recent Kubernetes minor releases. As of this writing, the most recent releases are as follows:
| Upstream Kubernetes | k3s |
| ------------- | ------------- |
| [v1.18.2](https://github.com/kubernetes/kubernetes/releases/tag/v1.18.2)  | [v1.18.2+k3s1](https://github.com/rancher/k3s/releases/tag/v1.18.2%2Bk3s1)  |
| [v1.17.5](https://github.com/kubernetes/kubernetes/releases/tag/v1.17.5)  | [v1.17.5+k3s1](https://github.com/rancher/k3s/releases/tag/v1.17.5%2Bk3s1)  |
|  [v1.16.9](https://github.com/kubernetes/kubernetes/releases/tag/v1.16.9) | [v1.16.9+k3s1](https://github.com/rancher/k3s/releases/tag/v1.16.9%2Bk3s1)  |

The project has a vibrant community. It has over 12,000 stars on GitHub and 89 code contibutors. It's most recent stable release has over [60,000 downloads across three different architectures](https://api.github.com/repos/rancher/k3s/releases/24836622).

### Future Plans
k3s's roadmap includes:
- Improving stability and support across operating systems and architectures
- Enhancing security through SELinux support and CIS compliance
- Developing HA solutions apprporiate for small edge clusters where even three nodes is cost prohibitive
- Improving support Kubernetes cloud providers
- Improved support for database backends, including embedded etcd

while continuing to maintain release cadence and conformance with upstream Kubernetes.

## Project Scope
### Clear project definition
As previously state, k3s's is a CNCF certified, production-grade, lightweight Kubernetes distribution. It is packaged with sane defaults to achieve a fully functional cluster with minimal dependencies.

To achieve this, k3s has the follwoing scope:
1. Packaged as a single binary
1. Shipped with Lightweight storage backend based on sqlite3 as the default storage mechanism. etcd3, MySQL, Postgres are also supported
1. Wrapped in simple launcher that handles a lot of the complexity of TLS and options
1. Secure by default with reasonable defaults for lightweight environments
1. Brings its own dependencies such that just a sane kernel and cgroup mounts are needed. k3s packages the following required dependencies:
    - containerd
    - Flannel
    - CoreDNS
    - CNI
    - Host utilities (iptables, socat, etc)
    - Ingress controller (traefik)
    - Embedded service loadbalancer
    -   Embedded network policy controller
  
### Value-add to the CNCF ecosystem
k3s is bringing Kubernetes to environments and use cases that are not easily accessible to upstream Kubernets, such as edge and IoT. In doing so, it is promoting the overall growth and adoption of Kubernetes. When coupled with Kubernetes's explosive growth in the cloud and the datacenter, k3s is helping Kubeernetes to become the universal compute platform.

### Alignment with other CNCF projects
***Does the project align and actively collaborate with other CNCF projects?***

k3s is incredibly well aligned with other CNCF projects. It levarages existing CNCF projects such as Kubernetes, CNI, CRI, CSI, containerd, CoreDNS, and Helm. In dooing so, its maintainers contribute to these projects by opening issues, submitting PRs, promoting them on social media, and engaging in technical discussions.

***Does the project require any specific versions of projects (or APIs) to interoperate? (e.g. K8s API, CSI, CNI, CRI)?***

k3s generally seeks to support the latest stable versions of the CNCF projects that it levarages. For projects that are themselves closely tied to Kubernetes, such as CNI, CRI, and CSI, k3s supports the same versions that upstream Kubernetes supports.

***Does the project augment or benefit other CNCF projects?***

As stated, k3s benefits Kubernetes by bringing it to environments that are not easily accessible to upstream Kubernetes. In focusing on secondary use cases and environemnts, k3s also illuminates problems or bugs in the other CNCF projects it leverages. Here are a few examples: [kubernetes#89554](https://github.com/kubernetes/kubernetes/issues/89554), [cri-tools#585](https://github.com/kubernetes-sigs/cri-tools/issues/585), [kubernetes#88376](https://github.com/kubernetes/kubernetes/issues/88376), and [containerd#2991](https://github.com/containerd/containerd/issues/2991).

### Anticipated use cases
With hundreds of thousands of downloads and a large and growing community of users, k3s's usecases are well proven. These usecases have already been stated: edge, IoT, ARM devices, and software appliacnes. One major usecase that has not yet been addressed is that of fleet managment. This is tied directly to the "edge" and IoT use cases, but is worth calling out explicitly. k3s's ease of deployment, operations, and upgrades makes the managing thousands or even millions of small Kubernetes clusters a possibility.

Alignment with SIG Reference Model
Does the project align with the SIG CNCF reference model and which capabilities does it require/provide at each level of the reference model.

### High level architecture
Describe the overall architecture of the project. Feel free to add diagrams.

## Formal Requirements
Document that the project fulfills the requirements as documented in the CNCF graduation criteria for sandbox

Are there any anticipated issues with any of the criteria ?

Has the TOC been approached for sponsorship? If yes, which TOC members have agreed to sponsor the project?

## CNCF IP Policy
Becoming a sandbox project requires adoption of the CNCF IP Policy: https://github.com/cncf/foundation/blob/master/charter.md#11-ip-policy

Note: there is a grace period after becoming a sandbox period to enable projects to adopt the policy, however, some prep is required to ensure there are no major blockers.

Has the IP policy been reviewed?

List the repos for the project and their current license

List any dependent repos (upstream/downstream) that are required to build the project (including but not limited to libraries, commercial tools, plugins)

What actions are required to be compliant with the IP policy?

## Other Considerations
### _Please note, these are not gating criteria but rather to:_
- Collect a standard set of information for each project
- Provides a point in time capture of the state of the project which makes it easier to track progress at future reviews and / or promotion
- Help projects to prepare for SIG and TOC presentation
- Allow the SIG to review the project and perform due diligence for incubation
- Provide the TOC with the information required to accept sponsorship of a project and/or votes
- Identify and rectify any significant issues / blockers prior to presenting to the TOC and acceptance as a CNCF project

### Cloud Native
Does the project meet the definition of Cloud Native? The CNCF charter states:
```
“Cloud native technologies empower organizations to build and run scalable applications in modern, dynamic environments such as public, private, and hybrid clouds. Containers, service meshes, microservices, immutable infrastructure, and declarative APIs exemplify this approach.


“These techniques enable loosely coupled systems that are resilient, manageable, and observable. Combined with robust automation, they allow engineers to make high-impact changes frequently and predictably with minimal toil.”
```

### Project and Code Quality
Are there any metrics around code quality? Are there good examples of code reviews? Are there enforced coding standards?

What are the performance goals and results? What performance tradeoffs have been made? What is the resource cost?

What is the CI/CD system? Are there code coverage metrics? What types of tests exist?

Is there documentation?

How is it deployed?

How is it orchestrated?

How will the project benefit from acceptance into the CNCF?

Has a security assessment by the security SIG been done? If not, what is the status/progress of the assessment?
