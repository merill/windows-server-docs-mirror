---
layout: Conceptual
title: bitsadmin reset | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-reset
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin reset command, which cancels all jobs in the transfer queue owned by the current user.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a1a1e885-77dc-82ce-0ea1-af373143e0aa
document_version_independent_id: 513f7dd1-137e-0cfe-d3ea-e237d18578d7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-reset.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-reset
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-reset.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1793663a-c915-6ba7-1e64-2c047f5abcde
---

# bitsadmin reset | Microsoft Learn

Cancels all jobs in the transfer queue owned by the current user. You can't reset jobs created by Local System. Instead, you must be an administrator and use the task scheduler to schedule this command as a task using the Local System credentials.

Note

If you have administrator privileges in BITSAdmin 1.5 and earlier, the /reset switch will cancel all the jobs in the queue. Additionally, the /allusers option isn't supported.

## Syntax

```
bitsadmin /reset [/allusers]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /allusers | Optional. Cancels all jobs in the queue owned by the current user. You must have administrator privileges to use this parameter. |

## Examples

To cancel all the jobs in the transfer queue for the current user.

```
bitsadmin /reset
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)