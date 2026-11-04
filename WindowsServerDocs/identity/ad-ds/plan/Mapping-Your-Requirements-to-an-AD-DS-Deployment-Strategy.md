---
layout: Conceptual
title: Mapping Your Requirements to an AD DS Deployment Strategy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/mapping-your-requirements-to-an-ad-ds-deployment-strategy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Mapping Your Requirements to an AD DS Deployment Strategy'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 84c25bd1-4030-4cee-8383-8c3d8e77ed31
document_version_independent_id: e697f0f6-ef95-d6d4-7027-dde0423d3362
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Mapping-Your-Requirements-to-an-AD-DS-Deployment-Strategy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/mapping-your-requirements-to-an-ad-ds-deployment-strategy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Mapping-Your-Requirements-to-an-AD-DS-Deployment-Strategy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 2950a1d9-7273-4815-0de7-0691b3de3abd
---

# Mapping Your Requirements to an AD DS Deployment Strategy | Microsoft Learn

After you finish reviewing and identifying the Active Directory Domain Services (AD DS) design and deployment requirements and you determine which of them are related to your specific deployment, you can map those requirements to a specific AD DS deployment strategy.

Use the following table to determine which AD DS deployment strategy maps to the appropriate combination of AD DS design and deployment requirements for your organization. ("Yes" means that a specific requirement is necessary for your deployment strategy; "No" means that a specific requirement is not necessary for your deployment strategy.)

This table refers only to the three primary AD DS deployment strategies as described in this guide:

- [Deploying AD DS in a New Organization](deploying-ad-ds-in-a-new-organization)
- [Deploying AD DS in a Windows Server 2003 Organization](deploying-ad-ds-in-a-windows-server-2003-organization)
- [Deploying AD DS in a Windows 2000 Organization](deploying-ad-ds-in-a-windows-2000-organization)

However, you can create a hybrid or custom AD DS deployment strategy by using any combination of the AD DS design and deployment requirements to meet the needs of your organization.

| AD DS design and deployment requirements | Deploying AD DS in a New Organization | Deploying AD DS in a Windows Server 2003 Organization | Deploying AD DS in a Windows 2000 Organization |
| --- | --- | --- | --- |
| [Designing the Logical Structure for Windows Server 2008 AD DS](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc770806%28v=ws.10%29) | Yes | Yes | Yes |
| [Designing the Site Topology for Windows Server 2008 AD DS](designing-the-site-topology) | Yes | Yes | Yes |
| Planning Domain Controller Capacity | Yes | Yes | Yes |
| [Deploying a Windows Server 2008 Forest Root Domain](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731174%28v=ws.10%29) | Yes | No | No |
| [Deploying Windows Server 2008 Regional Domains](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc755118%28v=ws.10%29) | Yes | Yes | Yes |
| [Enabling Advanced Features for AD DS](enabling-advanced-features-for-ad-ds) | Yes | Yes, but all domain controllers in the environment must run Windows Server 2008 before you set the domain or forest functional level to Windows Server 2008. | Yes, but all domain controllers in the environment must run Windows Server 2008 before you set the domain or forest functional level to Windows Server 2008. |
| [Upgrading Active Directory Domains to Windows Server 2008 and Windows Server 2008 R2 AD DS Domains](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731188%28v=ws.10%29) | No | Yes | Yes |
| [ADMT Guide: Migrating and Restructuring Active Directory Domains](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc974332%28v=ws.10%29) | Yes, if you want to migrate a pilot domain into your production environment, merge with another organization and consolidate the two information technology (IT) infrastructures, or consolidate resource and account domains that you upgraded in place from Windows 2000 or Windows Server 2003 environments. | Yes, if you want to merge with another organization and consolidate the two IT infrastructures or consolidate resource and account domains that you upgraded in place from Windows 2000 or Windows Server 2003 environments. | Yes, if you want to merge with another organization and consolidate the two IT infrastructures or consolidate resource and account domains that you upgraded in place from Windows 2000 or Windows Server 2003 environments. |
| [ADMT Guide: Migrating and Restructuring Active Directory Domains](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc974332%28v=ws.10%29) | No | Yes, if you need to reduce the number of domains, reduce replication traffic and the amount of required user and group administration, or simplify the administration of Group Policy. | Yes, if you need to reduce the number of domains, reduce replication traffic and the amount of required user and group administration, or simplify the administration of Group Policy. |