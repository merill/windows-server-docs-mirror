---
layout: Conceptual
title: Netdom join | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netdom-join
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Netdom is a command-line utility that joins a workstation or member server to a domain in Windows Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-09T00:00:00.0000000Z
locale: en-us
document_id: 0d84f9f5-9472-63f0-bb23-261dcad94cee
document_version_independent_id: 0d84f9f5-9472-63f0-bb23-261dcad94cee
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netdom-join.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netdom-join
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netdom-join.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 4c83f66a-ac65-3199-a366-7c26128ea785
---

# Netdom join | Microsoft Learn

The `netdom join` command joins a workstation or member server to a domain. The act of joining a computer to a domain creates an account for the computer on the domain, if it doesn't already exist. It's available if you have the Active Directory Domain Services (AD DS) server role installed. It's also available if you install the Active Directory Domain Services Tools that are part of the Remote Server Administration Tools (RSAT). For more information, see [How to Administer Microsoft Windows Client and Server Computers Locally and Remotely](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee649281%28v=ws.10%29).

To use `netdom join`, you must run the command from an elevated command prompt.

## Syntax

```
netdom join machine /Domain:domain [/OU:ou path] [/UserD:user]
                    [/PasswordD:[password | *]]
                    [/UserO:user] [/PasswordO:[password | *]]
                    [/PasswordM:[password | *]]
                    [/ReadOnly]
                    [/REBoot[:Time in seconds]]
                    [/SecurePasswordPrompt]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<machine>` | Specifies the name of the computer that you want to join to the domain. |
| `/domain:<Domain>` | Specifies the domain that you want to join the computer to. Using the Fully Qualified Domain Name (FQDN) format is recommended for clarity. If not specified, `netdom join` defaults to the domain to which the current computer belongs to. |
| `/ou:<OUPath>` | Specifies the organizational unit (OU) under which you want to create the account. You must specify the full [RFC 1779](https://www.rfc-editor.org/rfc/rfc1779) distinguished name of the OU. If not specified, `netdom join` creates the account under the default OU for computer objects for that domain. |
| `/userd:<Domain>\<User>` | Specifies the user account that makes the connection with the domain specified with the `/domain` parameter. If not specified, `netdom join` uses the current user account. |
| `/usero:<User>` | Specifies the user account that makes the connection with the computer you want to join to the domain. If not specified, `netdom join` uses the current user account. |
| `/passwordd:<Password>` | `*` | Specifies the password of the user account specified with the `/userd` parameter. If you specify `*`, you're prompted for the password. |
| `/passwordo:<Password>` | `*` | Specifies the password of the user account specified with the `/usero` parameter. If you specify `*`, you're prompted for the password. |
| `/passwordm:<Password>` | `*` | Specifies the password for the pre-created computer account identified by the machine name. If you specify `*` instead of a password, you're prompted for the password. This option must be used with the `/ReadOnly` parameter. |
| `/readonly` | Joins the domain using a pre-created computer account without writing to a domain controller. This doesn't require a writable domain controller. It must be used with the `/Domain` and `/PasswordM` parameters, and can't be used with the `/OU` parameter. |
| `/reboot:<seconds>` | Shuts down the computer and automatically reboots after the join operation completes. The *seconds* value is the number of seconds before automatic shutdown. The default is **20** seconds. |
| `/securepasswordprompt` | Opens a secure credentials popup for entering credentials. This is useful when specifying smartcard credentials. This option is effective only when the password is entered as `*`. |
| `help` | `/?` | Displays help at the command prompt. |

## Examples

To join the computer **mywksta** to the **devgroup.contoso.com** domain in the **Dsys/workstations** OU, run the following command:

```cmd
netdom join mywksta /domain:devgroup.contoso.com /OU:"OU=Workstations,OU=Dsys,DC=devgroup,DC=contoso,DC=com"
```

Besides adding the computer account to the domain, this command modifies the workstation to contain the appropriate shared secret to complete the *join* operation.

To join the computer **mywksta** to the domain **contoso.com**, run the following command:

```cmd
netdom join mywksta /domain:contoso.com /userd:user01 /passwordd:*
```

This command prompts you to enter the password for the domain user "user01" securely.