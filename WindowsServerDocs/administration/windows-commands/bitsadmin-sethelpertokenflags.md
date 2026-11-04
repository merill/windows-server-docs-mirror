---
layout: Conceptual
title: bitsadmin sethelpertokenflags | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-sethelpertokenflags
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin sethelpertokenflags command, which sets the usage flags for a helper token that is associated with a BITS transfer job.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2019-03-01T00:00:00.0000000Z
locale: en-us
document_id: 8aea95f4-5e57-6f6e-5f3c-4f3c5fcd39b0
document_version_independent_id: c62ca477-1a22-a6e1-6d67-df085aa4af0b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-sethelpertokenflags.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-sethelpertokenflags
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-sethelpertokenflags.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 780ddbad-7239-968f-1131-a170dcf66848
---

# bitsadmin sethelpertokenflags | Microsoft Learn

Sets the usage flags for a [helper token](/en-us/windows/win32/bits/helper-tokens-for-bits-transfer-jobs) that is associated with a BITS transfer job.

Note

This command isn't supported by BITS 3.0 and earlier.

## Syntax

```
bitsadmin /sethelpertokenflags <job> <flags>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| flags | Possible helper token values, including:<br>- **0x0001.** Used to open the local file of an upload job, to create or rename the temporary file of a download job, or to create or rename the reply file of an upload-reply job.<br>- **0x0002.** Used to open the remote file of a Server Message Block (SMB) upload or download job, or in response to an HTTP server or proxy challenge for implicit NTLM or Kerberos credentials.<br><br>You must call `/setcredentialsjob targetscheme null null` to send the credentials over HTTP. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)