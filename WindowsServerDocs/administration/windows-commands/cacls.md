---
layout: Conceptual
title: cacls | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/cacls
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the cacls command. This command has been deprecated and isn't guaranteed to be supported in future releases of Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a259ded6-6d3a-a1de-5af0-732dac079000
document_version_independent_id: f8fdf643-0878-9edf-fcd7-05f602edcbe2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/cacls.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/cacls
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/cacls.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ee3bf64f-6ae7-6aa4-fabe-90ffe96180dc
---

# cacls | Microsoft Learn

Important

This command has been deprecated. Please use [icacls](icacls) instead.

Displays or modifies discretionary access control lists (DACL) on specified files.

## Syntax

```
cacls <filename> [/t] [/m] [/l] [/s[:sddl]] [/e] [/c] [/g user:<perm>] [/r user [...]] [/p user:<perm> [...]] [/d user [...]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<filename>` | Required. Displays ACLs of specified files. |
| /t | Changes ACLs of specified files in the current directory and all subdirectories. |
| /m | Changes ACLs of volumes mounted to a directory. |
| /l | Works on the Symbolic Link itself instead of the target. |
| /s:sddl | Replaces the ACLs with those specified in the SDDL string. This parameter is not valid for use with the **/e**, **/g**, **/r**, **/p**, or **/d** parameters. |
| /e | Edit an ACL instead of replacing it. |
| /c | Continue after access denied errors. |
| `/g user:<perm>` | Grants specified user access rights, including these valid values for permission:<br>- **n** - None<br>- **r** - Read<br>- **w** - Write<br>- **c** - Change (write)<br>- **f** - Full control |
| /r user [...] | Revoke specified user's access rights. Only valid when used with the **/e** parameter. |
| `[/p user:<perm> [...]` | Replace specified user's access rights, including these valid values for permission:<br>- **n** - None<br>- **r** - Read<br>- **w** - Write<br>- **c** - Change (write)<br>- **f** - Full control |
| [/d user [...] | Deny specified user access. |
| /? | Displays help at the command prompt. |

#### Sample output

| Output | Access control entry (ACE) applies to |
| --- | --- |
| OI | Object inherit. This folder and files. |
| CI | Container inherit. This folder and subfolders. |
| IO | Inherit only. The ACE does not apply to the current file/directory. |
| No output message | This folder only. |
| (OI)(CI) | This folder, subfolders, and files. |
| (OI)(CI)(IO) | Subfolders and files only. |
| (CI)(IO) | Subfolders only. |
| (OI)(IO) | Files only. |

#### Remarks

- You can use wildcards (**?** and **\***) to specify multiple files.
- You can specify more than one user.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [icacls](icacls)