---
layout: Conceptual
title: QoS Policy Architecture | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/qos/qos-policy-architecture
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn about the architecture of QoS Policy.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: f054bdd6-275e-99a9-c5ed-2ac7779c3824
document_version_independent_id: aa6e8fb7-52b8-91e0-1f34-e35417f4c1ba
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/qos/qos-policy-architecture.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/qos/qos-policy-architecture
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/qos/qos-policy-architecture.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fbd4c825-5072-fcb0-9dea-09dae9397f88
---

# QoS Policy Architecture | Microsoft Learn

You can use this topic to learn about the architecture of QoS Policy.

The following figure shows the architecture of Policy-based QoS.

![Architecture of QoS Policy](../../media/qos/qos-policy-architecture.jpg)

The architecture of Policy-based QoS consists of the following components:

- **Group Policy Client Service**. A Windows service that manages user and computer configuration Group Policy settings.
- **Group Policy engine**. A component of the Group Policy Client Service that retrieves user and computer configuration Group Policy settings from Active Directory upon startup and periodically checks for changes (by default, every 90 minutes). If changes are detected, the Group Policy engine retrieves the new Group Policy settings. The Group Policy engine processes the incoming GPOs and informs the QoS Client Side Extension when the QoS policies are updated.
- **QoS Client Side Extension**. A component of the Group Policy Client Service that waits for an indication from the Group Policy engine that the QoS policies have changed and informs the QoS Inspection Module.
- **TCP/IP Stack**. The TCP/IP stack that includes integrated support for IPv4 and IPv6 and supports Windows Filtering Platform.
- **QoS Inspection**. Module A component within the TCP/IP stack that waits for indications of QoS policy changes from the QoS Client Side Extension, retrieves the QoS policy settings, and interacts with the Transport Layer and Pacer.sys to internally mark traffic that matches the QoS policies.
- **NDIS 6.x**. A standard interface between kernel-mode network drivers and the operating system in Windows Server and Client operating systems. NDIS 6.x supports lightweight filters, which is a simplified driver model for NDIS intermediate drivers and miniport drivers that provides better performance.
- **QoS Network Provider Interface (NPI)**. An interface for kernel-mode drivers to interact with Pacer.sys.
- **Pacer.sys**. An NDIS 6.x lightweight filter driver that controls packet scheduling for Policy-based QoS and for the traffic of applications that use the Generic QoS (GQoS) and Traffic Control (TC) APIs. Pacer.sys replaced Psched.sys in Windows Server 2003 and Windows XP. Pacer.sys is installed with the QoS Packet Scheduler component from the properties of a network connection or adapter.

For the next topic in this guide, see [QoS Policy Scenarios](qos-policy-scenarios).

For the first topic in this guide, see [Quality of Service (QoS) Policy](qos-policy-top).