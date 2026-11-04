---
layout: Conceptual
title: Enabling Advanced Features for AD DS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/enabling-advanced-features-for-ad-ds
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Enabling Advanced Features for AD DS'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: f23f516f-ad0b-9cb7-d349-b53eb6c8a61a
document_version_independent_id: 17f3609c-bcd4-5981-e6e0-27ef1054b267
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Enabling-Advanced-Features-for-AD-DS.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/enabling-advanced-features-for-ad-ds
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Enabling-Advanced-Features-for-AD-DS.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: e99b8b97-80ca-53c2-64f6-85a7c3322d0a
---

# Enabling Advanced Features for AD DS | Microsoft Learn

Active Directory Domain Services (AD DS) makes it possible for you to introduce advanced features into your environment by raising the domain or forest functional levels. To use advanced AD DS features, you must identify the operating systems that are running on the domain controllers in your environment.

You must also determine the best functional level for your organization based on your existing infrastructure and then raise the domain or forest functional level as appropriate. You can raise the functional level when all domain controllers in the domain or forest are running an appropriate version of Windows. Although raising the functional level makes it possible for you to enable new features, it also limits the versions of Windows operating systems that you can run on domain controllers in your environment.