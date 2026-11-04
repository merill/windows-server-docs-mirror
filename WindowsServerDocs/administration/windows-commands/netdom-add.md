---
layout: Conceptual
title: Netdom add | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netdom-add
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Netdom add is a command-line utility that adds a workstation or server account to a domain in Windows Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-09T00:00:00.0000000Z
locale: en-us
document_id: ae209906-b53f-00a7-1c99-5473896928ca
document_version_independent_id: ae209906-b53f-00a7-1c99-5473896928ca
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netdom-add.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netdom-add
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netdom-add.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f3f23660-0fe7-9c9e-f752-fd0ba11af89d
---

# Netdom add | Microsoft Learn

The `netdom add` command adds a workstation or server account to a domain. It's available if you have the Active Directory Domain Services (AD DS) server role installed. It's also available if you install the AD DS tools that are part of the Remote Server Administration Tools (RSAT). To use `netdom add`, you must run the command from an elevated command prompt.

## Syntax

```
netdom add machine [/Domain:domain] [/UserD:user] [/PasswordD:[password | *]]
                   [/Server:server] [/OU:ou path] [/DC] [/SecurePasswordPrompt]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<machine>` | Specifies the name of the computer that you want to add. |
| `/domain:<Domain>` | Specifies the domain in which to create the account. If you don't specify this parameter, then `netdom add` uses the domain that the current computer belongs to. |
| `/userd:<User>` | Specifies the user account that makes the connection with the domain that you specify using the `/domain` parameter. If you don't specify this parameter, `netdom add` uses the current user account. |
| `/passwordd:<Password>` | `*` | Specifies the password of the user account that you specify using the `/userd` parameter. If you specify the value of this parameter as a wildcard character (`*`), this parameter prompts you for the password. |
| `/server:<Server>` | Specifies the name of a domain controller that performs the *add* operation. This parameter can't be used with the `/ou` parameter. |
| `/ou:<OUPath>` | Specifies the organizational unit (OU) under which to create the account. You must use the full [RFC 1779](https://www.rfc-editor.org/rfc/rfc1779) distinguished name of the OU. If you don't specify this parameter, `netdom add` creates the account under the default OU for computer objects for that domain. |
| `/dc` | Specifies that a domain controller's machine account is to be created. This makes it possible for the computer accounts for new AD DS domain controllers. This parameter can't be used with the **/ou** parameter. |
| `/securepasswordprompt` | Opens a secure credentials popup for entering credentials. This is useful when specifying smartcard credentials. This option is effective only when the password is entered as `*`. |
| `help` | `/?` | Displays help at the command prompt. |

## Examples

To add the workstation **mywksta** to the domain **reskita** using the credentials of a domain administrator, run the following command:

```cmd
netdom add mywksta /domain:reskita /userd:domainadmin /passwordd:*
```

To add a computer named **Srv01** to the domain **reskita.com** and specify the organizational unit (OU) where the computer account should be placed, run the following command:

```cmd
netdom add Srv01 /domain:reskita /OU:"OU=Servers,DC=reskita,DC=com" /userd:domainadmin /passwordd:*
```

Note

If you don't specify the `/ou` parameter, `netdom add` creates the account in the **Computers** container.