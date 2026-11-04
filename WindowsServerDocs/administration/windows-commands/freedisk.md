---
layout: Conceptual
title: freedisk | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/freedisk
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the freedisk command, which checks to see if the specified amount of disk space is available before continuing with an installation process.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 792e81a9-2f64-37b0-b0ed-e03b6b508e45
document_version_independent_id: ce82042b-0663-da95-214d-28ab726afb68
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/freedisk.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/freedisk
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/freedisk.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: b5c5d622-b036-de2a-f728-2e0538672c44
---

# freedisk | Microsoft Learn

Checks to see if the specified amount of disk space is available before continuing with an installation process.

## Syntax

```
freedisk [/s <computer> [/u [<domain>\]<user> [/p [<password>]]]] [/d <drive>] [<value>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /s `<computer>` | Specifies the name or IP address of a remote computer (do not use backslashes). The default is the local computer. This parameter applies to all files and folders specified in the command. |
| /u [`<domain>`\]`<user>` | Runs the script with the permissions of the specified user account. The default is system permissions. |
| /p [`<password>`] | Specifies the password of the user account that is specified in **/u**. |
| /d `<drive>` | Specifies the drive for which you want to find out the availability of free space. You must specify `<drive>` for a remote computer. |
| `<value>` | Checks for a specific amount of free disk space. You can specify `<value>` in bytes, KB, MB, GB, TB, PB, EB, ZB, or YB. |

#### Remarks

- Using the **/s**, **/u**, and **/p** command-line options are available only when you use **/s**. You must use **/p** with **/u**to provide the user's password.
- For unattended installations, you can use **freedisk** in installation batch files to check for the prerequisite amount free space before continuing with the installation.
- When you use **freedisk** in a batch file, it returns a **0** if there's enough space and a **1** if there's not enough space.

### Examples

To determine whether there are at least 50 MB of free space available on drive C, type:

```
freedisk 50mb
```

Output similar to the following example appears on the screen:

```
INFO: The specified 52,428,800 byte(s) of free space is available on current drive.
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)