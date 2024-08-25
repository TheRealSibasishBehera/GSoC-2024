# Google Summer of Code 2024: Work Product Submission

<p align="center">
<img src="https://github.com/kubevirt/community/raw/main/logo/KubeVirt_icon.png" width="100">
</p>

## Table of Contents

- [Student Developer Info](#student-developer-info)
- [Project Overview](#project-overview)
- [Communication and Work Management](#communication-and-work-management)
- [Primary Features/Components I Worked On](#primary-featurescomponents-i-worked-on)
- [Challenges Encountered](#challenges-encountered)
- [Future Scope of the Project](#future-scope-of-the-project)
- [Key Learnings](#key-learnings)
- [Acknowledgments](#acknowledgments)
- [Important Links](#important-links)

## Student Developer Info

**Name**: Sibasish Behera ([@TheRealSibasishBehera](https://github.com/TheRealSibasishBehera))  
**Organization**: [KubeVirt Community](https://www.kubevirt.io/)  
**Project**: [Persistent Device Claims for KubeVirt](https://github.com/kubevirt/community/issues/254)

## Project Overview

The project focused on implementing Persistent Device Claims (PDC) within KubeVirt, enabling Kubernetes users to request and utilize specific hardware devices, such as GPUs or NICs, across KubeVirt virtual machines (VMs). This functionality is a significant milestone for integrating Dynamic Resource Allocation (DRA) into KubeVirt, a new alpha API available since Kubernetes 1.26+. DRA provides a more flexible method for requesting resources compared to the traditional device plugin framework.

This project involved creating a proof-of-concept (POC) DRA-based driver for PCI devices. The POC included a fork of KubeVirt where DRA is enabled, allowing users to declare and use ResourceClaims within their VM manifests.

### Components of Persistent Device Claims

- **DRA-PCI Driver**:

  - The [DRA-PCI driver](https://github.com/kubevirt/dra-pci-driver) was developed as part of this project to handle device requests, allocation, and management of PCI devices using DRA.
  - This driver ensures that specific hardware devices can be claimed by KubeVirt VMs while maintaining compatibility with the Kubernetes Dynamic Resource Allocation (DRA) API.
  - The driver was tested using [kubevirtci](https://github.com/kubevirt/kubevirtci) and emulated NVMe devices.
  - The driver consists of two components: the `kubelet-plugin`, which manages the state of devices at the node level, and the `dra-controller`, which communicates with the Kubernetes API to make scheduling decisions.

- **KubeVirt Integration**:
  - The integration with KubeVirt, as demonstrated in [KubeVirt PR #12533](https://github.com/kubevirt/kubevirt/pull/12533), allows VMs to request and attach specific hardware devices via ResourceClaims using the DRA-PCI driver.
  - This integration also involved designing a feature gate `DynamicResourceAllocation`, as the DRA API and DRA-PCI driver are still evolving.

## Communication and Work Management

- The project was managed and hosted under the KubeVirt GitHub repository.
- Weekly meetings were held with mentors from the KubeVirt team to discuss progress, address blockers, and review code.
- Communication was facilitated through Slack and video calls, providing a platform for real-time collaboration and feedback.
- Code reviews were conducted on GitHub, with feedback from multiple maintainers and contributors.

## Challenges Encountered

- **Translation of Device Data in Libvirt XML**:
  - One of the challenges was translating the device data into the correct Libvirt XML format required by KubeVirt. This translation required careful consideration of the device specifications and ensuring that the XML accurately represented the requested resources.

- **Navigating Kubernetes DRA Implementation**:
  - Understanding and integrating the Dynamic Resource Allocation (DRA) implementation within Kubernetes presented challenges, particularly with respect to aligning it with KubeVirt’s existing infrastructure and ensuring smooth operation.

## Future Scope of the Project

- **Expanding Device Support**:
  - Expanding the range of supported hardware devices to include mediated devices, USB devices, and others.

- **Enhancing Security and Access Control**:
  - Implementing improved communication strategies and access control mechanisms to enhance security in the device claim and allocation process.

## Key Learnings

- **Device Management in Kubernetes**:
  - Gained in-depth knowledge of Kubernetes and its device management mechanisms, including the DRA API and device plugin mechanisms.

- **KubeVirt Architecture**:
  - Developed a comprehensive understanding of KubeVirt’s architecture, virtualization, and distributed systems.

- **Collaboration in Open Source**:
  - Learned the importance of effective communication and collaboration in open-source projects, particularly within a distributed team.

## Acknowledgments

I would like to express my heartfelt gratitude to:

- My mentors, Alice Frosi ([@alicefr](https://github.com/alicefr)) and Victor Toso ([@victortoso](https://github.com/victortoso)), for their invaluable time, detailed reviews, and guidance.
- The entire KubeVirt Community for their warm support and assistance.

## Important Links

- [GitHub Repository](https://github.com/kubevirt/kubevirt)
- [DRA-PCI Driver Repository](https://github.com/kubevirt/dra-pci-driver)
- [KubeVirt PR #12533](https://github.com/kubevirt/kubevirt/pull/12533)

Documentation can be found in the respective repositories.
