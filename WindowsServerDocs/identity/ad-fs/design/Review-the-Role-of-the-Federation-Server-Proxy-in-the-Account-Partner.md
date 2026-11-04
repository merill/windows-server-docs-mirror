---
layout: Conceptual
title: Review the Role of the Federation Server Proxy in the Account Partner | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/review-the-role-of-the-federation-server-proxy-in-the-account-partner
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Review the Role of the Federation Server Proxy in the Account Partner'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 84984b0c-e5b0-cada-96e9-3279710590a4
document_version_independent_id: 3fb26231-d0cb-5eda-3a3d-de34d1a4bbb5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Review-the-Role-of-the-Federation-Server-Proxy-in-the-Account-Partner.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/review-the-role-of-the-federation-server-proxy-in-the-account-partner
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Review-the-Role-of-the-Federation-Server-Proxy-in-the-Account-Partner.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 8b5fa19a-f7b6-73b3-943e-1258cff8a502
---

# Review the Role of the Federation Server Proxy in the Account Partner | Microsoft Learn

The primary role of the federation server proxy in the perimeter network of the account partner organization in Active Directory Federation Services (AD FS) is to collect authentication credentials from a client computer that logs on over the Internet and to pass those credentials to the federation server, which is located inside the corporate network of the account partner organization. The account for the client computer is stored in the account partner's attribute store.

A federation server proxy can also function in one or more of the following roles, depending on how you configure it to meet the needs of the account partner organization:

- Relay Security Tokens—The federation server issues a security token to the federation server proxy, which then relays the token to the client computer. The security token is used to provide access for that client computer to a specific relying party.
- Collect Credentials—The federation server proxy uses a default client logon Web form (clientlogon.aspx) to collect password-based credentials through forms-based authentication. However, you can customize this form to accept other supported types of authentication, such as Secure Sockets Layer (SSL) client authentication. For more information about how to customize this page, see Customizing Client Logon and Home Realm Discovery Pages ([http://go.microsoft.com/fwlink/?LinkId=104275](/en-us/previous-versions/windows/desktop/legacy/bb625464%28v=vs.85%29)). A federation server proxy does not accept credentials through Windows Integrated Authentication.

To summarize, a federation server proxy in the account partner acts as a proxy for client logons to a federation server that is located in the corporate network. The federation server proxy also facilitates the distribution of security tokens to Internet clients that are destined for relying parties.

Caution

Exposing a federation server proxy on the account partner extranet will the client logon Web form accessible by anyone with Internet access. This can potentially leave your organization vulnerable to some password-based attacks, such as dictionary attacks or brute force attacks that can trigger account lockouts for user accounts that are stored in the corporate Active Directory Domain Services (AD DS).