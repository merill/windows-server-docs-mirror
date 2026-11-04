---
layout: Conceptual
title: Creating a DNS Infrastructure Design | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/creating-a-dns-infrastructure-design
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Creating a DNS Infrastructure Design'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 8c39d2f2-c666-4236-e1e7-d0dce90a3d2a
document_version_independent_id: b7143f02-e968-a6f7-d001-0d6d009fd4b9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Creating-a-DNS-Infrastructure-Design.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/creating-a-dns-infrastructure-design
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Creating-a-DNS-Infrastructure-Design.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 896c5f6c-60e2-3d2a-22c2-4fdb99a2889a
---

# Creating a DNS Infrastructure Design | Microsoft Learn

After you create your Active Directory forest and domain designs, you must design a Domain Name System (DNS) infrastructure to support your Active Directory logical structure. DNS enables users to use friendly names that are easy to remember to connect to computers and other resources on IP networks. Active Directory Domain Services (AD DS) in Windows Server 2008 requires DNS.

The process for designing DNS to support AD DS varies according to whether your organization already has an existing DNS Server service or you are deploying a new DNS Server service:

- If you already have an existing DNS infrastructure, you must integrate the Active Directory namespace into that environment. For more information, see [Integrating AD DS into an Existing DNS Infrastructure](integrating-ad-ds-into-an-existing-dns-infrastructure).
- If you do not have a DNS infrastructure in place, you must design and deploy a new DNS infrastructure to support AD DS. For more information, see [Deploying Domain Name System (DNS)](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc780661%28v=ws.10%29).

If your organization has an existing DNS infrastructure, you must make sure that you understand how your DNS infrastructure will interact with the Active Directory namespace. For a worksheet to assist you in documenting your existing DNS infrastructure design, download Job\_Aids\_Designing\_and\_Deploying\_Directory\_and\_Security\_Services.zip from [Job Aids for Windows Server 2003 Deployment Kit](https://microsoft.com/download/details.aspx?id=9608) and open "DNS Inventory" (DSSLOGI\_8.doc).

Note

In addition to IP version 4 (IPv4) addresses, Windows Server also supports IP version 6 (IPv6) addresses. For a worksheet to assist you in listing the IPv6 addresses while documenting the recursive name resolution method of your current DNS structure, see [Appendix A: DNS Inventory](appendix-a--dns-inventory).

Before you design your DNS infrastructure to support AD DS, it can be helpful to read about the DNS hierarchy, the DNS name resolution process, and how DNS supports AD DS. For more information about the DNS hierarchy and name resolution process, see the [DNS Technical Reference](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc779926%28v=ws.10%29). For more information about how DNS supports AD DS, see the [DNS Support for Active Directory Technical Reference](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc781627%28v=ws.10%29).