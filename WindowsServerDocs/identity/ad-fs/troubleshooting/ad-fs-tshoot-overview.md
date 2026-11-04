---
layout: Conceptual
title: Troubleshoot AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: Learn about the strategies and tools that you can use to diagnose and troubleshoot various aspects of Active Directory Federation Services.
ms.date: 2023-05-19T00:00:00.0000000Z
ms.topic: troubleshooting-general
locale: en-us
document_id: baef5a1f-dd97-c75b-3306-30ccfc4ae180
document_version_independent_id: 0abb596b-6ed3-3391-90ee-bec23218553a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/troubleshooting/ad-fs-tshoot-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 03e9e0c3-3072-bbb5-73d1-1a88c388f5be
---

# Troubleshoot AD FS | Microsoft Learn

Active Directory Federation Services (AD FS) has many moving pieces, touches many different things, and has many different dependencies. This complexity can give rise to various issues. This article helps to get you started on troubleshooting these issues. It introduces you to the common areas where you should focus, how to enable features for more information, and the various tools to track down problems.

## What to check first

Before you dive into in-depth troubleshooting, check these things first:

- **Domain Name System (DNS) configuration**: Can you resolve the name of the federation service? This connection should resolve to either the load balancer's IP address or the IP address of one of the AD FS servers in your farm. For more information, see [AD FS troubleshooting: DNS](ad-fs-tshoot-dns).
- **AD FS endpoints**: Can you browse to the AD FS endpoints? Browsing to this endpoint can determine whether or not your AD FS web server is responding to requests. If you can get to this file, you know that AD FS is servicing requests over 443. For more information, see [AD FS troubleshooting: AD FS metadata endpoints](ad-fs-tshoot-endpoints).
- **Identity Provider (IdP)-initiated sign-in**: Can you sign in and authenticate via the IdP-initiated sign-in page? Ensure that this page is enabled because it's disabled by default. Use `Set-AdfsProperties -EnableIdPInitiatedSignOn $true` to enable the page. If you can sign in and authenticate, you know that AD FS is working in this area. For more information, see [AD FS troubleshooting: IdP-initiated sign-in](ad-fs-tshoot-initiatedsignon).

## Common troubleshooting areas

| Name | Description |
| --- | --- |
| [Events and logging](ad-fs-tshoot-logging) | Use Windows Event Logs to view high-level and low-level information via the admin and trace logs. You can also use logs to view security auditing. |
| [SQL connectivity](ad-fs-tshoot-sql) | Information on how to test the connectivity between your AD FS servers and the back-end SQL databases. |
| [Claims issuance](ad-fs-tshoot-claims-issuance) | Information on how to determine whether AD FS is issuing claims correctly. |
| [Loop detection](ad-fs-tshoot-loop) | Information on how to determine and prevent users from being bounced back and forth between the IdP and a relying party. |
| [Certificates](ad-fs-tshoot-certs) | Typical certificate issues that can arise. |
| [Fiddler](ad-fs-tshoot-fiddler) | Information on how to install and use Fiddler. |
| [WS-Federation with Fiddler](ad-fs-tshoot-fiddler-ws-fed) | Detailed Fiddler trace of a WS-Federation interaction. |
| [Claim rules syntax](ad-fs-tshoot-claims-rules) | Information on how to troubleshoot claim rules and their syntax. |
| [Integrated Windows Authentication](ad-fs-tshoot-iwa) | Information on how to troubleshoot integrated authentication. |
| [Microsoft Entra ID](ad-fs-tshoot-azure) | Information on how to troubleshoot AD FS interaction with Microsoft Entra ID. |