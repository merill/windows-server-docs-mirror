---
layout: Conceptual
title: showmount | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/showmount
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the showmount command, which displays information about mounted file systems exported by Server for NFS on a specified computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9a61c6a0-7a37-c20f-8e7d-08713415cf14
document_version_independent_id: 490be918-a803-aaad-b51b-d2d751b7e71e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/showmount.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/showmount
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/showmount.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 07e5b61d-716c-d28e-312e-6da99c108025
---

# showmount | Microsoft Learn

You can use **showmount** to display information about mounted file systems exported by Server for NFS on a specified computer. If you don't specify a server, this command displays information about the computer on which the **showmount** command is run.

## Syntax

```
showmount {-e|-a|-d} <server>
```

### Parameters

| Parameter | Description |
| --- | --- |
| -e | Displays all the file systems exported on the server. |
| -a | Displays all Network File System (NFS) clients and the directories on the server each has mounted. |
| -d | Displays all directories on the server that are currently mounted by NFS clients. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Services for Network File System Command Reference](services-for-network-file-system-command-reference)