---
layout: Conceptual
title: Computer Naming | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/computer-naming
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Computer Naming'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: d07cdbe9-2346-fb7b-0ec5-1678ff7df341
document_version_independent_id: f16d19a0-6bf5-3dba-39a8-dbc8e21279e1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Computer-Naming.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/computer-naming
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Computer-Naming.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e30c1d4d-6a89-8095-19d8-68e515d51131
---

# Computer Naming | Microsoft Learn

When a computer running the Windows 2000, Windows XP, Windows Server 2003, Windows Server 2008 , or Windows Vista operating system joins a domain, by default the computer assigns itself a name. The name it assigns itself comprises the host name of the computer (that is, Computer Name in System Properties) and the Domain Name System (DNS) name of the Active Directory domain that the computer joined (that is, Primary DNS Suffix in System Properties). The concatenation of the host name and the DNS name of the domain is known as the fully qualified domain name (FQDN). For example, if a computer with host name Server1 joins the domain corp.contoso.com, the FQDN of the computer is server1.corp.contoso.com.

If a computer already has a different DNS domain name that was statically entered into a DNS zone or registered by an integrated DNS/Dynamic Host Configuration Protocol (DHCP) Server service, the FQDN of the computer is distinct from the name that was registered previously. The computer can be referenced by either name.

For more information about naming conventions in Active Directory Domain Services (AD DS), see [Naming conventions in Active Directory for computers, domains, sites, and OUs](https://support.microsoft.com/help/909264/).