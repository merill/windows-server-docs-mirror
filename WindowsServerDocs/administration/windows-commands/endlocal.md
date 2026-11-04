---
layout: Conceptual
title: endlocal | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/endlocal
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the endlocal command, which ends localization of environment changes in a batch file, and restores environment variables to their values before the corresponding setlocal command was run.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f6d54014-f78f-8546-f26a-c28bcff11330
document_version_independent_id: 75dda616-a8db-2946-81e2-7a18bfac7746
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/endlocal.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/endlocal
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/endlocal.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 85c61e51-db03-9438-cec3-e9834ed3ec2b
---

# endlocal | Microsoft Learn

Ends localization of environment changes in a batch file, and restores environment variables to their values before the corresponding **setlocal** command was run.

## Syntax

```
endlocal
```

### Parameters

| Parameter | Description |
| --- | --- |
| /? | Displays help at the command prompt. |

#### Remarks

- The **endlocal** command has no effect outside a script or batch file.
- There is an implicit **endlocal** command at the end of a batch file.
- If command extensions are enabled (command extensions are enabled by default), the **endlocal** command restores the state of command extensions (that is, enabled or disabled) to what it was before the corresponding **setlocal** command was run.

Note

For more information about enabling and disabling command extensions, see the [Cmd command](cmd).

### Examples

You can localize environment variables in a batch file. For example, the following program starts the *superapp* batch program on the network, directs the output to a file, and displays the file in Notepad:

```
@echo off
setlocal
path=g:\programs\superapp;%path%
call superapp>c:\superapp.out
endlocal
start notepad c:\superapp.out
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)