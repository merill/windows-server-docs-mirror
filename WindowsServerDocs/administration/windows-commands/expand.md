---
layout: Conceptual
title: expand | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/expand
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the expand command, which expands one or more compressed files.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-11-01T00:00:00.0000000Z
locale: en-us
document_id: d352c588-1b3d-dd0d-0d8b-b7761eae861f
document_version_independent_id: a2e41711-2938-19a5-8bee-34ff2081b17c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/expand.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/expand
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/expand.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6d7821bb-4771-698b-98e1-b0df1aa3e3f5
---

# expand | Microsoft Learn

> 
> Applies to: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Expands one or more compressed files. You can also use this command to retrieve compressed files from distribution disks.

The **expand** command can also run from the Windows Recovery Console, using different parameters. For more information, see [Windows Recovery Environment (WinRE)](/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference).

## Syntax

```
expand [-r] <source> <destination>
expand -r <source> [<destination>]
expand -i <source> [<destination>]
expand -d <source>.cab [-f:<files>]
expand <source>.cab -f:<files> <destination>
```

### Parameters

| Parameter | Description |
| --- | --- |
| -r | Renames expanded files. |
| source | Specifies the files to expand. *Source* can consist of a drive letter and colon, a directory name, a file name, or a combination of these. You can use wildcards (**\*** or **?**). |
| destination | Specifies where files are to be expanded.<br>If *source* consists of multiple files and you don't specify **-r**, the *destination* must be a directory that already exists. *Destination* can consist of a drive letter and colon, a directory name, a file name, or a combination of these. Destination `file \| path` specification. |
| -i | Renames expanded files but ignores the directory structure. |
| -d | Displays a list of files in the source location. Doesn't expand or extract the files. |
| -f:`<files>` | Specifies the files in a cabinet (.cab) file that you want to expand. You can use wildcards (**\*** or **?**). |
| /? | Displays help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)