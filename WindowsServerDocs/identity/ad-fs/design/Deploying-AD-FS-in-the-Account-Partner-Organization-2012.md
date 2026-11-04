---
layout: Conceptual
title: Deploying AD FS in the Account Partner Organization | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/deploying-ad-fs-in-the-account-partner-organization-2012
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Deploying AD FS in the Account Partner Organization'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: be0db0cc-7d68-9f7c-323a-97507fde2206
document_version_independent_id: 484b7c35-6eef-9af9-4753-4e5988256e56
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Deploying-AD-FS-in-the-Account-Partner-Organization-2012.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/deploying-ad-fs-in-the-account-partner-organization-2012
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Deploying-AD-FS-in-the-Account-Partner-Organization-2012.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 40200cde-62bf-8045-d694-cbe6c0189862
---

# Deploying AD FS in the Account Partner Organization | Microsoft Learn

An account partner in Active Directory Federation Services (AD FS) represents the organization in the federation trust relationship that physically stores user accounts in a supported attribute store. For more information about which attribute stores are supported, see [The Role of Attribute Stores](../technical-reference/the-role-of-attribute-stores).

The federation server in the account partner organization authenticates local users and creates security tokens that are used by the resource partner in making authorization decisions. Relying parties such as Web sites and Web services are then able to easily register themselves with the federation server and consume issued tokens for authentication and access control.

In scenarios in which you need to provide your users with access to multiple federated applications or services—when each application or service is hosted by a different organization—you can configure the account partner federation server so that you can deploy multiple relying parties.

For more information about how to set up and configure an account partner organization, see [Checklist: Configuring the Account Partner Organization](../deployment/checklist--configuring-the-account-partner-organization).