---
layout: Conceptual
title: bitsadmin setvalidationstate | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setvalidationstate
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setvalidationstate command, which sets the content validation state of the given file within the job.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 8f147e2c-546a-ff36-d933-f9d9b933ce4d
document_version_independent_id: 8bc0a580-2be4-befb-e1a1-251da5c8d2e3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setvalidationstate.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setvalidationstate
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setvalidationstate.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 43acab31-8e88-c6ff-942e-fe70e041cf5c
---

# bitsadmin setvalidationstate | Microsoft Learn

Sets the content validation state of the given file within the job.

## Syntax

```
bitsadmin /setvalidationstate <job> <file_index> <TRUE|FALSE>
```

### Parameters

| Parameter | Description |
| --- | --- |
| Job | The job's display name or GUID. |
| file\_index | Starts at 0. |
| TRUE or FALSE | **TRUE** turns on content validation for the specified file, while **FALSE** turns it off. |

## Examples

To set the content validation state of file 2 to TRUE for the job named *myDownloadJob*:

```
bitsadmin /setvalidationstate myDownloadJob 2 TRUE
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)