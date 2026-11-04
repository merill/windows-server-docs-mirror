---
layout: Conceptual
title: What is Windows Admin Center Virtualization Mode (preview)? | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/virtualization-mode-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn what Windows Admin Center Virtualization Mode is. See how it differs from administration mode, the scale it supports, setup needs, upkeep, and built-in tools for large environments.
author: robinharwood
ms.author: roharwoo
ms.topic: overview
ms.date: 2026-05-01T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: c8431ed0-cfd9-29f2-38b5-89155742a24f
document_version_independent_id: c8431ed0-cfd9-29f2-38b5-89155742a24f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/virtualization-mode-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/virtualization-mode-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/virtualization-mode-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 863968d3-ad4d-8252-aa18-dbc653c34149
---

# What is Windows Admin Center Virtualization Mode (preview)? | Microsoft Learn

Important

Windows Admin Center Virtualization Mode is currently in PREVIEW. This information relates to a prerelease product that may be substantially modified before it's released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

To file issues, questions, and feedback not covered in this documentation, visit [the Windows Admin Center feedback platform](https://github.com/MicrosoftDocs/Windows-Admin-Center-Ideas-and-Feedback).

Windows Admin Center Virtualization Mode is a purpose-built management experience for virtualization infrastructure. IT professionals can use it to centrally administer Hyper-V hosts, clusters, storage, and networking at scale.

Unlike administration mode, which focuses on general system management, Virtualization Mode focuses on fabric management. It supports parallel operations and contextual views for compute, storage, and network resources. This mode is optimized for large-scale, cluster-based environments and integrates lifecycle management, global search, and role-based access control.

To get an overview of Windows Admin Center Virtualization Mode, watch the following video. 

Virtualization Mode offers the following key capabilities:

- Search across navigation objects with contextual filtering.
- Support for SAN, NAS, hyperconverged, and scale-out file server architectures.
- VM templates for standardized provisioning. For more information about creating and deploying VM templates, see [Use VM templates in Virtualization Mode](use-virtualization-mode-vm-templates).
- Software-defined storage and networking (not available at this time).

## Operational modes

Windows Admin Center has two independent modes:

- **Administration mode**: The Windows Admin Center experience you're already familiar with. Administration mode focuses on general server administration with tools and features that help you perform general server administration tasks.
- **Virtualization mode**: Manage the infrastructure required to host virtual machines. The tools and experiences are more focused on these specific goals.

For example, in administration mode, you have tools like Device Manager and Registry Editor, while virtualization mode features SDN tools, among other things specific to virtualization.

The following table summarizes the key differences between administration mode and virtualization mode:

| Area | Administration Mode | Virtualization Mode |
| --- | --- | --- |
| Used for | General system administration (Device Manager, Remote Desktop, Registry, Roles & Features). | Virtualization fabric management (Hyper-V hosts/clusters, VM lifecycle, Storage Spaces Direct, Network ATC, SDN, volumes). |
| Scenario Focus | Single-server and cluster management tasks and troubleshooting. | Large-scale, distributed cluster and resource lifecycle management. |
| Connection | Stateless, per-session direct connections (WinRM/PowerShell) to individual servers. | Stateful with database and agents enabling parallel, persistent cluster connections. |
| View | Component-centric (processes, services, registry, events, features). | Resource-centric (compute, storage, networking, VMs) with contextual navigation and search. |
| Scale | Typically 1–50 hosts for general server management. | Up to 1,000 hosts and 25,000 VMs per instance. |
| Operations | Remote PowerShell at runtime | Parallel operations using a local agent. |

You must install Windows Admin Center Administration Mode and Windows Admin Center Virtualization mode on separate systems.

### Tools and features

Virtualization Mode includes the following tools and features:

| Host profile | Tools and features |
| --- | --- |
| Compute (hosts) | - Overview dashboard- Settings- Updates- Virtual Machines- Servers- Volumes- Hyper-V Replica- GPU-P |
| Compute (servers) | - Dashboard- Settings- Events- Firewall- Updates- Virtual Machines- Networks- Storage |
| Storage | The Storage view displays onboarded storage devices and their linked compute systems. |
| Networking | The Network view lets you browse, create, edit, and delete network intent templates. The networking host profile isn't available at this time. |

To learn about the tools available to Administration Mode for non-virtualization scenarios, see [Manage Servers with Windows Admin Center](use/manage-servers).

## How it works

Virtualization Mode deploys as an appliance on physical or virtual machines. For more information about the installation requirements, see [Install Windows Admin Center Virtualization Mode](install-virtualization-mode).

This mode uses a client-server architecture with a web-based gateway and local agents on managed Hyper-V hosts. The gateway handles user authentication, request routing, and maintains a stateful database, while agents perform operations on hosts. TLS secures communication between the gateway and agents.

The following diagram illustrates the architecture of Windows Admin Center Virtualization Mode:

[![Diagram that shows a client browser connecting to a Virtualization Mode gateway, which orchestrates three Hyper-V hosts in parallel.](media/virtualization-mode-overview/architecture.png)](media/virtualization-mode-overview/architecture.png#lightbox)

The architecture efficiently orchestrates large-scale virtualization environments, so it doesn't affect the availability or performance of the managed Hyper-V hosts and clusters during normal operations.

Virtualization Mode introduces the concepts of resource groups and host profiles to help organize and manage virtualization resources at scale.

### Resource groups

A resource group is a logical container in Virtualization Mode that you use to organize virtualization resources. Resource groups don't nest. Each host belongs to exactly one resource group for organization and profile-based management.

Use resource groups to:

- Segregate hosts by environment (production, lab, staging).
- Simplify navigation by scoping search and operations.

### Host profiles

Host profiles indicate the service a system provides to virtual machines within Virtualization Mode. A profile classifies each added system by its primary role so Virtualization Mode can present it in the correct navigation view and role-aware workflows.

Profile types:

- Compute: Hosts provide compute virtualization.
- Storage: Storage systems for virtual machines (SAN, NAS, or hyperconverged using Storage Spaces Direct). The Storage view displays onboarded storage devices linked to your compute systems. The storage host profile isn't available at this time.
- Networking: Software Defined Networking (SDN) services for virtual machines. The Network view lets you manage network intent templates. The networking host profile isn't available at this time.

### Network intent templates

Windows Admin Center Virtualization Mode introduces a concept called a *Network intent template*, which is an abstracted, predefined intent that you didn't yet apply to a network adapter or associate with a cluster or standalone host. A network intent template serves as a blueprint that you can use to create intents after you specify which NICs the template should apply to.

Network intent templates persist across sessions. After you create a template in the Add Resource workflow, it's saved and available for reuse the next time you onboard new hosts or clusters. You can select a saved template from the dropdown without recreating it. For more information about configuring network intent templates during onboarding, see [Add resources in Virtualization Mode](add-virtualization-mode-resources#add-resources).

You can also manage network intent templates outside of the Add Resource workflow. Select the **Network** view in the top navigation bar to browse, create, edit, and delete your network intent templates.