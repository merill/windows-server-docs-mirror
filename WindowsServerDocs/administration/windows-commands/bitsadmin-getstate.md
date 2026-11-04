---
layout: Conceptual
title: bitsadmin getstate | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-getstate
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin getstate command, which retrieves the state of the specified job.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-04-01T00:00:00.0000000Z
locale: en-us
document_id: ad148bfd-3d75-508b-8978-5d11057278e2
document_version_independent_id: 25d46068-05a9-b6aa-902a-b0ba07b693b8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-getstate.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-getstate
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-getstate.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3c03dfa6-118e-fac8-9af6-1bc957c71bbe
---

# bitsadmin getstate | Microsoft Learn

Applies to: Windows Server (All supported versions)

The `bitsadmin /getstate` command retrieves the state of a specified job.

## Syntax

```
bitsadmin /getstate <job>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |

#### Output

The returned output values can be:

| State | Description |
| --- | --- |
| `Queued` | The job is waiting to run. |
| `Connecting` | BITS is contacting the server. |
| `Transferring` | BITS is transferring data. |
| `Transferred` | BITS has successfully transferred all files in the job. |
| `Suspended` | The job is paused. |
| `Error` | A nonrecoverable error occurred; the transfer isn't retried. |
| `Transient_Error` | A recoverable error occurred; the transfer retries when the minimum retry delay expires. |
| `Acknowledged` | The job completed. |
| `Canceled` | The job was canceled. |

## Examples

To retrieve the state for the job named *myDownloadJob*:

```
bitsadmin /getstate myDownloadJob
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)