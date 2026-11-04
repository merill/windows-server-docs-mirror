---
layout: Conceptual
title: Customize WebSocket validation for Windows Admin Center gateway | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/configure/websocket-validation
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn how administrators can customize the WebSocket validation for their Windows Admin Center (Project Honolulu) instance.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2021-10-22T00:00:00.0000000Z
locale: en-us
document_id: 092d8e33-d5af-fd1e-31da-bc2be501e4a4
document_version_independent_id: 092d8e33-d5af-fd1e-31da-bc2be501e4a4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/configure/websocket-validation.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/configure/websocket-validation
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/configure/websocket-validation.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 8b955f00-7d60-2740-0f6a-98cfae76ff7c
---

# Customize WebSocket validation for Windows Admin Center gateway | Microsoft Learn

To protect WebSocket access, WebSocket connection will now validate **origin** state from the browser so not any external application could get access the WebSocket API defined on the gateway.

## Customization of validation

Validation can be adjusted to customize various conditions.

User can configure WebSocket override setting at a Windows Admin Center registry value, `HKLM\Software\Microsoft\ServerManagementGateway\WebSocketValidationOverride`, to specify exceptional **origin host** name and **origin port**. This include wildcard name such as "`*.mydomain.mycompany.net`" or just "`*`" to accept all. Wildcard must be specified single form like "`*.`" and cannot be combined with complex string match condition like "`something*something`".

Example of accepted formats are as follows:

- Always allows origin host defined on current TLS certificate. (subject name, alternate DNS names)
- Always allows origin port configured to Windows Admin Center
- "`*`" - accept any origin host and origin port
- "`*:9876`" - accept any origin host and origin port 9876
- "`:9876`" - accept origin port 9876
- "\*`.my.domain.com`" - accept origin host &lt;any.any.any...&gt;.my.domain.com
- "`*.my.domain.com:9876`" - accept origin host &lt;any.any.any...&gt;.my.domain.com and origin port 9876

## Prevention logic

Gateway adds a session cookie (WAC-SESSION) for user browser. It associates the browser session and username always. It prevents different user attempting using the same browser session.

- When UI starts a WebSocket connection the browser sends the session cookie back to Gateway.
- Gateway validates authenticated username matched with the session cookie always.

Gateway looks for **origin header**, which is endpoint URL that original Windows Admin Center site was loaded.

- Gateway validated **origin host** and **origin port** against current SSL certificate settings which includes list of DNS host names. This tells the UI code is loaded from expected DNS name sites and port.

## RDP enhancement

On RDP TCP connection, Gateway only allows to use port 3389 (RDP) and port 2179 (VM connection), so TCP forwarding feature cannot be used for any other purpose.

## Possible side effect

If user uses Windows Admin Center by IP address or something not described on the SSL certificate, user cannot access WebSocket because it's not trustable. If it needs to support, modify `HKLM\Software\Microsoft\ServerManagementGateway\WebSocketValidationOverride` registry value to set the IP address or just specify "`*`" to ignore validation.