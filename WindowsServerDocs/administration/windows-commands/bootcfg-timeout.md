---
layout: Conceptual
title: bootcfg timeout | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bootcfg-timeout
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bootcfg timeout command, which changes the operating system time-out value.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4c3d638a-e39d-1a15-4be0-130386cb0d05
document_version_independent_id: 4f39a2d1-68e4-bbff-49be-0ff9964c0624
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bootcfg-timeout.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bootcfg-timeout
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bootcfg-timeout.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d6b856c7-d0cf-5b20-102a-d58b46b0d9e5
---

# bootcfg timeout | Microsoft Learn

Changes the operating system time-out value.

## Syntax

```
bootcfg /timeout <timeoutvalue> [/s <computer> [/u <domain>\<user> /p <password>]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `/timeout <timeoutvalue>` | Specifies the timeout value in the [boot loader] section. The `<timeoutvalue>` is the number of seconds the user has to select an operating system from the boot loader screen before NTLDR loads the default. The valid range for `<timeoutvalue>` is 0-999. If the value is 0, NTLDR immediately starts the default operating system without displaying the boot loader screen. |
| `/s <computer>` | Specifies the name or IP address of a remote computer (don't use backslashes). The default is the local computer. |
| `/u <domain>\<user>` | Runs the command with the account permissions of the user specified by `<user>` or `<domain>\<user>`. The default is the permissions of the current logged on user on the computer issuing the command. |
| `/p <password>` | Specifies the password of the user account that is specified in the **/u** parameter. |
| /? | Displays help at the command prompt. |

## Examples

To use the **bootcfg /timeout** command:

```
bootcfg /timeout 30
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /timeout 50
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bootcfg command](bootcfg)