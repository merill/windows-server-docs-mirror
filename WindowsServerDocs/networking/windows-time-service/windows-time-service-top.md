---
layout: Conceptual
title: Windows Time Service (W32Time) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/windows-time-service/windows-time-service-top
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: 'Learn more about: Windows Time Service (W32Time)'
author: robinharwood
ms.author: roharwoo
ms.date: 2021-11-04T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 5c0f61c2-4721-5953-e06b-54feec153512
document_version_independent_id: 74bbf954-cbba-f911-dc34-4f1b478f30f9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/windows-time-service/windows-time-service-top.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/windows-time-service/windows-time-service-top
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/windows-time-service/windows-time-service-top.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 03853d13-f928-cddf-1e10-a9eadab780b8
---

# Windows Time Service (W32Time) | Microsoft Learn

The Windows Time service (W32Time) synchronizes the date and time for all computers running in Active Directory Domain Services (AD DS). Time synchronization is critical for the proper operation of many Windows services and line-of-business (LOB) applications. The Windows Time service uses the Network Time Protocol (NTP) to synchronize computer clocks on the network. NTP ensures that an accurate clock value, or timestamp, can be assigned to network validation and resource access requests.

In the Windows Time Service (W32Time) topic, the following content is available:

- **[Windows Server 2016 Accurate Time](accurate-time).** Time synchronization accuracy in Windows Server 2016 has been improved substantially, while maintaining full backwards NTP compatibility with older Windows versions. Under reasonable operating conditions, you can maintain a 1-ms accuracy with respect to UTC or better for Windows Server 2016 and Windows 10 Anniversary Update domain members.
- **[Support boundary for high-accuracy environments](support-boundary).** This article describes the support boundaries for the Windows Time service (W32Time) in environments that require highly accurate and stable system time.
- **[Configuring Systems for high accuracy](configuring-systems-for-high-accuracy).** Time synchronization in Windows 10 and Windows Server 2016 has been substantially improved. Under reasonable operating conditions, systems can be configured to maintain 1 ms (millisecond) accuracy or better (with respect to UTC).
- **[Windows Time for Traceability](windows-time-for-traceability).** Regulations in many sectors require systems to be traceable to UTC. This means that a system's offset can be attested with respect to UTC. To enable regulatory compliance scenarios, Windows 10 and Server 2016 provide new event logs to provide a picture from the perspective of the Operating System to form an understanding of the actions taken on the system clock. These event logs are generated continuously for Windows Time service and can be examined or archived for later analysis.
- **[Windows Time service technical reference](windows-time-service-tech-ref).**The W32Time service provides network clock synchronization for computers without the need for extensive configuration. The W32Time service is essential to the successful operation of Kerberos V5 authentication and, therefore, to AD DS-based authentication.
    - **[How the Windows Time service works](how-the-windows-time-service-works).** Although the Windows Time service is not an exact implementation of the Network Time Protocol (NTP), it uses the complex suite of algorithms that is defined in the NTP specifications to ensure that clocks on computers throughout a network are as accurate as possible.
    - **[Windows Time service tools and settings](windows-time-service-tools-and-settings).** Most domain member computers have a time client type of NT5DS, which means that they synchronize time from the domain hierarchy. The only typical exception to this is the domain controller that functions as the primary domain controller (PDC) emulator operations master of the forest root domain, which is usually configured to synchronize time with an external time source.