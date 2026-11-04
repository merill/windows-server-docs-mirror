---
layout: Conceptual
title: flattemp | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/flattemp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the flattemp command, which enables or disables flat temporary folders.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 2a74673b-3f8b-08f0-9508-6aa31ab38b54
document_version_independent_id: 3805508c-341a-8987-2601-0d2dc9684bb3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/flattemp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/flattemp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/flattemp.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f49c4dc0-4c8b-b66b-27e8-1a15bf6579d4
---

# flattemp | Microsoft Learn

Enables or disables flat temporary folders. You must have administrative credentials to run this command.

Note

This command is only available if you have installed the Remote Desktop Session Host role service.

## Syntax

```
flattemp {/query | /enable | /disable}
```

### Parameters

| Parameter | Description |
| --- | --- |
| /query | Queries the current setting. |
| /enable | Enables flat temporary folders. Users will share the temporary folder unless the temporary folder resides in the user's home folder. |
| /disable | Disables flat temporary folders. Each user's temporary folder will reside in a separate folder (determined by the user's Session ID). |
| /? | Displays help at the command prompt. |

#### Remarks

- After each user has a unique temporary folder, use `flattemp /enable` to enable flat temporary folders.
- The default method for creating temporary folders for multiple users (usually pointed to by the TEMP and TMP environment variables) is to create subfolders in the **\Temp** folder, by using the logonID as the subfolder name. For example, if the TEMP environment variable points to C:\Temp, the temporary folder assigned to the user logonID 4 is C:\Temp\4.

    Using **flattemp**, you can point directly to the \Temp folder and prevent subfolders from forming. This is useful when you want the user temporary folders to be contained in home folders, whether on an Remote Desktop Session Host server local drive or on a shared network drive. You should use the `flattemp /enable*` command only when each user has a separate temporary folder.
- You might encounter app errors if the user's temporary folder is on a network drive. This occurs when the shared network drive becomes momentarily inaccessible on the network. Because the temporary files of the app are either inaccessible or out of synchronization, it responds as if the disk has stopped. Moving the temporary folder to a network drive is not recommended. The default is to keep temporary folders on the local hard disk. If you experience unexpected behavior or disk-corruption errors with certain applications, stabilize your network or move the temporary folders back to the local hard disk.
- If you disable using separate temporary folders per-session, **flattemp** settings are ignored. This option is set in the Remote Desktop Services Configuration tool.

### Examples

To display the current setting for flat temporary folders, type:

```
flattemp /query
```

To enable flat temporary folders, type:

```
flattemp /enable
```

To disable flat temporary folders, type:

```
flattemp /disable
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)