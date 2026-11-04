---
layout: Conceptual
title: fsutil repair | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-repair
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil repair command, which administers and monitors NTFS self-healing repair operations.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: da08d8c2-14de-4156-9d32-989cd3c37d1c
document_version_independent_id: f5299423-3e69-eb7e-a09a-deebf57b9bbb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-repair.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-repair
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-repair.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: daec4f2c-08d0-fa3f-ccd3-731f249a0817
---

# fsutil repair | Microsoft Learn

Administers and monitors NTFS self-healing repair operations. Self-healing NTFS attempts to correct corruptions of the NTFS file system online, without requiring **Chkdsk.exe** to be run. For more information, see [Self-healing NTFS](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc771388%28v=ws.10%29).

## Syntax

```
fsutil repair [enumerate] <volumepath> [<logname>]
fsutil repair [initiate] <volumepath> <filereference>
fsutil repair [query] <volumepath>
fsutil repair [set] <volumepath> <flags>
fsutil repair [wait][<waittype>] <volumepath>

```

### Parameters

| Parameter | Description |
| --- | --- |
| enumerate | Enumerates the entires of a volume's corruption log. |
| `<logname>` | Can be `$corrupt`, the set of confirmed corruptions in the volume or `$verify`, a set of potential, unverified corruptions in the volume. |
| initiate | Initiates NTFS self-healing. |
| `<filereference>` | Specifies the NTFS volume-specific file ID (file reference number). The file reference includes the segment number of the file. |
| query | Queries the self-healing state of the NTFS volume. |
| set | Sets the self-healing state of the volume. |
| `<flags>` | Specifies the repair method to be used when setting the self-healing state of the volume.<br>This parameter can be set to three values:<br><br>- **0x01** - Enables general repair.<br>- **0x09** - Warns about potential data loss without repair.<br>- **0x00** - Disables NTFS self-healing repair operations. |
| state | Queries the corruption state of the system or for a given volume. |
| wait | Waits for repair(s) to complete. If NTFS has detected a problem on a volume on which it is performing repairs, this option allows the system to wait until the repair is complete before it runs any pending scripts. |
| `[waittype {0|1}]` | Indicates whether to wait for the current repair to complete or to wait for all repairs to complete. The *waittype* parameter can be set to the following values:<br>- **0** - Waits for all repairs to complete. (default value)<br>- **1** - Waits for the current repair to complete. |

### Examples

To enumerate the confirmed corruptions of a volume, type:

```
fsutil repair enumerate C: $Corrupt
```

To enable self-healing repair on drive C, type:

```
fsutil repair set c: 1
```

To disable self-healing repair on drive C, type:

```
fsutil repair set c: 0
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)
- [Self-healing NTFS](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc771388%28v=ws.10%29)