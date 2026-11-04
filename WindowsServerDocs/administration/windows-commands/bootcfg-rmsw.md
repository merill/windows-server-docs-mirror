---
layout: Conceptual
title: bootcfg rmsw | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bootcfg-rmsw
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bootcfg rmsw command, which removes operating system load options for a specified operating system entry.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ddab153b-f269-e6da-2126-8a7781eb0d4e
document_version_independent_id: 05daa7cd-c605-8eab-ef92-72ae51c62f10
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bootcfg-rmsw.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bootcfg-rmsw
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bootcfg-rmsw.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b54991b2-53f4-71d8-740e-252133b49b35
---

# bootcfg rmsw | Microsoft Learn

Removes operating system load options for a specified operating system entry.

## Syntax

```
bootcfg /rmsw [/s <computer> [/u <domain>\<user> /p <password>]] [/mm] [/bv] [/so] [/ng] /id <osentrylinenum>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `/s <computer>` | Specifies the name or IP address of a remote computer (don't use backslashes). The default is the local computer. |
| `/u <domain>\<user>` | Runs the command with the account permissions of the user specified by `<user>` or `<domain>\<user>`. The default is the permissions of the current logged on user on the computer issuing the command. |
| `/p <password>` | Specifies the password of the user account that is specified in the **/u** parameter. |
| /mm | Removes the /maxmem option and its associated maximum memory value from the specified `<osentrylinenum>`. The /maxmem option specifies the maximum amount of RAM that the operating system can use. |
| /bv | Removes the /basevideo option from the specified `<osentrylinenum>`. The /basevideo option directs the operating system to use standard VGA mode for the installed video driver. |
| /so | Removes the /sos option from the specified `<osentrylinenum>`. The /sos option directs the operating system to display device driver names while they are being loaded. |
| /ng | Removes the /noguiboot option from the specified `<osentrylinenum>`. The /noguiboot option disables the progress bar that appears before the CTRL+ALT+DEL logon prompt. |
| `/id <osentrylinenum>` | Specifies the operating system entry line number in the [operating systems] section of the Boot.ini file to which the operating system load options are added. The first line after the [operating systems] section header is 1. |
| /? | Displays help at the command prompt. |

## Examples

To use the **bootcfg /rmsw** command:

```
bootcfg /rmsw /mm 64 /id 2
bootcfg /rmsw /so /id 3
bootcfg /rmsw /so /ng /s srvmain /u hiropln /id 2
bootcfg /rmsw /ng /id 2
bootcfg /rmsw /mm 96 /ng /s srvmain /u maindom\hiropln /p p@ssW23 /id 2
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bootcfg command](bootcfg)