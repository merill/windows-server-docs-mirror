---
layout: Conceptual
title: Increase Concurrent Authentications Processed by NPS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-concurrent-auth
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to improve NPS performance by increasing the number of concurrent authentications allowed between the NPS and the domain controller.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 7e40427d-d4f4-c706-e9e8-a9994966e0ea
document_version_independent_id: ceb914d5-a1db-89ee-d4fb-0546087cd425
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-concurrent-auth.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-concurrent-auth
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-concurrent-auth.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 2aa64dc3-73a5-331f-0bf7-103461a52c15
---

# Increase Concurrent Authentications Processed by NPS | Microsoft Learn

You can use this topic for instructions on configuring Network Policy Server concurrent authentications.

If you installed Network Policy Server (NPS) on a computer other than a domain controller and the NPS is receiving a large number of authentication requests per second, you can improve NPS performance by increasing the number of concurrent authentications allowed between the NPS and the domain controller.

To do this, you must edit the following registry key:

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters`

Add a new DWORD value named **MaxConcurrentApi** and assign to it a value of 150.

Caution

If you assign a value to **MaxConcurrentApi** that is too high, your NPS might place an excessive load on your domain controller.

For more information about MaxConcurrentApi, see [How to do performance tuning for NTLM authentication by using the MaxConcurrentApi setting](/en-us/troubleshoot/windows-server/windows-security/performance-tuning-ntlm-authentication-maxconcurrentapi)

For more information about managing NPS, see [Manage Network Policy Server](nps-manage-top).

For more information about NPS, see [Network Policy Server (NPS)](nps-top).