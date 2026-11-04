---
layout: Conceptual
title: bitsadmin setaclflag | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setaclflag
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setaclflag command, which sets the access control list (ACL) propagations flags.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b3349a80-5a3a-a5d8-41c5-3159ec17a5b1
document_version_independent_id: 97a12f28-3b73-c39f-5dba-016a9f7b6a2e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setaclflag.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setaclflag
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setaclflag.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: da94ace6-623d-5942-b2f9-ec4323ec37cd
---

# bitsadmin setaclflag | Microsoft Learn

Sets the access control list (ACL) propagations flags for the job. The flags indicate that you want to maintain the owner and ACL information with the file being downloaded. For example, to maintain the owner and group with the file, set the **flags** parameter to `og`.

## Syntax

```
bitsadmin /setaclflag <job> <flags>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| flags | Specify one or more of the values, including:<br>- **o** - Copy owner information with file.<br>- **g** - Copy group information with file.<br>- **d** - Copy discretionary access control list (DACL) information with file.<br>- **s** - Copy system access control list (SACL) information with file. |

## Examples

To set the access control list propagation flags for the job named *myDownloadJob*, so it maintains the owner and group information with the downloaded files.

```
bitsadmin /setaclflags myDownloadJob og
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)