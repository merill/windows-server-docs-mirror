---
layout: Conceptual
title: Deploying AD DS in a Windows Server 2003 Organization | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/deploying-ad-ds-in-a-windows-server-2003-organization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Deploying AD DS in a Windows Server 2003 Organization'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: e653e107-c95a-50fa-e685-31ce312a6e6e
document_version_independent_id: ae950306-6ae8-a6c2-ebb7-f68f6f1b8501
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Deploying-AD-DS-in-a-Windows-Server-2003-Organization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/deploying-ad-ds-in-a-windows-server-2003-organization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Deploying-AD-DS-in-a-Windows-Server-2003-Organization.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 567e3ca0-a4d5-a639-53a6-f860c0b6b765
---

# Deploying AD DS in a Windows Server 2003 Organization | Microsoft Learn

If your organization is currently running Windows Server 2003 Active Directory, you can deploy Windows Server 2008 Active Directory Domain Services (AD DS) by either performing an in-place upgrade of some or all of your domain controllers' operating systems to Windows Server 2008 or by introducing domain controllers running Windows Server 2008 into your environment.

Before you can add a domain controller running Windows Server 2008 to an existing Windows Server 2003 Active Directory domain, you must run **adprep**, a command-line tool. Adprep extends the AD DS schema, updates default security descriptors of selected objects, and adds new directory objects as required by some applications. Adprep is available on the Windows Server 2008 installation disk (\sources\adprep\adprep.exe). For more information, see [Adprep](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc731728%28v=ws.11%29).

The following illustration shows the steps for deploying Windows Server 2008 AD DS in a network environment that is currently running Windows Server 2003 Active Directory.

![deploy in a windows 2003 org](media/deploying-ad-ds-in-a-windows-server-2003-organization/900c4eee-1119-4a9a-9310-755597428b71.gif)

Note

If you want to set the domain or forest functional level to Windows Server 2008 , all domain controllers in your environment must run the Windows Server 2008 operating system.

Consolidating resource domains and account domains that are upgraded in place from a Windows Server 2003 environment as part of your Windows Server 2008 AD DS deployment may require interforest or intraforest domain restructuring. Restructuring AD DS domains between forests helps you reduce the complexity of the representation of your organization in AD DS, and it helps reduce the associated administrative costs. Restructuring AD DS domains within a forest helps you decrease the administrative overhead for your organization by reducing replication traffic, reducing the amount of user and group administration that is required, and simplifying the administration of Group Policy. For more information, see [ADMT Guide: Migrating and Restructuring Active Directory Domains](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc974332%28v=ws.10%29).

For a list of detailed tasks that you can use to plan and deploy AD DS in an organization that is running Windows Server 2003 Active Directory, see [Checklist: Deploying AD DS in a Windows Server 2003 Organization](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc771407%28v=ws.10%29).