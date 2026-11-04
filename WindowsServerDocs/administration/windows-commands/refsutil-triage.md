---
layout: Conceptual
title: refsutil triage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/refsutil-triage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the refsutil triage tool, which ensures data integrity and consistency by scrubbing the directory contents or global tables on a ReFS (Resilient File System) volume in Windows.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-04-02T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: a7814073-38cc-148f-c6ef-0b0a5f789d34
document_version_independent_id: a7814073-38cc-148f-c6ef-0b0a5f789d34
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/refsutil-triage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/refsutil-triage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/refsutil-triage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c9812901-851c-23da-9ed6-7719a8b2e35f
---

# refsutil triage | Microsoft Learn

The `refsutil triage` command is used to scrub directory contents or global tables on a ReFS (Resilient File System) volume, ensuring data integrity and consistency.

## Syntax

```
refsutil triage <drive> [/s <id>] [/g] [/v]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<drive>` | Specifies the target drive, either as a drive letter in the format `E:` or as a path to the volume's mount point. |
| `/s <id>` | Scrubs the directory specified by `<id>`, where `<id>` is the file identifier for the directory. This option scrubs all files within the specified directory. This parameter can't be used with the `/g` parameter. |
| `/g` | Scrubs the global tables of the volume. This parameter can't be used with the `/s <id>` parameter. |
| `/v` | Displays verbose output, providing detailed information during the scrubbing operation. |

## Examples

To perform a directory scrub on the directory with file ID `15100` on the D: drive, run the following command:

```
refsutil triage D: /s 15100
```

To perform a directory scrub on the directory with file ID `16040` on the D: drive with verbose output, run the following command:

```
refsutil triage D: /s 16040 /v
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)