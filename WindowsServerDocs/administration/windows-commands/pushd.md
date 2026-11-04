---
layout: Conceptual
title: pushd | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pushd
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pushd command, which stores the current directory for use by the popd command, and then changes to the specified directory.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 8476ea49-b196-7010-88f1-0c199b7cec41
document_version_independent_id: 320776d9-13d3-a1af-12b9-5066535e6871
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pushd.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pushd
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pushd.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fd97e7b1-9ce3-ae5c-c6f7-0f84301a55a1
---

# pushd | Microsoft Learn

Stores the current directory for use by the **popd** command, and then changes to the specified directory.

Every time you use the **pushd** command, a single directory is stored for your use. However, you can store multiple directories by using the **pushd** command multiple times. The directories are stored sequentially in a virtual stack, so if you use the **pushd** command once, the directory in which you use the command is placed at the bottom of the stack. If you use the command again, the second directory is placed on top of the first one. The process repeats every time you use the **pushd** command.

If you use the **popd** command, the directory on the top of the stack is removed and the current directory is changed to that directory. If you use the **popd** command again, the next directory on the stack is removed. If command extensions are enabled, the **popd** command removes any drive-letter assignment created by the **pushd** command.

## Syntax

```
pushd [<path>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<path>` | Specifies the directory to make the current directory. This command supports relative paths. |
| /? | Displays help at the command prompt. |

#### Remarks

- If command extensions are enabled, the **pushd** command accepts either a network path or a local drive letter and path.
- If you specify a network path, the **pushd** command temporarily assigns the highest unused drive letter (starting with Z:) to the specified network resource. The command then changes the current drive and directory to the specified directory on the newly assigned drive. If you use the **popd** command with command extensions enabled, the **popd** command removes the drive-letter assignment created by **pushd**.

### Examples

To change the current directory from the one in which the batch program was run, and then to change it back:

```
@echo off
rem This batch file deletes all .txt files in a specified directory
pushd %1
del *.txt
popd
cls
echo All text files deleted in the %1 directory
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [popd command](popd)