---
layout: Conceptual
title: popd | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/popd
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pnputil command, which changes the current directory to the directory that was most recently stored by the pushd command.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: 0e303089-d9a0-d5bb-329b-97aa7f4988e9
document_version_independent_id: 9d34c2f7-dde3-f8dc-004d-e2b0ae610f2f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/popd.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/popd
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/popd.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1758ccfb-8141-5c07-0ff2-a3c5a83bc7d1
---

# popd | Microsoft Learn

The **popd** command changes the current directory to the directory that was most recently stored by the **pushd** command.

Every time you use the **pushd** command, a single directory is stored for your use. However, you can store multiple directories by using the **pushd** command multiple times. The directories are stored sequentially in a virtual stack, so if you use the **pushd** command once, the directory in which you use the command is placed at the bottom of the stack. If you use the command again, the second directory is placed on top of the first one. The process repeats every time you use the **pushd** command.

If you use the **popd** command, the directory on the top of the stack is removed and the current directory is changed to that directory. If you use the **popd** command again, the next directory on the stack is removed. If command extensions are enabled, the **popd** command removes any drive-letter assignments created by the **pushd** command.

## Syntax

```
popd
```

### Parameters

| Parameter | Description |
| --- | --- |
| /? | Displays help at the command prompt. |

### Examples

To change the current directory from the one in which the batch program was run, and then to change it back, type:

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
- [pushd](pushd)