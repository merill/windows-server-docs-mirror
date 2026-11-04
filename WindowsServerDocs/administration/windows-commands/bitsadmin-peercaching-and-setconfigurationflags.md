---
layout: Conceptual
title: bitsadmin peercaching and setconfigurationflags | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-peercaching-and-setconfigurationflags
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin peercaching and setconfigurationflags command, which sets the configuration flags that determine if the computer can serve content to peers and if it can download content from peers.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d4aa125f-5137-58f5-1673-6c2a0647f768
document_version_independent_id: 57a37a68-b8c1-0dc7-41d1-e5fc05c40512
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-peercaching-and-setconfigurationflags.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-peercaching-and-setconfigurationflags
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-peercaching-and-setconfigurationflags.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 06af1e5e-bd46-879b-cffd-5886b8985be4
---

# bitsadmin peercaching and setconfigurationflags | Microsoft Learn

Sets the configuration flags that determine if the computer can serve content to peers and if it can download content from peers.

## Syntax

```
bitsadmin /peercaching /setconfigurationflags <job> <value>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| value | An unsigned integer with the following interpretation for the bits in the binary representation:<br>- To allow the job's data to be downloaded from a peer, set the least significant bit.<br>- To allow the job's data to be served to peers, set the second bit from the right. |

## Examples

To specify the job's data to be downloaded from peers for the job named *myDownloadJob*:

```
bitsadmin /peercaching /setconfigurationflags myDownloadJob 1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)
- [bitsadmin peercaching command](bitsadmin-peercaching)