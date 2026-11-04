---
layout: Conceptual
title: Netdom resetpwd | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netdom-resetpwd
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Netdom resetpwd is a command-line utility that resets the computer account password for a domain controller in Windows Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-09T00:00:00.0000000Z
locale: en-us
document_id: ca9bc2b0-033f-9d63-a022-165af620aa3d
document_version_independent_id: ca9bc2b0-033f-9d63-a022-165af620aa3d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netdom-resetpwd.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netdom-resetpwd
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netdom-resetpwd.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 1ac47df6-9d20-5fc9-6ee7-8cd91ba18d8b
---

# Netdom resetpwd | Microsoft Learn

The `netdom resetpwd` command resets the secure channel password of the machine account for a domain controller (DC). This command must be run on the DC whose machine account password you wish to reset. It doesn't support resetting passwords for remote machines or member servers. It's available if you have the Active Directory Domain Services (AD DS) server role installed. It's also available if you install the AD DS tools that are part of the Remote Server Administration Tools (RSAT).

For more information, see [How to Administer Microsoft Windows Client and Server Computers Locally and Remotely](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee649281%28v=ws.10%29).

To use `netdom resetpwd`, you must run the command from an elevated command prompt.

## Syntax

```
netdom resetpwd /Server:domain-controller /UserD:user /PasswordD:[password | *]
                [/SecurePasswordPrompt]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `/server:<DC>` | Specifies the DC to use to set the computer account password. |
| `/userd:<User>]` | Specifies the user account to use to make the secure connection with the domain specified using the `/server` parameter. If omitted, it uses the current user account. |
| `/passwordd:<Password>` | `*` | Specifies the password for the user account when using the `/userd` parameter. If set to `*`, you're prompted for the password. |
| `/securepasswordprompt` | Opens a secure credentials popup for entering credentials. This is useful when specifying smartcard credentials. This option is effective only when the password is entered as `*`. |
| `help` | `/?` | Displays help at the command prompt. |

## Examples

To reset the secure channel password for a computer account associated with the DC **MyDC** and be securely prompted for the password, run the following command:

```
netdom resetpwd /server:MyDC /userd:admin /passwordd:*
```