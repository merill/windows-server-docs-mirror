---
layout: Conceptual
title: chkntfs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/chkntfs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the chkntfs command, which displays or modifies automatic disk checking when the computer is started.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e065da8b-35dd-8326-0fa0-703e3dd4b020
document_version_independent_id: 1ac484da-ee67-9d5b-e01b-7d5f60ee8506
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/chkntfs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/chkntfs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/chkntfs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 48ab14cc-0d63-faa0-204c-7099d555c1cf
---

# chkntfs | Microsoft Learn

Displays or modifies automatic disk checking when the computer is started. If used without options, **chkntfs** displays the file system of the specified volume. If automatic file checking is scheduled to run, **chkntfs** displays whether the specified volume is dirty or is scheduled to be checked the next time the computer is started.

Note

To run **chkntfs**, you must be a member of the Administrators group.

## Syntax

```
chkntfs <volume> [...]
chkntfs [/d]
chkntfs [/t[:<time>]]
chkntfs [/x <volume> [...]]
chkntfs [/c <volume> [...]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<volume>` [...] | Specifies one or more volumes to check when the computer starts. Valid volumes include drive letters (followed by a colon), mount points, or volume names. |
| /d | Restores all **chkntfs** default settings, except the countdown time for automatic file checking. By default, all volumes are checked when the computer is started, and **chkdsk** runs on those that are dirty. |
| /t [`:<time>`] | Changes the Autochk.exe initiation countdown time to the amount of time specified in seconds. If you do not enter a time, **/t** displays the current countdown time. |
| /x `<volume>` [...] | Specifies one or more volumes to exclude from checking when the computer is started, even if the volume is marked as requiring **chkdsk**. |
| /c `<volume>` [...] | Schedules one or more volumes to be checked when the computer is started, and runs **chkdsk** on those that are dirty. |
| /? | Displays help at the command prompt. |

## Examples

To display the type of file system for drive C, type:

```
chkntfs c:
```

Note

If automatic file checking is scheduled to run, additional output will display, indicating whether the drive is dirty or has been manually scheduled to be checked the next time the computer is started.

To display the Autochk.exe initiation countdown time, type:

```
chkntfs /t
```

To change the Autochk.exe initiation countdown time to 30 seconds, type:

```
chkntfs /t:30
```

Note

Although you can set the Autochk.exe initiation countdown time to zero, doing so will prevent you from canceling a potentially time-consuming automatic file check.

To exclude multiple volumes from being checked, you must list each of them in a single command. For example, to exclude both the D and E volumes, type:

```
chkntfs /x d: e:
```

Important

The **/x** command-line option isn't accumulative. If you type it more than once, the most recent entry overrides the previous entry.

To schedule automatic file checking on the D volume, but not the C or E volumes, type the following commands in order:

```
chkntfs /d
chkntfs /x c: d: e:
chkntfs /c d:
```

Important

The **/c** command-line option is accumulative. If you type **/c** more than once, each entry remains. To ensure that only a particular volume is checked, reset the defaults to clear all previous commands, exclude all volumes from being checked, and then schedule automatic file checking on the desired volume.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)