---
layout: Conceptual
title: 'Windows Admin Center: Choose an Installation | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/plan/installation-options
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Compare Windows Admin Center Administration Mode and Virtualization Mode, and choose an Administration Mode installation topology.
ms.topic: concept-article
author: davannaw-msft
ms.author: dawhite
ms.date: 2025-07-14T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 84be3ac8-1a9e-bb18-1070-ad161642890f
document_version_independent_id: e5552651-0676-fce6-b0b5-36be6df9ae64
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/plan/installation-options.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/plan/installation-options
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/plan/installation-options.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: ba28f88a-b085-32d8-147f-53dd8c6eb894
---

# Windows Admin Center: Choose an Installation | Microsoft Learn

Windows Admin Center provides two management experiences that you install independently: Administration Mode for general server and cluster management, and Virtualization Mode for virtualization fabric management at scale. This article helps you choose an experience and, if you choose Administration Mode, select an installation topology.

The installation topologies and supported operating systems in this article apply to Administration Mode. To install Windows Admin Center on a virtual machine (VM) in Azure, see [Deploy Windows Admin Center in Azure](../azure/deploy-wac-in-azure).

## Choose a management experience

Choose the experience that matches the scope and type of resources you need to manage.

| Experience | Choose this experience when | Installation model |
| --- | --- | --- |
| **Administration Mode** | You need general administration and troubleshooting tools for individual servers and clusters. | Install on a local client, gateway server, managed server, or failover cluster by using the standard Windows Admin Center installer. |
| **Virtualization Mode** | You need centralized, large-scale management of Hyper-V hosts, clusters, virtual machines, storage, and networking. | Install as a dedicated appliance on a physical or virtual Windows Server machine by using the separate Virtualization Mode installer. |

Important

You can't install Administration Mode and Virtualization Mode on the same system.

Virtualization Mode doesn't replace Administration Mode for general server administration. Install each mode on a separate system to use both experiences in the same environment. For more information about the capabilities and architecture of each experience, see [What is Windows Admin Center Virtualization Mode?](../virtualization-mode-overview) For Virtualization Mode requirements and installation guidance, see [Install Windows Admin Center Virtualization Mode](../install-virtualization-mode).

## Administration Mode installation topologies

For Administration Mode, choose one of the following installation topologies.

![Diagram that shows the four Administration Mode installation topologies.](../media/deployment-options/install-options.png)

| Topology | Install location | Choose this topology when |
| --- | --- | --- |
| Local client | [Install Windows Admin Center](../deploy/install) on a local Windows 11 client that has connectivity to the managed servers. | One administrator needs a quick setup for testing, ad hoc work, or small-scale management. |
| Gateway server | [Install Windows Admin Center](../deploy/install) on a designated gateway server that client browsers can reach. | Multiple administrators need shared access or you manage a larger environment. |
| Managed server | [Install Windows Admin Center](../deploy/install) directly on a managed server. | You need to remotely manage that server or a cluster in which the server is a member node, such as in a distributed environment. |
| Failover cluster | Deploy high availability for the gateway service on a failover cluster. | A production environment requires a highly available and resilient management service. |

We don't recommend using Administration Mode for local management of the same server on which it's installed. To manage a server, connect to it remotely from Windows Admin Center installed on a management PC or another server.

These topology choices don't apply to Virtualization Mode, which uses a dedicated appliance and has separate installation requirements.

## Installation supported operating systems

Use the following Windows operating systems to install Windows Admin Center Administration Mode:

| **Platform** | **Administration Mode topology** |
| --- | --- |
| Windows 11 | Local client |
| Windows 11 ARM64 Client | Local client |
| Windows Server Semi-Annual Channel | Gateway server, managed server, failover cluster |
| Windows Server 2025 | Gateway server, managed server, failover cluster |
| Windows Server 2022 | Gateway server, managed server, failover cluster |
| Windows Server 2019 | Gateway server, managed server, failover cluster |
| Windows Server 2016 | Gateway server, managed server, failover cluster |

To use Administration Mode:

- **Local client:** Launch the Windows Admin Center gateway from the Start menu, and connect to it from a client web browser by accessing `https://localhost:6516`.
- **Other topologies:** Connect to the Windows Admin Center gateway on a different machine from a client browser by using its URL, for example, `https://servername.contoso.com`.

Warning

Don't install Windows Admin Center on a domain controller because this configuration isn't supported. For more information, see [domain controller security best practices](../../../identity/ad-ds/plan/security-best-practices/securing-domain-controllers-against-attack).

Note

Port usage and defaults for Windows Admin Center installations on the modernized gateway vary from what is mentioned above. For more information, see [what's different in the modernized gateway](../understand/modernized-gateway).

## Installation: Supported web browsers

Microsoft Edge (including [Microsoft Edge insider](https://www.microsoft.com/edge/download/insider)) and Google Chrome are tested and supported on Windows 10 and 11. Other web browsers, including Firefox, aren't currently part of our test matrix and are therefore not *officially* supported. These browsers might have problems running Windows Admin Center. For example, Firefox has its own certificate store, so you must import the `Windows Admin Center Client` certificate into Firefox to use Windows Admin Center on Windows 10. For more details, see [browser-specific known issues](../support/known-issues#browser-specific-issues).

## Administration Mode supported management targets

Use Windows Admin Center Administration Mode to manage the following Windows operating systems:

| Version | Manage*node*via*Server Manager* | Manage via*Cluster Manager* |
| --- | --- | --- |
| Windows 11 | Yes (via Computer Management) | N/A |
| Windows 11 ARM64 client | Yes (via Computer Management) | N/A |
| Windows Server Semi-Annual Channel | Yes | Yes |
| Windows Server 2025 | Yes | Yes |
| Windows Server 2022 | Yes | Yes |
| Windows Server 2019 | Yes | Yes |
| Windows Server 2016 | Yes | Yes, with [latest cumulative update](../use/manage-hyper-converged#prepare-your-windows-server-2016-cluster-for-windows-admin-center) |
| Microsoft Hyper-V Server 2016 | Yes | Yes |

Windows Admin Center requires PowerShell features that are not included in Windows Server 2012 and 2012 R2. If you will manage these with Windows Admin Center, you will need to install Windows Management Framework (WMF) version 5.1 or higher on those servers.

Type `$PSVersiontable` in PowerShell to verify that WMF is installed, and that the version is 5.1 or higher.

If WMF isn't installed, you can [download WMF 5.1](https://www.microsoft.com/download/details.aspx?id=54616).

## Administration Mode high availability

You can enable high availability for the Administration Mode gateway service by deploying Windows Admin Center in an active-passive model on a failover cluster. If one of the nodes in the cluster fails, Windows Admin Center gracefully fails over to another node, so you can continue managing the servers in your environment without interruption.

[Deploy Windows Admin Center with high availability](../deploy/high-availability).