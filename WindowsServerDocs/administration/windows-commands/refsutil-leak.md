---
layout: Conceptual
title: refsutil leak | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/refsutil-leak
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the refsutil leak tool, which detects and diagnoses storage leaks, revealing their location and size to optimize storage usage on a specified Resilient File System (ReFS) volume in Windows.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-04-03T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 22b6bf62-41b0-fbf5-18a5-8d9ad8b3246d
document_version_independent_id: 22b6bf62-41b0-fbf5-18a5-8d9ad8b3246d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/refsutil-leak.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/refsutil-leak
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/refsutil-leak.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c82f1f21-1933-daf9-9494-7fe1bdc651fa
---

# refsutil leak | Microsoft Learn

The `refsutil leak` command assists administrators in detecting and diagnosing storage leaks, which occur when storage space is consumed inefficiently or unnecessarily. When the specified Resilient File System (ReFS) volume is scanned, this command identifies the location and size of leaks, helping to optimize storage usage and maintain system performance.

## Syntax

```
refsutil leak <drive> [/a] [/x] [/v] [/d] [/q] [/t <count>] [/s <file>]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<drive>` | Specifies the drive letter in the format `E:` or the path to the volume mount point. |
| `/a` | If leak detection discovers corruption, this parameter attempts to fix it and rerun the leak detection. With this parameter enabled, leak detection restarts once for each corrupted directory found on the volume. |
| `/x` | Operates with an exclusive lock on the volume. Without this parameter, leak detection creates a snapshot of the volume for processing. |
| `/v` | Enables verbose output, providing more detailed information. |
| `/d` | Only performs a diagnosis. Leaks are reported to standard output (stdout) but isn't fixed. |
| `/q` | Queries the required space for the leak analysis operation. |
| `/t <count>` | Specifies how many CPU threads to use for leak detection. Utilizing more threads speeds up the process on a multi-core CPU. If set to `0`, it runs the detection in a single thread (not recommended). The default is `4` threads. |
| `/s <file>` | Uses the specified `<file>` as a scratch buffer for the operation. The `<file>` must be able to grow to the size reported by the `/q` parameter. If this parameter is omitted, a scratch buffer is created in the TEMP directory. |

Note

Using the `/d` and `/a` parameters together will triage all found directory and file corruptions, but doesn't fix leaks.

## Examples

To perform a leak analysis and generate a detailed report using F:\Scratch.tmp as the temporary file using `6` CPU threads, run this command:

```
refsutil leak D: /a /t 6 /s F:\Scratch.tmp
```

To perform a leak analysis and display detailed output using `5` CPU threads, run this command:

```
refsutil leak D: /a /d /v /t 5
```

To check the amount of space needed for a leak analysis on the D: drive, run this command:

```
refsutil leak D: /q
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)