---
layout: Conceptual
title: bitsadmin setnoprogresstimeout | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setnoprogresstimeout
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setnoprogresstimeout command, which sets the length of time, in seconds, that the service tries to transfer the file after a transient error occurs.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 3ade7c24-f857-013b-4044-4cd7e4e3e691
document_version_independent_id: d22969eb-ab7b-4c48-c6f6-cdb29dcdce70
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setnoprogresstimeout.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setnoprogresstimeout
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setnoprogresstimeout.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a16a72e6-8162-ba68-6368-3b106c7875da
---

# bitsadmin setnoprogresstimeout | Microsoft Learn

Sets the length of time, in seconds, that BITS tries to transfer the file after the first transient error occurs.

## Syntax

```
bitsadmin /setnoprogresstimeout <job> <timeoutvalue>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| timeoutvalue | The length of time that BITS waits to transfer a file after the first error, in seconds. |

### Remarks

- The "no progress" timeout interval begins when the job encounters its first transient error.
- The timeout interval stops or resets when a byte of data is successfully transferred.
- If the "no progress" timeout interval exceeds the *timeoutvalue*, then the job is placed in a fatal error state.

## Examples

To set the "no progress" timeout value to 20 seconds, for the job named *myDownloadJob*:

```
bitsadmin /setnoprogresstimeout myDownloadJob 20
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)