---
layout: Conceptual
title: Deploying AD FS in the Resource Partner Organization | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/deploying-ad-fs-in-the-resource-partner-organization-2012
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Deploying AD FS in the Resource Partner Organization'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: a0abfbd1-bc95-db0d-0e6c-ffe1acc6829c
document_version_independent_id: 7539dd1b-7f6c-2ac9-30da-a999d835c4bc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Deploying-AD-FS-in-the-Resource-Partner-Organization-2012.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/deploying-ad-fs-in-the-resource-partner-organization-2012
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Deploying-AD-FS-in-the-Resource-Partner-Organization-2012.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: a43ebfe0-e9a7-513b-c2a7-eea401215b68
---

# Deploying AD FS in the Resource Partner Organization | Microsoft Learn

The resource partner organization in Active Directory Federation Services (AD FS) represents the organization whose Web servers may be protected by a resource-side federation server. The federation server at the resource partner uses the security tokens that are produced by the account partner to provide claims to the Web servers that are located in the resource partner.

In scenarios in which you need to provide access to federated services or applications to many different users—when some users reside in different organizations—you can configure the resource federation server so that you can deploy multiple account partners.

For more information about how to set up and configure a resource partner organization, see [Checklist: Configuring the Resource Partner Organization](../deployment/checklist--configuring-the-resource-partner-organization).