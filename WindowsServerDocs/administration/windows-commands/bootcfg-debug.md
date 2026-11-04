---
layout: Conceptual
title: bootcfg debug | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bootcfg-debug
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bootcfg debug command, which adds or changes the debug settings for a specified operating system entry.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 3210cab9-c6ba-22bd-f698-ac9d35915ecc
document_version_independent_id: c4a5c907-0e3f-9dbc-c52a-0f051ac7fb8c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bootcfg-debug.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bootcfg-debug
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bootcfg-debug.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bed8d526-7da6-3e7c-eafa-062601308206
---

# bootcfg debug | Microsoft Learn

Adds or changes the debug settings for a specified operating system entry.

Note

If you're attempting to debug port 1394, use the [bootcfg dbg1394](bootcfg-dbg1394) command instead.

## Syntax

```
bootcfg /debug {on | off | edit}[/s <computer> [/u <domain>\<user> /p <password>]] [/port {COM1 | COM2 | COM3 | COM4}] [/baud {9600 | 19200 | 38400 | 57600 | 115200}] [/id <osentrylinenum>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `{on | off | edit}` | Specifies the value for port debugging, including:<br>- **on.** Enables remote debugging support by adding the /debug option to the specified `<osentrylinenum>`.<br>- **off.** Disables remote debugging support by removing the /debug option from the specified `<osentrylinenum>`.<br>- **edit.** Allows changes to port and baud rate settings by changing the values associated with the /debug option for the specified `<osentrylinenum>`. |
| `/s <computer>` | Specifies the name or IP address of a remote computer (don't use backslashes). The default is the local computer. |
| `/u <domain>\<user>` | Runs the command with the account permissions of the user specified by `<user>` or `<domain>\<user>`. The default is the permissions of the current logged on user on the computer issuing the command. |
| `/p <password>` | Specifies the password of the user account that is specified in the **/u** parameter. |
| `/port {COM1 | COM2 | COM3 | COM4}` | Specifies the COM port to be used for debugging. Don't use this parameter if debugging is disabled. |
| `/baud {9600 | 19200 | 38400 | 57600 | 115200}` | Specifies the baud rate to be used for debugging. Don't use this parameter if debugging is disabled. |
| `/id <osentrylinenum>` | Specifies the operating system entry line number in the [operating systems] section of the Boot.ini file to which the operating system load options are added. The first line after the [operating systems] section header is 1. |
| /? | Displays help at the command prompt. |

## Examples

To use the **bootcfg /debug** command:

```
bootcfg /debug on /port com1 /id 2
bootcfg /debug edit /port com2 /baud 19200 /id 2
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /debug off /id 2
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bootcfg command](bootcfg)