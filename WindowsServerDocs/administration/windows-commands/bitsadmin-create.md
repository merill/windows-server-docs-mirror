---
layout: Conceptual
title: bitsadmin create | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-create
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin create command, which creates a transfer job with the given display name.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 87f389a7-0e52-93c0-5bc9-0be9cb5be3c6
document_version_independent_id: 2ecd73f0-8554-9fb0-b0fc-076b50909e1a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-create.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-create
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-create.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2efe9967-121d-cd06-bcc7-0cdd79a1bf0c
---

# bitsadmin create | Microsoft Learn

Creates a transfer job with the given display name.

Note

The **/Upload** and **/Upload-Reply** parameter types aren't supported by BITS 1.2 and earlier.

## Syntax

```
bitsadmin /create [type] displayname
```

### Parameters

| Parameter | Description |
| --- | --- |
| type | There are three types of jobs:<br>- **/Download.** Transfers data from a server to a local file.<br>- **/Upload.** Transfers data from a local file to a server.<br>- **/Upload-Reply.** Transfers data from a local file to a server and receives a reply file from the server.<br><br>This parameter defaults to **/Download** if it's not specified. |
| displayname | The display name assigned to the newly created job. |

## Examples

To create a download job named *myDownloadJob*:

```
bitsadmin /create myDownloadJob
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin resume command](bitsadmin-resume)
- [bitsadmin command](bitsadmin)