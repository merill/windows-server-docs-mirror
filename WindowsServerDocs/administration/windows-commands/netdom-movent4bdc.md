---
layout: Conceptual
title: Netdom movent4bdc | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netdom-movent4bdc
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Netdom movent4bdc is a command-line utility that renames a Windows NT 4.0 backup domain controller in Windows Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-09T00:00:00.0000000Z
locale: en-us
document_id: 0214a5e7-babb-53a1-eb88-b5083f04619a
document_version_independent_id: 0214a5e7-babb-53a1-eb88-b5083f04619a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netdom-movent4bdc.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netdom-movent4bdc
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netdom-movent4bdc.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: d3c70f39-0b35-65e9-1d83-7ddd7b7bd29e
---

# Netdom movent4bdc | Microsoft Learn

The `netdom movent4bdc` command renames a Windows NT 4.0 backup domain controller (DC). It's available if you have the Active Directory Domain Services (AD DS) server role installed. It's also available if you install the AD DS tools that are part of the Remote Server Administration Tools (RSAT). To use `netdom movent4bdc`, you must run the command from an elevated command prompt.

This command is specific to legacy Windows Server operating systems.

## Syntax

```
netdom movent4bdc machine [/Domain:domain] [/Reboot[:Time in seconds]]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<machine>` | Specifies the name of the backup DC that you want to rename. |
| `/domain:<Domain>` | Specifies the new name of the domain. |
| `/reboot:<seconds>` | Shuts down the computer and automatically reboots after the move operation completes. The *seconds* value is the number of seconds before automatic shutdown. The default is **20** seconds. |
| `help` | `/?` | Displays help at the command prompt. |

## Examples

To rename **OldBDC** to **NewBDC** for the domain **reskita**, run the following command:

```cmd
netdom movent4bdc oldbdc newbdc /domain:reskita
```