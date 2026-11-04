---
layout: Conceptual
title: Assigning Domain Names | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/assigning-domain-names
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Assigning Domain Names'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: best-practice
locale: en-us
document_id: 2ba5b10c-64cd-e241-6d0b-138771f89910
document_version_independent_id: ffd1c7d0-0462-d4bb-2d6c-d8e12911d928
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Assigning-Domain-Names.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/assigning-domain-names
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Assigning-Domain-Names.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c4799e66-7782-6d07-7a6b-f27127646e7a
---

# Assigning Domain Names | Microsoft Learn

You must assign a name to every domain in your plan. Active Directory Domain Services (AD DS) domains have two types of names: Domain Name System (DNS) names and NetBIOS names. In general, both names are visible to end users. The DNS names of Active Directory domains include two parts, a prefix and a suffix. When creating domain names, first determine the DNS prefix. This is the first label in the DNS name of the domain. The suffix is determined when you select the name of the forest root domain. The following table lists the prefix naming rules for DNS names.

| Rule | Explanation |
| --- | --- |
| Select a prefix that is not likely to become outdated. | Avoid names such as a product line or operating system that might change in the future. We recommend using geographical names. |
| Select a prefix that includes Internet standard characters only. | A-Z, a-z, 0-9, and (-), but not entirely numerical. |
| Include 15 characters or less in the prefix. | If you choose a prefix length of 15 characters or less, the NetBIOS name is the same as the prefix. |

For more information, see [Naming conventions in Active Directory for computers, domains, sites, and OUs](https://support.microsoft.com/help/909264/).

Note

Although Dcpromo.exe in Windows Server 2008 and Windows Server 2003 allows you to create a single-label DNS domain name, you should not use a single-label DNS name for a domain for several reasons. In Windows Server 2008 R2, Dcpromo.exe does not allow you to create a single-label DNS name for a domain. For more information, see [Deployment and operation of Active Directory domains that are configured by using single-label DNS names](https://support.microsoft.com/help/300684/).

If the current NetBIOS name of the domain is inappropriate to represent the region or fails to satisfy the prefix naming rules, select a new prefix. In this case, the NetBIOS name of the domain is different from the DNS prefix of the domain.

For each new domain that you deploy, select a prefix that is appropriate for the region and that satisfies prefix naming rules. We recommend that the NetBIOS name of the domain be the same as the DNS prefix.

Document the DNS prefix and NetBIOS names that you select for each domain in your forest. You can add the DNS and NetBIOS name information to the "Domain Planning" worksheet that you created to document your plan for new and upgraded domains. To open it, download Job\_Aids\_Designing\_and\_Deploying\_Directory\_and\_Security\_Services.zip from [Job Aids for Windows Server 2003 Deployment Kit](https://microsoft.com/download/details.aspx?id=9608) and open "Domain Planning" (DSSLOGI\_5.doc).