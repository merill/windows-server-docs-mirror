---
layout: Conceptual
title: Netdom reset | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netdom-reset
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Netdom reset is a command-line utility that resets the secure connection between a workstation and a domain controller in Windows Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-09T00:00:00.0000000Z
locale: en-us
document_id: 88080e83-2969-75b4-43e3-1d6898a75709
document_version_independent_id: 88080e83-2969-75b4-43e3-1d6898a75709
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netdom-reset.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netdom-reset
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netdom-reset.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: b2cf304c-4039-36ec-cd0b-2baf3728559b
---

# Netdom reset | Microsoft Learn

The `netdom reset` command resets the secure connection between a workstation and a domain controller (DC). It's available if you have the Active Directory Domain Services (AD DS) server role installed. It's also available if you install the AD DS tools that are part of the Remote Server Administration Tools (RSAT). For more information, see [How to Administer Microsoft Windows Client and Server Computers Locally and Remotely](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee649281%28v=ws.10%29).

To use `netdom reset`, you must run the command from an elevated command prompt.

## Syntax

```
netdom reset machine [/Domain:domain] [/Server:server]
                     [/UserO:user] [/PasswordO:[password | *]] [/SecurePasswordPrompt]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<machine>` | Specifies the name of the computer whose secure connection you want to reset. |
| `/domain:<Domain>` | Specifies the domain with which to establish the secure connection. If not specified, `netdom reset` uses the domain to which the current computer belongs. |
| `/server:<Server>` | Specifies the DC to use to establish the secure connection. |
| `/usero:<User>` | Specifies the user account to use to make the secure connection with the computer that you want to reset. If not specified, `netdom reset` uses the current user account. |
| `/passwordo:<Password>` | `*` | Specifies the password of the user account specified using the `/usero` parameter. If you use the wildcard character (`*`), you're prompted for the password. |
| `/securepasswordprompt` | Opens a secure credentials popup for entering credentials. This is useful when specifying smartcard credentials. This option is effective only when the password is entered as `*`. |
| `help` | `?` | Displays help at the command prompt. |

## Examples

To reset the secure channel secret that is maintained between **mywksta** and **devgroup.contoso.com**, run the following command:

```cmd
netdom reset mywksta /domain:devgroup.contoso.com
```

To reset the secure channel between the primary DC for **NorthAmerica** and the backup DC **BackupDC**, run the following command:

```cmd
netdom reset BackupDC /domain:NorthAmerica
```

Member servers frequently establish secure channel sessions with DCs that aren't local to their site. To force a secure channel session between member server **mywksta** and a specific DC, **MyOtherDC**, run the following command:

```cmd
netdom reset mywksta /domain:MyDomain.contoso.com /Server:MyOtherDC
```