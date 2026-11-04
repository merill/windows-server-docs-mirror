---
layout: Conceptual
title: Netdom move | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netdom-move
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Netdom move is a command-line utility moves a workstation or member server to a new domain in Windows Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-09T00:00:00.0000000Z
locale: en-us
document_id: 72fe0c4f-0dde-8fce-540b-c12c3be269a8
document_version_independent_id: 72fe0c4f-0dde-8fce-540b-c12c3be269a8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netdom-move.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netdom-move
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netdom-move.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e9f8396c-997c-0567-2d60-9d27ae03b486
---

# Netdom move | Microsoft Learn

The `netdom move` command moves a workstation or member server to a new domain. The act of moving a computer to a new domain creates an account for the computer on the domain, if it doesn't already exist. It's available if you have the Active Directory Domain Services (AD DS) server role installed. It's also available if you install the AD DS tools that are part of the Remote Server Administration Tools (RSAT). To use `netdom move`, you must run the command from an elevated command prompt.

## Syntax

```
netdom move machine /Domain:domain [/OU:ou path]
                    [/UserD:user] [/PasswordD:[password | *]]
                    [/UserO:user] [/PasswordO:[password | *]]
                    [/UserF:user] [/PasswordF:[password | *]]
                    [/Reboot[:Time in seconds]]
                    [/SecurePasswordPrompt]
```

## Parameters

Note

When you move a computer to a new domain, `netdom move` doesn't delete its computer account in the former domain. However, if you supply credentials for the former domain, this command disables the old computer account.

| Parameter | Description |
| --- | --- |
| `<machine>` | Specifies the name of the computer that you want to move. |
| `/domain:<Domain>` | Specifies the domain to which you want to move the account. If you don't specify the parameter, then `netdom move` uses the domain to which the current computer belongs. |
| `/ou:<OUPath>` | Specifies the organizational unit (OU) under which to create the account. This must be the full [RFC 1779](https://www.rfc-editor.org/rfc/rfc1779) distinguished name of the OU. If you don't specify this parameter, `netdom move` creates the account under the default OU for computer objects for that domain. |
| `/userd:<User>` | Specifies the user account that makes the connection with the domain that you specify using the `/domain` parameter. If you don't specify this parameter, `netdom move` uses the current user account. |
| `/passwordd:<Password>` | `*` | Specifies the password of the user account that you specify using the `/userd` parameter. If you specify the value of this parameter as a wildcard character (`*`), this parameter prompts you for the password. |
| `/usero:<User>` | Specifies the user account to make the connection with the computer that you want to move. If you don't specify this parameter, `netdom move` uses the current user account. |
| `/passwordo:<Password>` | `*` | Specifies the password of the user account that you specify using the `/usero` parameter. If you specify the value of this parameter as a wildcard character (`*`), this parameter prompts you for the password. |
| `/userf:<User>` | Specifies the user account to make the connection with the computer's former domain (of which the computer was a member before the move). This parameter is used to disable the old computer account. |
| `/passwordf:<Password>` | `*` | Specifies the password of the user account that you specify using the `/userf` parameter. If you specify the value of this parameter as a wildcard character (`*`), this parameter prompts you for the password. |
| `/reboot:<seconds>` | Shuts down the computer and automatically reboots after the move operation completes. The *seconds* value is the number of seconds before automatic shutdown. The default is **20** seconds. |
| `/securepasswordprompt` | Opens a secure credentials popup for entering credentials. This is useful when specifying smartcard credentials. This option is effective only when the password is entered as `*`. |
| `help` | `/?` | Displays help at the command prompt. |

## Examples

To move **mywksta** from its current domain into the **MyDomain** domain, run the following command:

```cmd
netdom move mywksta /domain:mydomain /userd:mydomain\admin /passwordd:*
```

If the destination is an AD DS domain, this command updates the Security ID history for the workstation, retaining the security permissions that the computer account had previously.

To move **Srv01** to the domain **NewDomain** and specify the OU, run the following command:

```cmd
netdom move svr01 /domain:newdomain /ou:"OU=Workstations,OU=Resources,DC=NewDomain,DC=local" /userd:NewDomain\DomainAdmin /passwordd:*
```