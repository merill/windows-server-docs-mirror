---
layout: Conceptual
title: move | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/move
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the move command, which moves one or more files from one directory to another directory.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-08-15T00:00:00.0000000Z
locale: en-us
document_id: 8ed20aad-3112-c2cc-466f-48e09a1854f1
document_version_independent_id: 708cccea-201e-3a10-dd6b-815d7c6ec1ec
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/move.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/move
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/move.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: 42e2d241-ebb1-01ce-3b3d-92e737b5e2fa
---

# move | Microsoft Learn

Moves one or more files from one directory to another directory.

Important

Moving encrypted files to a volume that doesn't support Encrypting File System (EFS) results in an error. You must first decrypt the files or move them to a volume that supports EFS.

## Syntax

```
move [{/y|-y}] [<source>] [<target>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /y | Stops prompting for confirmation that you want to overwrite an existing destination file. This parameter might be preset in the COPYCMD environment variable. You can override this preset by using the **/-y** parameter. The default is to prompt before overwriting files, unless the command is run from within a batch script. |
| /-y | Starts prompting for confirmation that you want to overwrite an existing destination file. |
| `<source>` | Specifies the path and name of the file or files to move. To move or rename a directory, the *source* should be the current directory path and name. |
| `<target>` | Specifies the path and name to move files to. To move or rename a directory, the *target* should be the desired directory path and name. |
| /? | Displays help at the command prompt. |

### Examples

To move all files with the .xls extension from the *\Data* directory to the *\Second\_Q\Reports* directory, type:

```
move \data\*.xls \second_q\reports\
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)