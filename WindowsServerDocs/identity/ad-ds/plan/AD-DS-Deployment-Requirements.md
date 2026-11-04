---
layout: Conceptual
title: AD DS Deployment Requirements | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/ad-ds-deployment-requirements
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD DS Deployment Requirements'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: d9e1c0ce-d11c-281f-4a77-72c3bc2d6684
document_version_independent_id: db07d8ed-2912-6c3d-5c27-b2a2a313af91
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/AD-DS-Deployment-Requirements.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/ad-ds-deployment-requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/AD-DS-Deployment-Requirements.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: da32639c-649a-c9f9-0c6e-95f196e2f203
---

# AD DS Deployment Requirements | Microsoft Learn

The structure of your existing environment determines your strategy for deploying Windows Server 2008 Active Directory Domain Services (AD DS). If you are creating an AD DS environment and you do not have an existing domain structure, complete your AD DS design before you begin creating your AD DS environment. Then, you can deploy a new forest root domain and deploy the rest of your domain structure according to your design.

Also, as part of your AD DS deployment, you might decide to upgrade and restructure your environment. For example, if your organization has an existing Windows 2000 domain structure, you might perform an in-place upgrade of some domains and restructure others. In addition, you might decide to reduce the complexity of your environment by either restructuring domains between forests or restructuring domains within a forest after you deploy AD DS.

## Deploying a Windows Server 2008 forest root domain

The forest root domain provides the foundation for your AD DS forest infrastructure. To deploy AD DS, you must first deploy a forest root domain. To do this, you must review your AD DS design; configure the DNS service for the forest root domain; create the forest root domain, which consists of deploying forest root domain controllers, configuring the site topology for the forest root domain, and configuring operations master roles (also known as flexible single master operations or FSMO); and raise the forest and domain functional levels. The following illustration shows the overall process of deploying a forest root domain.

![Illustration that shows the overall process of deploying a forest root domain.](media/ad-ds-deployment-requirements/033aad0b-25ff-4793-8825-88a6daa01a55.gif)

For more information, see [Deploying a Windows Server 2008 Forest Root Domain](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731174%28v=ws.10%29).

## Deploying Windows Server 2008 regional domains

After you complete the deployment of the forest root domain, you are ready to deploy any new Windows Server 2008 regional domains that are specified by your design. To do this, you must deploy domain controllers for each regional domain. The following illustration shows the process of deploying regional domains.

![AD DS requirements](media/ad-ds-deployment-requirements/89a878c8-9a94-4180-ad43-ca75316a6318.gif)

For more information, see [Deploying Windows Server 2008 Regional Domains](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc755118%28v=ws.10%29).

## Upgrading Active Directory domains to Windows Server 2008

Upgrading your Windows 2000 or Windows Server 2003 domains to Windows Server 2008 domains is an efficient, straightforward way to take advantage of additional Windows Server 2008 features and functionality. You can upgrade domains to maintain your current network and domain configuration while improving the security, scalability, and manageability of your network infrastructure. Upgrading from Windows 2000 or Windows Server 2003 to Windows Server 2008 requires minimal network configuration. Upgrading also has little impact on user operations. For more information, see [Upgrading Active Directory Domains to Windows Server 2008 and Windows Server 2008 R2 AD DS Domains](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731188%28v=ws.10%29).

## Restructuring AD DS domains

When you restructure domains between Windows Server 2008 forests (interforest restructure), you can reduce the number of domains in your environment and therefore reduce administrative complexity and overhead. When you migrate objects between forests as part of this restructuring process, both the source domain and target domain environments exist simultaneously. This makes it possible for you to roll back to the source environment during the migration, if necessary.

When you restructure Windows Server 2008 domains within a Windows Server 2008 forest (intraforest restructure), you can consolidate your domain structure and therefore reduce administrative complexity and overhead. When you restructure domains within a forest, the migrated accounts no longer exist in the source domain.

For more information about how to use the Active Directory Migration Tool (ADMT) version 3.1 (ADMT v3.1) to restructure domains, see [ADMT Guide: Migrating and Restructuring Active Directory Domains](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc974332%28v=ws.10%29).