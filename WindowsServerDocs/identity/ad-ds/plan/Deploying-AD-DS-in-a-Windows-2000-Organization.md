---
layout: Conceptual
title: Deploying AD DS in a Windows 2000 Organization | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/deploying-ad-ds-in-a-windows-2000-organization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Deploying AD DS in a Windows 2000 Organization'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 3ba55801-3500-31ff-bd5f-a3da29d076db
document_version_independent_id: 79392129-ea03-5a3b-1985-9ac48d2c4d26
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Deploying-AD-DS-in-a-Windows-2000-Organization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/deploying-ad-ds-in-a-windows-2000-organization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Deploying-AD-DS-in-a-Windows-2000-Organization.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 757f24b7-6bff-d1d7-9f20-419ff8b15ba5
---

# Deploying AD DS in a Windows 2000 Organization | Microsoft Learn

If your organization is currently running Windows 2000 Active Directory, you can deploy Windows Server 2008 Active Directory Domain Services (AD DS) by either performing an in-place upgrade of some or all of your domain controllers' operating systems to Windows Server 2008 or by introducing domain controllers running Windows Server 2008 into your environment.

Before you can add a domain controller running Windows Server 2008 to an existing Windows 2000 Active Directory domain, you must run **adprep**, a command-line tool. Adprep extends the AD DS schema, updates default security descriptors of selected objects, and adds new directory objects as required by some applications. Adprep is available on the Windows Server 2008 installation disk (\sources\adprep\adprep.exe). For more information, see [Adprep](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc731728%28v=ws.11%29).

Note

If you want to perform an in-place upgrade of an existing Windows 2000 AD DS domain controller to Windows Server 2008 , you must first upgrade the server to Windows Server 2003, and then upgrade it to Windows Server 2008 .

The following illustration shows the steps for deploying the Windows Server 2008 AD DS in a network environment that is currently running Windows 2000 Active Directory.

![deploying in a windows 2000 org](media/deploying-ad-ds-in-a-windows-2000-organization/ee51218a-a858-49d9-8b99-9986679191c1.gif)

Note

If you want to set the domain or forest functional level to Windows Server 2008 , all domain controllers in your environment must run the Windows Server 2008 operating system.

Consolidating resource and account domains that are upgraded in place from a Windows 2000 environment as part of your Windows Server 2008 AD DS deployment may require interforest or intraforest domain restructuring. Restructuring AD DS domains between forests helps you reduce the complexity of your organization and the associated administrative costs. Restructuring AD DS domains within a forest helps you to decrease the administrative overhead for your organization by reducing replication traffic, reducing the amount of user and group administration that is required, and simplifying the administration of Group Policy. For more information, see [ADMT Guide: Migrating and Restructuring Active Directory Domains](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc974332%28v=ws.10%29).

For a list of detailed tasks that you can use to plan and deploy AD DS in an organization that is currently running Windows 2000 Active Directory, see [Checklist: Deploying AD DS in a Windows 2000 Organization](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc732737%28v=ws.10%29).