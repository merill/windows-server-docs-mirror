---
layout: Conceptual
title: bitsadmin gethelpertokenflags | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-gethelpertokenflags
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin gethelpertokenflags command, which returns the usage flags for a helper token that is associated with a BITS transfer job.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2019-03-01T00:00:00.0000000Z
locale: en-us
document_id: 1cfaebbf-efd7-0fb0-e91b-1bcd54ca19f0
document_version_independent_id: 7a6b835b-a72b-0c63-e880-ee36c05a7191
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-gethelpertokenflags.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-gethelpertokenflags
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-gethelpertokenflags.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 215d4b6f-5ee4-a7e2-565a-0f09603adaa2
---

# bitsadmin gethelpertokenflags | Microsoft Learn

Returns the usage flags for a [helper token](/en-us/windows/win32/bits/helper-tokens-for-bits-transfer-jobs) that is associated with a BITS transfer job.

Note

This command isn't supported by BITS 3.0 and earlier.

## Syntax

```
bitsadmin /gethelpertokenflags <job>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |

### Remarks

Possible return values, including:

- **0x0001.** The helper token is used to open the local file of an upload job, to create or rename the temporary file of a download job, or to create or rename the reply file of an upload-reply job.
- **0x0002.** The helper token is used to open the remote file of a Server Message Block (SMB) upload or download job, or in response to an HTTP server or proxy challenge for implicit NTLM or Kerberos credentials. You must call `/SetCredentialsJob TargetScheme NULL NULL` to allow the credentials to be sent over HTTP.

## Examples

To retrieve the usage flags for a helper token associated with a BITS transfer job named *myDownloadJob*:

```
bitsadmin /gethelpertokenflags myDownloadJob
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)