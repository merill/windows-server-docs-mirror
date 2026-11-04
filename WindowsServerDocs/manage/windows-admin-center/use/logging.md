---
layout: Conceptual
title: Event Logging in Windows Admin Center | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/use/logging
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn about event logging in Windows Admin Center.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2018-06-18T00:00:00.0000000Z
locale: en-us
document_id: cc9cac53-f87d-0f95-c03d-18b6f4389502
document_version_independent_id: 5c9be401-a770-63b5-3b76-2fbab0e57e01
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/use/logging.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/use/logging
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/use/logging.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 33af7b06-5d11-662f-148d-a3ded8cd7467
---

# Event Logging in Windows Admin Center | Microsoft Learn

Windows Admin Center writes event logs that show the management activities performed on the servers in your environment. Event logs can also help you troubleshoot any Windows Admin Center problems.

## Management activities

Windows Admin Center provides insight into the management activities performed on the servers in your environment by logging actions to the **WindowsAdminCenter** event channel in the event log of the managed server. `EventID` is `4000`, and `Source` is `SMEGateway`.

Windows Admin Center logs only actions on the managed server. Events aren't logged if a user accesses a server for read-only purposes.

Logged events include the following information:

| Key | Value |
| --- | --- |
| `PowerShell` | PowerShell script name that was run on the server, if the action ran a PowerShell script. |
| `CIM ` | CIM call that was run on the server, if the action ran a CIM call. |
| `Module` | Tool (or module) where the action was run. |
| `Gateway` | Name of the Windows Admin Center gateway machine where the action was run. |
| `UserOnGateway` | Username that's used to access the Windows Admin Center gateway and execute the action. |
| `UserOnTarget` | Username that's used to access the target managed server, if it's different from `UserOnGateway`. That is, the user accessed the server by using **Manage as** credentials. |
| `Delegation` | Boolean, if the target managed server trusts the gateway and credentials are delegated from the user's client machine. |
| `LAPS` | Boolean, if the user accessed the server by using [LAPS](/en-us/previous-versions/mt227395%28v=msdn.10%29) credentials. |
| `File` | Name of the uploaded file, if the action was a file upload. |

## Gateway usage

Windows Admin Center logs gateway activity to the event channel on the gateway computer to help you troubleshoot issues and view metrics on usage. These events are also logged to the **WindowsAdminCenter** event channel.

[Learn more about troubleshooting Windows Admin Center](../support/troubleshooting).