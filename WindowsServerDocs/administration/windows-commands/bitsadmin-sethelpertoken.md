---
layout: Conceptual
title: bitsadmin sethelpertoken | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-sethelpertoken
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin sethelpertoken command, which sets the current command prompt's primary token (or an arbitrary local user account's token, if specified) as a BITS transfer job's helper token.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2019-03-01T00:00:00.0000000Z
locale: en-us
document_id: a99dc4fd-4432-110d-5a23-c7106ab0b226
document_version_independent_id: 9babd2e3-2e90-0862-0336-f31f591ada65
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-sethelpertoken.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-sethelpertoken
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-sethelpertoken.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d8fad3e6-1676-49ef-b73b-c40a8d0c18af
---

# bitsadmin sethelpertoken | Microsoft Learn

Sets the current command prompt's primary token (or an arbitrary local user account's token, if specified) as a BITS transfer job's [helper token](/en-us/windows/win32/bits/helper-tokens-for-bits-transfer-jobs).

Note

This command isn't supported by BITS 3.0 and earlier.

## Syntax

```
bitsadmin /sethelpertoken <job> [<user_name@domain> <password>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| `<username@domain>``<password>` | Optional. The local user account credentials for which token to use. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)