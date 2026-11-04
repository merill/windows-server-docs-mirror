---
layout: Conceptual
title: bitsadmin util and enableanalyticchannel | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-util-and-enableanalyticchannel
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin util and enableanalyticchannel command, which enables or disables the BITS client analytic channel.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e8090b27-f94b-cb91-4344-3e26dbfc9e69
document_version_independent_id: 9ef5fa60-fa2c-b336-ae40-3f0a470bdbc8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-util-and-enableanalyticchannel.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-util-and-enableanalyticchannel
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-util-and-enableanalyticchannel.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d8b373fc-210b-0b4d-c009-0d1a9887fa9d
---

# bitsadmin util and enableanalyticchannel | Microsoft Learn

Enables or disables the BITS client analytic channel.

## Syntax

```
bitsadmin /util /enableanalyticchannel TRUE|FALSE
```

| Parameter | Description |
| --- | --- |
| TRUE or FALSE | **TRUE** turns on content validation for the specified file, while **FALSE** turns it off. |

## Examples

To turn the BITS client analytic channel on or off.

```
bitsadmin /util / enableanalyticchannel TRUE
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin util command](bitsadmin-util)
- [bitsadmin command](bitsadmin)