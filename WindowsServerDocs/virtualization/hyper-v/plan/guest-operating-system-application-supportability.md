---
layout: Conceptual
title: Guest operating system and application supportability on Hyper-V | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/plan/guest-operating-system-application-supportability
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Understand which versions of Windows Server or Azure Local are compatible products for a guest operating system or application that has been validated for Hyper-V.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2022-01-11T00:00:00.0000000Z
locale: en-us
document_id: 03603e9b-f19a-ed2e-dcbe-1c6234cc4af5
document_version_independent_id: 03603e9b-f19a-ed2e-dcbe-1c6234cc4af5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/plan/guest-operating-system-application-supportability.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/plan/guest-operating-system-application-supportability
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/plan/guest-operating-system-application-supportability.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/289b8734-3abd-4162-bc19-e661c3f4c940
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a94795e-9024-410d-b38e-b67941440893
platformId: f5100f35-9c91-8351-2674-6b0d00758d1e
---

# Guest operating system and application supportability on Hyper-V | Microsoft Learn

Hyper-V is a hypervisor that is broadly used in many Microsoft server products, including the Windows Server family (Datacenter, Standard, and Essentials editions) and Azure Local. Hyper-V provides a platform with broad ecosystem support and compatibility. This article clarifies which versions of Windows Server or Azure Local map to which Hyper-V build numbers. This helps understand supported scenarios where a guest operating system or application has been validated for Hyper-V.

Although the different products that include Hyper-V could contain variations in features, the common codebase provides a consistent platform for guest operating systems and applications running inside of a virtual machine to run on compatible products that share the same Hyper-V build number. This means that any support or compatibility statements for a guest operating system or application that is certified for specific builds of Hyper-V is compatible with all products that share the same build number for Hyper-V.

The table below shows which Hyper-V build numbers are available in which compatible products:

| Hyper-V build | Compatible products |
| --- | --- |
| 20348 | Windows Server 2022 DatacenterWindows Server 2022 StandardWindows Server 2022 EssentialsAzure Stack HCI version 21H2 Azure Stack HCI version 22H2 |
| 17763 and 17784 | Windows Server 2019 DatacenterWindows Server 2019 StandardWindows Server 2019 EssentialsHyper-V Server 2019Azure Stack HCI version 20H2 |
| 14393 | Windows Server 2016 DatacenterWindows Server 2016 StandardWindows Server 2016 EssentialsHyper-V Server 2016 |

For more information, see:

- [Windows Server release information](../../../get-started/windows-server-release-info)
- [Supported Windows guest operating systems on Hyper-V](../supported-windows-guest-operating-systems-for-hyper-v-on-windows)
- [Supported Linux and FreeBSD guest operating systems on Hyper-V](../supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows)