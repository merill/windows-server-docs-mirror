---
layout: Conceptual
title: Netdom remove | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netdom-remove
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Netdom remove is a command-line utility that removes a workstation or server from a domain in Windows Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-09T00:00:00.0000000Z
locale: en-us
document_id: 43d746e8-5696-606f-a6e0-907516f2c57e
document_version_independent_id: 43d746e8-5696-606f-a6e0-907516f2c57e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netdom-remove.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netdom-remove
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netdom-remove.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: eed35459-316e-a303-e15c-c8771cbfedbd
---

# Netdom remove | Microsoft Learn

The `netdom remove` command removes a workstation or server from a domain. It's available if you have the Active Directory Domain Services (AD DS) server role installed. It's also available if you install the AD DS tools that are part of the Remote Server Administration Tools (RSAT). For more information, see [How to Administer Microsoft Windows Client and Server Computers Locally and Remotely](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee649281%28v=ws.10%29).

To use `netdom remove`, you must run the command from an elevated command prompt.

## Syntax

```
netdom remove machine [/Domain:domain] [/UserD:user]
                      [/PasswordD:[password | *]]
                      [/UserO:user] [/PasswordO:[password | *]]
                      [/Reboot[:Time in seconds]] [/Force]
                      [/SecurePasswordPrompt]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<machine>` | Specifies the name of the computer that you want to remove. |
| `/domain:<Domain>` | Specifies the domain from which you want to remove the computer. If not specified, `netdom remove` uses the domain that the current computer belongs to. |
| `/userd:<User>` | Specifies the user account that makes the connection with the domain specified using the `/domain` parameter. If not specified, uses the current user account. |
| `/passwordd:<Password>` | `*` | Specifies the password of the user account specified using the `/userd` parameter. If set to `*`, you're prompted for the password. |
| `/usero:<User>` | Specifies the user account to make the connection with the computer you want to remove. If not specified, uses the current user account. |
| `/passwordo:<Password>` | `*` | Specifies the password of the user account specified using the `/usero` parameter. If set to `*`, you're prompted for the password. |
| `/reboot:<seconds>` | Shuts down the computer and automatically reboots after the move operation completes. The *seconds* value is the number of seconds before automatic shutdown. The default is **20** seconds. |
| `/securepasswordprompt` | Opens a secure credentials popup for entering credentials. This is useful when specifying smartcard credentials. This option is effective only when the password is entered as `*`. |
| `help` | `/?` | Displays help at the command prompt. |

## Examples

To remove **mywksta** from the **MyDomain** domain, run the following command:

```cmd
netdom remove mywksta /domain:MyDomain /userd:MyDomain\admin /passwordd:*
```