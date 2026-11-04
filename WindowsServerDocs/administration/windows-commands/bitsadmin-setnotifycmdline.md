---
layout: Conceptual
title: bitsadmin setnotifycmdline | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setnotifycmdline
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setnotifycmdline command, which sets the command-line command that will run when the job finishes transferring data, or when a job enters a state.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 59bf2df8-def3-fb31-50b7-b09f42e05d6f
document_version_independent_id: 6d4f03f9-f8b3-2c6c-4652-280fd1299c43
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setnotifycmdline.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setnotifycmdline
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setnotifycmdline.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 554c7dcd-35ab-1259-14a2-3d4d259d3a56
---

# bitsadmin setnotifycmdline | Microsoft Learn

Sets the command-line command that runs after the job finishes transferring data or after a job enters a specified state.

Note

This command isn't supported by BITS 1.2 and earlier.

## Syntax

```
bitsadmin /setnotifycmdline <job> <program_name> [program_parameters]
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| program\_name | Name of the command to run when the job completes. You can set this value as NULL, but if you do, *program\_parameters* must also be set to NULL. |
| program\_parameters | Parameters that you want to pass to *program\_name*. You can set this value as NULL. If *program\_parameters* isn't set to NULL, then the first parameter in *program\_parameters* must match the *program\_name*. |

## Examples

To run Notepad.exe at the completion of the job named *myDownloadJob*:

```
bitsadmin /setnotifycmdline myDownloadJob c:\winnt\system32\notepad.exe NULL
```

To show the EULA text in Notepad.exe, at the completion of the job named myDownloadJob:

```
bitsadmin /setnotifycmdline myDownloadJob c:\winnt\system32\notepad.exe notepad c:\eula.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)