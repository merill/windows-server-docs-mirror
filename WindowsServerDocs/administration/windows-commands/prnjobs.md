---
layout: Conceptual
title: prnjobs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/prnjobs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the prnjobs command, which pauses, resumes, cancels, and lists print jobs.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: dc1686c0-049e-40b1-1631-38c2430d430d
document_version_independent_id: 40032167-287e-b14e-e466-3a4ce98b2eb7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/prnjobs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/prnjobs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/prnjobs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e895482f-f520-5036-8823-de339be1fa15
---

# prnjobs | Microsoft Learn

Pauses, resumes, cancels, and lists print jobs. This command is a Visual Basic script located in the `%WINdir%\System32\printing_Admin_Scripts\<language>` directory. To use this command at a command prompt, type **cscript** followed by the full path to the prnjobs file, or change directories to the appropriate folder. For example: `cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prnjobs.vbs`.

## Syntax

```
cscript prnjobs {-z | -m | -x | -l | -?} [-s <Servername>] [-p <Printername>] [-j <JobID>] [-u <Username>] [-w <password>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -z | Pauses the print job specified by the **-j** parameter. |
| -m | Resumes the print job specified by the **-j** parameter. |
| -x | Cancels the print job specified by the **-j** parameter. |
| -l | Lists all the print jobs in a print queue. |
| -s `<Servername>` | Specifies the name of the remote computer that hosts the printer that you want to manage. If you don't specify a computer, the local computer is used. |
| -p `<Printername>` | Required. Specifies the name of the printer that you want to manage. |
| -j `<JobID>` | Specifies (by ID number) the print job you want to cancel. |
| -u `<Username>` -w `<password>` | Specifies an account with permissions to connect to the computer that hosts the printer that you want to manage. All members of the target computer's local Administrators group have these permissions, but the permissions can also be granted to other users. If you don't specify an account, you must be logged on under an account with these permissions for the command to work. |
| /? | Displays help at the command prompt. |

#### Remarks

- If the information that you supply contains spaces, use quotation marks around the text (for example, "Computer Name").

### Examples

To pause a print job with a job ID of 27 sent to the remote computer named HRServer for printing on the printer named colorprinter, type:

```
cscript prnjobs.vbs -z -s HRServer -p colorprinter -j 27
```

To list all current print jobs in the queue for the local printer named colorprinter\_2, type:

```
cscript prnjobs.vbs -l -p colorprinter_2
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Print Command Reference](print-command-reference)