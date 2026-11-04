---
layout: Conceptual
title: Active Directory-Integrated DNS Zones | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/active-directory-integrated-dns-zones
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Active Directory-Integrated DNS Zones'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 49d2f534-0183-807f-c3fc-088936f5b645
document_version_independent_id: 51601221-39b9-bb21-b3aa-c615b1003a67
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Active-Directory-Integrated-DNS-Zones.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/active-directory-integrated-dns-zones
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Active-Directory-Integrated-DNS-Zones.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 5f8d2608-b553-8568-92bf-e4afb1c4076d
---

# Active Directory-Integrated DNS Zones | Microsoft Learn

Domain Name System (DNS) servers running on domain controllers can store their zones in Active Directory Domain Services (AD DS). In this way, it is not necessary to configure a separate DNS replication topology that uses ordinary DNS zone transfers because all zone data is replicated automatically by means of Active Directory replication. This simplifies the process of deploying DNS and provides the following advantages:

- Multiple masters are created for DNS replication. Therefore, any domain controller in the domain running the DNS Server service can write updates to the Active Directory-integrated DNS zones for the domain name for which they are authoritative. A separate DNS zone transfer topology is not needed.
- Secure dynamic updates are supported. Secure dynamic updates allow an administrator to control what computers update what names and prevent unauthorized computers from overwriting existing names in DNS.

Active Directory-integrated DNS in Windows Server 2008 stores zone data in application directory partitions. (There are no behavioral changes from Windows Server 2003-based DNS integration with Active Directory.) The following DNS-specific application directory partitions are created during AD DS installation:

- A forest-wide application directory partition, called ForestDnsZones
- Domain-wide application directory partitions for each domain in the forest, named DomainDnsZones

For more information about how AD DS stores DNS information in application partitions, see the [DNS Technical Reference](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc779926%28v=ws.10%29).

Note

We recommend that you install DNS when you run the Active Directory Domain Services Installation Wizard (Dcpromo.exe). If you do this, the wizard creates the DNS zone delegation automatically. For more information, see [Deploying a Windows Server 2008 Forest Root Domain](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731174%28v=ws.10%29).