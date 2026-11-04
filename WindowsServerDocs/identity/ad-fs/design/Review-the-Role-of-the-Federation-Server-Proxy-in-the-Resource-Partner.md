---
layout: Conceptual
title: Review the Role of the Federation Server Proxy in the Resource Partner | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/review-the-role-of-the-federation-server-proxy-in-the-resource-partner
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Review the Role of the Federation Server Proxy in the Resource Partner'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 3c7587ac-c282-98cb-a327-84e55b5a24ff
document_version_independent_id: fe822254-83fe-8f02-ba67-99df04fd23f3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Review-the-Role-of-the-Federation-Server-Proxy-in-the-Resource-Partner.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/review-the-role-of-the-federation-server-proxy-in-the-resource-partner
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Review-the-Role-of-the-Federation-Server-Proxy-in-the-Resource-Partner.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 890cdf93-7140-7e6e-d2ed-4b3f4bda6281
---

# Review the Role of the Federation Server Proxy in the Resource Partner | Microsoft Learn

A federation server proxy in Active Directory Federation Services (AD FS) can function in one or more of the following roles, depending on how you configure the server to meet the needs of the resource partner organization:

- **Account partner discovery**: An Internet client computer must identify which account partner will authenticate it. The client finds the account partner by using an account partner discovery Web form (discoverclientrealm.aspx), which is stored on the federation server proxy in the resource partner. If more than one account partner is configured in the AD FS Management snap-in, a drop-down menu appears to the client with all the available account partners that are visible to Internet client computers that access the account partner discovery Web form. You can change how the account partner discovery Web form is presented to client computers by customizing the discoverclientrealm.aspx file.
- **Security token redirection**: The federation server proxy in the account partner sends the security tokens to the resource partner. The resource federation server proxy accepts these tokens and passes them on to the federation server in the resource partner. The resource federation server then issues a security token that is bound for a specific resource Web server. The resource federation server proxy then redirects the token to the client.

To summarize, a resource federation server proxy facilitates the federated logon process by redirecting client computers to a federation server that can authenticate the clients. A resource federation server proxy also acts as a proxy for client security tokens to resource federation servers.

Note

When it is necessary to help reduce the amount of hardware and the number of required certificates, the federation server proxy can be located on the same computer as the Web server.