---
layout: Conceptual
title: bitsadmin peercaching and getconfigurationflags | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-peercaching-and-getconfigurationflags
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin peercaching and getconfigurationflags command, which gets the configuration flags that determine if the computer serves content to peers and if it can download content from peers.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a67725b3-85e4-8c38-0073-fc3549c86aa5
document_version_independent_id: c7f49489-261b-adc2-85a0-f6d3299ae894
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-peercaching-and-getconfigurationflags.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-peercaching-and-getconfigurationflags
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-peercaching-and-getconfigurationflags.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5d84b4a8-2fa9-d93d-0f05-5fbab0ae8181
---

# bitsadmin peercaching and getconfigurationflags | Microsoft Learn

Gets the configuration flags that determine if the computer serves content to peers and if it can download content from peers.

## Syntax

```
bitsadmin /peercaching /getconfigurationflags <job>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |

## Examples

To get the configuration flags for the job named *myDownloadJob*:

```
bitsadmin /peercaching /getconfigurationflags myDownloadJob
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)
- [bitsadmin peercaching command](bitsadmin-peercaching)