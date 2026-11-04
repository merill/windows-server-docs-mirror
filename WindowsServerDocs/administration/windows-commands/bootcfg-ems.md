---
layout: Conceptual
title: bootcfg ems | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bootcfg-ems
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bootcfg ems command, which enables the user to add or change the settings for redirection of the Emergency Management Services console to a remote computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b5036741-729c-61c8-818d-601ae12b3690
document_version_independent_id: aea77780-7a2c-b82c-2ac8-d86f9e5013b4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bootcfg-ems.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bootcfg-ems
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bootcfg-ems.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3f040eb6-a920-a296-bfcc-d24ffdc169f6
---

# bootcfg ems | Microsoft Learn

Enables the user to add or change the settings for redirection of the Emergency Management Services console to a remote computer. Enabling Emergency Management Services, adds a `redirect=Port#` line to the [boot loader] section of the Boot.ini file along with a /redirect option to the specified operating system entry line. The Emergency Management Services feature is enabled only on servers.

## Syntax

```
bootcfg /ems {on | off | edit}[/s <computer> [/u <domain>\<user> /p <password>]] [/port {COM1 | COM2 | COM3 | COM4 | BIOSSET}] [/baud {9600 | 19200 | 38400 | 57600 | 115200}] [/id <osentrylinenum>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `{on | off | edit}` | Specifies the value for Emergency Management Services redirection, including:<br>- **on.** Enables remote output for the specified `<osentrylinenum>`. Also adds a /redirect option to the specified `<osentrylinenum>` and a `redirect=com<X>` setting to the [boot loader] section. The value of `com<X>` is set by the **/port** parameter.<br>- **off.** Disables output to a remote computer. Also removes the /redirect option to the specified `<osentrylinenum>` and the `redirect=com<X>` setting from the [boot loader] section.<br>- **edit.** Allows changes to port settings by changing the `redirect=com<X>` setting in the [boot loader] section. The value of `com<X>` is set by the **/port** parameter. |
| `/s <computer>` | Specifies the name or IP address of a remote computer (don't use backslashes). The default is the local computer. |
| `/u <domain>\<user>` | Runs the command with the account permissions of the user specified by `<user>` or `<domain>\<user>`. The default is the permissions of the current logged on user on the computer issuing the command. |
| `/p <password>` | Specifies the password of the user account that is specified in the **/u** parameter. |
| `/port {COM1 | COM2 | COM3 | COM4 | BIOSSET}` | Specifies the COM port to be used for redirection. The BIOSSET parameter directs Emergency Management Services to get the BIOS settings to determine which port should be used for redirection. Don't use this parameter if remotely administered output is disabled. |
| `/baud {9600 | 19200 | 38400 | 57600 | 115200}` | Specifies the baud rate to be used for redirection. Don't use this parameter if remotely administered output is disabled. |
| `/id <osentrylinenum>` | Specifies the operating system entry line number to which the Emergency Management Services option is added in the [operating systems] section of the Boot.ini file. The first line after the [operating systems] section header is 1. This parameter is required when the Emergency Management Services value is set to **on** or **off**. |
| /? | Displays help at the command prompt. |

## Examples

To use the **bootcfg /ems** command:

```
bootcfg /ems on /port com1 /baud 19200 /id 2
bootcfg /ems on /port biosset /id 3
bootcfg /s srvmain /ems off /id 2
bootcfg /ems edit /port com2 /baud 115200
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /ems off /id 2
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bootcfg command](bootcfg)