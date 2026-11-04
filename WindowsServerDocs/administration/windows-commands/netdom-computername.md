---
layout: Conceptual
title: Netdom computername | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netdom-computername
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Netdom computername is a command-line utility that manages the primary and alternate names for a computer in Windows Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-09T00:00:00.0000000Z
locale: en-us
document_id: 53762ad4-5e01-fa05-66e6-7a2a3fd8817a
document_version_independent_id: 53762ad4-5e01-fa05-66e6-7a2a3fd8817a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netdom-computername.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netdom-computername
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netdom-computername.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 0489eb6a-c393-007b-c7e3-f664d770472d
---

# Netdom computername | Microsoft Learn

The `netdom computername` command manages the primary and alternate names for a computer. This command can safely rename Active Directory (AD) domain controllers (DC) and member servers. It's available if you have the Active Directory Domain Services (AD DS) server role installed. It's also available if you install the AD DS tools that are part of the Remote Server Administration Tools (RSAT). To use `netdom computername`, you must run the command from an elevated command prompt.

## Syntax

```
netdom computername machine [/UserO:user] [/PasswordO:[password | *]]
                            [/UserD:user] [/PasswordD:[password | *]] [/SecurePasswordPrompt]
                            /Add:<new-alternate-DNS-name> | /Remove:<alternate-DNS-name>
                            /MakePrimary:<computer-dns-name>
                            /Enumerate[:{AlternateNames | PrimaryName | AllNames}]
                            /Verify
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<machine>` | Specifies the name of the computer that you want to manage. |
| `/usero:<UserName>` | Specifies the user account that you want to use for the originating domain. |
| `/passwordo:<Password>` | `*` | Specifies the password that you want to use for the originating domain. If you specify `*`, you're prompted for the password. |
| `/userd:<UserName>` | Specifies the user account that you want to use for the destination domain. |
| `/passwordd:<Password>` | `*` | Specifies the password that you want to use for the destination domain. If you specify `*`, you're prompted for the password. |
| `/securepasswordprompt` | Opens a secure credentials popup for entering credentials. This is useful when specifying smartcard credentials. This option is effective only when the password is entered as `*`. |
| `/add:<NewAltDNSName>` | Creates a new alternate name. Specify a fully qualified domain name (FQDN), such as `comp1.example.com`. |
| `/remove:<AltDNSName>` | Deletes an existing alternate name. Specify an FQDN, such as `comp1.example.com`. |
| `/makeprimary:<ComputerDNSName>` | Makes an existing alternate name into the primary name. Specify an FQDN, such as `comp1.example.com`. |
| `/enumerate:ALTERNATENAMES` | `PRIMARYNAME`| `ALLNAMES` | Lists the primary name or any alternate names. Values:- `ALTERNATENAMES`: Lists alternate names only.- `PRIMARYNAME`: Lists the primary name only.- `ALLNAMES`: Lists the primary and any alternate names (default). |
| `/verify` | Checks if there's a DNS record and a service principal name (SPN) for each computer name. |
| `help` | `/?` | Displays help at the command prompt. |

## Examples

To give an alternate name for the DC **MyDC** in the **mydomain.com** domain, run the following command:

```cmd
netdom computername mydc.mydomain.com /add:altDCname.mydomain.com
```

Before you can make an alternate name the primary name of a computer, the name must exist as an alternate name.

Once the alternate name is added, you can promote it to be the primary name. To rename the domain controller **MyDC** to **altDCname** in the **mydomain.com** domain, use the following command:

```cmd
netdom computername mydc.mydomain.com /makeprimary:altdcname.mydomain.com
```

When you rename a member server, the process is similar. Use an existing alternate name as the new primary name.