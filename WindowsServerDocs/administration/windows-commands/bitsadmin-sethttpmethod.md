---
layout: Conceptual
title: bitsadmin sethttpmethod | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-sethttpmethod
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin sethttpmethod command, which sets the HTTP verb to use.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2019-03-01T00:00:00.0000000Z
locale: en-us
document_id: 6aae703b-cd31-b781-e862-8177241c8abf
document_version_independent_id: 970866e3-0238-c205-05ee-ea5bd00026fc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-sethttpmethod.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-sethttpmethod
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-sethttpmethod.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4cd52b8e-8511-c846-60b6-791822cc2a50
---

# bitsadmin sethttpmethod | Microsoft Learn

Sets the HTTP verb to use.

## Syntax

```
bitsadmin /sethttpmethod <job> <httpmethod>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| httpmethod | The HTTP verb to use. For information about available verbs, see [Method Definitions](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html). |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)