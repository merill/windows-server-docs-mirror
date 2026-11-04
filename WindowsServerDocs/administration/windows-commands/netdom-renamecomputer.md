---
layout: Conceptual
title: netdom renamecomputer | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netdom-renamecomputer
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Netdom renamecomputer is a command-line utility that renames a domain workstation or member server in Windows Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-09T00:00:00.0000000Z
locale: en-us
document_id: f630f576-59f9-54b8-3b97-d9e1ac981706
document_version_independent_id: f630f576-59f9-54b8-3b97-d9e1ac981706
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netdom-renamecomputer.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netdom-renamecomputer
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netdom-renamecomputer.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b257540d-975f-8cf6-1067-3288c113bdd7
---

# netdom renamecomputer | Microsoft Learn

The `netdom renamecomputer` command renames a domain workstation or member server and its corresponding domain account. It's available if you have the Active Directory Domain Services (AD DS) server role installed. It's also available if you install the AD DS tools that are part of the Remote Server Administration Tools (RSAT). For more information, see [How to Administer Microsoft Windows Client and Server Computers Locally and Remotely](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee649281%28v=ws.10%29).

To use `netdom renamecomputer`, you must run the command from an elevated command prompt.

## Syntax

```
netdom renamecomputer machine /NewName:new-name
                              [/UserD:user [/PasswordD:[password | *]]]
                              [/UserO:user [/PasswordO:[password | *]]]
                              [/Force] [/Reboot[:Time in seconds]]
                              [/SecurePasswordPrompt]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<machine>` | Specifies the name of the computer that you want to rename. |
| `/newname:<NewComputerName>` | Specifies the new name of the computer. |
| `/userd:<User>` | Specifies the user account that you want to use for the destination domain. |
| `/passwordd:<Password>` | `*` | Specifies the password of the user account that you specify using the `/userd` parameter. If you specify the value of this parameter as a wildcard character (`*`), this parameter prompts you for the password. |
| `/usero:<User>` | Specifies the user account that you want to use for the originating domain. |
| `/passwordo:<Password>` | `*` | Specifies the password of the user account that you specify using the `/usero` parameter. If you specify the value of this parameter as a wildcard character (`*`), this parameter prompts you for the password. |
| `/force` | When the `/force` parameter is specified, you aren't prompted for confirmation to rename a device. |
| `/reboot:<seconds>` | Shuts down the computer and automatically reboots after the move operation completes. The *seconds* value is the number of seconds before automatic shutdown. The default is **20** seconds. |
| `/securepasswordprompt` | Opens a secure credentials popup for entering credentials. This is useful when specifying smartcard credentials. This option is effective only when the password is entered as `*`. |
| `help` | `/?` | Displays help at the command prompt. |

Note

Don't use the `netdom renamecomputer` command to rename an AD DS domain controller (DC). Doing so Might cause the DC to no longer function as a DC on the network. Instead, use the `netdom computername` command.

## Examples

To rename the member server **MyServer** to **MyNewServer**, run the following command:

```cmd
netdom renamecomputer MyServer /newname:MyNewServer
```

If you don't have the appropriate permissions, the `/userd` and `/passwordd` parameters must be specified.