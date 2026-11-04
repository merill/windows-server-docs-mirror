---
layout: Conceptual
title: bcdboot | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bcdboot
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bcdboot command, which quickly set up a system partition, or repair the boot environment located on the system partition.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a288353c-cce4-82dc-1285-6857758b0166
document_version_independent_id: dfb4d079-d860-d4fd-b93c-47bbcdc0fb85
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bcdboot.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bcdboot
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bcdboot.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ec77bbeb-571a-5382-06c2-b3aa6b6aec00
---

# bcdboot | Microsoft Learn

Enables you to quickly set up a system partition, or to repair the boot environment located on the system partition. The system partition is set up by copying a simple set of Boot Configuration Data (BCD) files to an existing empty partition.

## Syntax

```
bcdboot <source> [/l] [/s]
```

### Parameters

| Parameter | Description |
| --- | --- |
| source | Specifies the location of the Windows directory to use as the source for copying boot environment files. |
| /l | Specifies the locale. The default locale is US English. |
| /s | Specifies the volume letter of the system partition. The default is the system partition identified by the firmware. |

## Examples

For information about where to find BCDboot and examples of how to use this command, see the [BCDboot Command-Line Options](/en-us/previous-versions/windows/it-pro/windows-8.1-and-8/hh824874%28v=win.10%29) topic.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)