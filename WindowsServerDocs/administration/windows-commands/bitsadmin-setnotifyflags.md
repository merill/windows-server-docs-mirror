---
layout: Conceptual
title: bitsadmin setnotifyflags | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setnotifyflags
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setnotifyflags command, which sets the event notification flags for the specified job.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 93ccd80f-15af-d3e9-ce65-338896c00215
document_version_independent_id: e8dbe59b-766b-9643-b7eb-8dfc409ab52d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setnotifyflags.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setnotifyflags
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setnotifyflags.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7538ba28-53c5-e1db-8281-0c3a492de075
---

# bitsadmin setnotifyflags | Microsoft Learn

Sets the event notification flags for the specified job.

## Syntax

```
bitsadmin /setnotifyflags <job> <notifyflags>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| notifyflags | Can include one or more of the following notification flags, including:<br>- **1.** Generates an event when all files in the job have been transferred.<br>- **2.** Generates an event when an error occurs.<br>- **3.** Generates an event when all files have completed transfer or when an error occurs.<br>- **4.** Disables notifications. |

## Examples

To set the notification flags to generate an event when an error occurs, for a job named *myDownloadJob*:

```
bitsadmin /setnotifyflags myDownloadJob 2
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)