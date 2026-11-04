---
layout: Conceptual
title: refsutil dedup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/refsutil-dedup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the refsutil dedup tool, which deduplicates a Resilient File System (ReFS) volume in Windows.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-04-02T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: d310d71e-f3af-a995-008d-fb68c2c68d6f
document_version_independent_id: d310d71e-f3af-a995-008d-fb68c2c68d6f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/refsutil-dedup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/refsutil-dedup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/refsutil-dedup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b8e5a83d-8290-7718-45d1-e58eded77ba5
---

# refsutil dedup | Microsoft Learn

The `refsutil compression` command manages data deduplication on a specified Resilient File System (ReFS) volume. You can either deduplicate the volume or scan it to see how much space can be saved by deduplicating equivalent clusters. You can also control CPU usage and choose between memory-mapped file I/O or asynchronous reads.

## Syntax

```
refsutil dedup <drive> [/d] [/s] [/cpu <percentage>] [/mm]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `drive` | Specifies the volume path in the `E:` format or a mount point. |
| `/d` | Deduplicates the volume. This parameter can't be used with the `/s` parameter. |
| `/s` | Scans the volume to determine how much space can be saved by deduplicating equivalent clusters. This parameter can't be used with the `/d` parameter. |
| `/cpu percentage` | Specifies the maximum percentage of CPU to use. Acceptable values are between 1-100. |
| `/mm` | Uses memory-mapped file I/O to read files for deduplication. This parameter must be used with either the `/d` or `/s` parameters. |

## Examples

To scan the D: volume and see how much space you can save by deduplicating equivalent clusters, run the command:

```
refsutil dedup D: /s
```

To deduplicate the D: volume using 50% of CPU resources, run the command:

```
refsutil dedup D: /d /cpu 50
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)