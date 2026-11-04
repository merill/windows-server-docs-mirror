---
layout: Conceptual
title: Prepare Client Computers in the Account Partner | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/prepare-client-computers-in-the-account-partner
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Prepare Client Computers in the Account Partner'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 15ca978b-6df5-e212-5020-9686bd5eceb0
document_version_independent_id: f9ea0c4a-a9a5-4e2e-46c9-d14cd46183e0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Prepare-Client-Computers-in-the-Account-Partner.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/prepare-client-computers-in-the-account-partner
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Prepare-Client-Computers-in-the-Account-Partner.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 263d8e9b-777a-559f-9ba0-3d5ba467d840
---

# Prepare Client Computers in the Account Partner | Microsoft Learn

The easiest way for an administrator in an account partner organization to prepare client computers for access to Active Directory Federation Services (AD FS) federated applications is to use Group Policy. Group Policy provides a convenient way for you to push specific certificates and settings that are required for federation to all the client computers that will be used to access federated applications.

So that your client computers can seamlessly access federated applications without certificate prompts or trusted site–related prompts, we recommend that you first prepare each client computer before you deploy AD FS broadly in your organization. Consider using Group Policy to automatically:

- Configure Internet Explorer on each client computer to trust the account federation server.

    For more information, see [Configure Client Computers to Trust the Account Federation Server](../deployment/configure-client-computers-to-trust-the-account-federation-server).
- Install the appropriate account federation server, resource federation server, and Web server Secure Sockets Layer (SSL) certificates (or equivalent certificates that chain to a trusted root) on each client computer.

    For more information, see [Distribute Certificates to Client Computers by Using Group Policy](../deployment/distribute-certificates-to-client-computers-by-using-group-policy).