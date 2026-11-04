---
layout: Conceptual
title: DirectAccess Known Issues | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/directaccess-known-issues
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: This topic provides a link to Microsoft Technical Support documents for DirectAccess in Windows Server 2016.
ms.topic: troubleshooting-known-issue
ms.author: roharwoo
author: robinharwood
ms.date: 2023-06-19T00:00:00.0000000Z
locale: en-us
document_id: 693ad579-d11f-7353-3b37-6ae8c7f79ac1
document_version_independent_id: cf3ccc86-8382-387b-2d9b-e1a60db37255
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/DirectAccess-Known-Issues.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/directaccess-known-issues
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/DirectAccess-Known-Issues.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 509c803a-8712-ced6-56c1-1d7734792a3f
---

# DirectAccess Known Issues | Microsoft Learn

## DNS registration of DirectAccess client IPv6 addresses

Starting with the Windows 10 May 2020 Update, a client no longer registers its IP addresses on DNS servers configured in a Name Resolution Policy Table (NRPT). If DNS registration is needed, for example **Manage Out**, it can be explicitly enabled with this registry key on the client:

Path: `HKLM\System\CurrentControlSet\Services\Dnscache\Parameters` Type: `DWORD` Value name: `DisableNRPTForAdapterRegistration` Values:`1` - DNS Registration disabled (default since the Windows 10 May 2020 Update)`0` - DNS Registration enabled