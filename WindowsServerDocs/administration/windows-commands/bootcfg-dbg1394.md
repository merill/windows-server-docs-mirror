---
layout: Conceptual
title: bootcfg dbg1394 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bootcfg-dbg1394
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bootcfg dbg1394 command, which configures 1394 port debugging for a specified operating system entry
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9f904674-9c14-f220-1af3-b36d77418379
document_version_independent_id: 2bf84731-acb0-8c8c-64fe-cdd9b90b185a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bootcfg-dbg1394.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bootcfg-dbg1394
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bootcfg-dbg1394.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4213f53a-01f2-1601-7116-a4e7aa02e5d9
---

# bootcfg dbg1394 | Microsoft Learn

Configures 1394 port debugging for a specified operating system entry.

## Syntax

```
bootcfg /dbg1394 {on | off}[/s <computer> [/u <domain>\<user> /p <password>]] [/ch <channel>] /id <osentrylinenum>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `{on | off}` | Specifies the value for 1394 port debugging, including:<br>- **on.** Enables remote debugging support by adding the /dbg1394 option to the specified `<osentrylinenum>`.<br>- **off.** Disables remote debugging support by removing the /dbg1394 option from the specified `<osentrylinenum>`. |
| `/s <computer>` | Specifies the name or IP address of a remote computer (don't use backslashes). The default is the local computer. |
| `/u <domain>\<user>` | Runs the command with the account permissions of the user specified by `<user>` or `<domain>\<user>`. The default is the permissions of the current logged on user on the computer issuing the command. |
| `/p <password>` | Specifies the password of the user account that is specified in the **/u** parameter. |
| `/ch <channel>` | Specifies the channel to use for debugging. Valid values include integers, between 1 and 64. Don't use this parameter if 1394 port debugging is disabled. |
| `/id <osentrylinenum>` | Specifies the operating system entry line number in the [operating systems] section of the Boot.ini file to which the operating system load options are added. The first line after the [operating systems] section header is 1. |
| /? | Displays help at the command prompt. |

## Examples

To use the **bootcfg /dbg1394**command:

```
bootcfg /dbg1394 /id 2
bootcfg /dbg1394 on /ch 1 /id 3
bootcfg /dbg1394 edit /ch 8 /id 2
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /dbg1394 off /id 2
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bootcfg command](bootcfg)