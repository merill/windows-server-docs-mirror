---
layout: Conceptual
title: NTLM overview in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/kerberos/ntlm-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about NTLM, and find links to technical resources to Windows Authentication and NTLM for Windows Server.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-04-17T00:00:00.0000000Z
locale: en-us
document_id: 4a7ee325-0910-830e-3992-79d7ddf317e6
document_version_independent_id: 6d8d74ea-201c-4827-3898-a22024fbe640
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/kerberos/ntlm-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/kerberos/ntlm-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/kerberos/ntlm-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c6706815-12d8-cc1b-4f7d-b2c7222006a4
---

# NTLM overview in Windows Server | Microsoft Learn

This topic for the IT professional describes NTLM, any changes in functionality, and provides links to technical resources to Windows Authentication and NTLM for Windows Server.

NTLM authentication is a family of authentication protocols that are encompassed in the Windows Msv1\_0.dll. The NTLM authentication protocols include LAN Manager version 1 and 2, and NTLM version 1 and 2. The NTLM authentication protocols authenticate users and computers based on a challenge response mechanism that proves to a server or domain controller that a user knows the password associated with an account. When the NTLM protocol is used, a resource server must take one of the following actions to verify the identity of a computer or user whenever a new access token is needed:

- Contact a domain authentication service on the domain controller for the computer's or user's account domain, if the account is a domain account.
- Look up the computer's or user's account in the local account database, if the account is a local account.

## Current applications

NTLM authentication is still supported and must be used for Windows authentication with systems configured as a member of a workgroup. NTLM authentication is also used for local logon authentication on non-domain controllers. Kerberos version 5 authentication is the preferred authentication method for Active Directory environments, but a non-Microsoft or Microsoft application might still use NTLM.

Reducing the usage of the NTLM protocol in an IT environment requires both the knowledge of deployed application requirements on NTLM and the strategies and steps necessary to configure computing environments to use other protocols. New tools and settings have been added to help you discover how NTLM is used in order to selectively restrict NTLM traffic. For information about how to analyze and restrict NTLM usage in your environments, see [Introducing the Restriction of NTLM Authentication](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd560653%28v=ws.10%29) to access the Auditing and restricting NTLM usage guide.