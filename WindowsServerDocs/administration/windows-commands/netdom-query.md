---
layout: Conceptual
title: Netdom query | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netdom-query
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Netdom query is a command-line utility that retrieves information from a domain about its membership and trust relationships in Windows Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-09T00:00:00.0000000Z
locale: en-us
document_id: 5ccc6384-2507-9b86-3aeb-3d54a2c0b376
document_version_independent_id: 5ccc6384-2507-9b86-3aeb-3d54a2c0b376
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netdom-query.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netdom-query
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netdom-query.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 8f13e696-7008-1268-fca0-1f7a758f29a1
---

# Netdom query | Microsoft Learn

The `netdom query` command retrieves information from a domain about its membership and trust relationships. It's available if you have the Active Directory Domain Services (AD DS) server role installed. It's also available if you install the AD DS tools that are part of the Remote Server Administration Tools (RSAT). For more information, see [How to Administer Microsoft Windows Client and Server Computers Locally and Remotely](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee649281%28v=ws.10%29).

To use `netdom query`, you must run the command from an elevated command prompt.

## Syntax

```
netdom query [/Domain:domain] [/Server:server]
             [/UserD:user] [/PasswordD:[password | *]]
             [/Verify] [/Reset] [/Direct] [/SecurePasswordPrompt]
             WORKSTATION | SERVER | DC | OU | PDC | FSMO | TRUST
```

## Parameters

| Parameter | Description |
| --- | --- |
| `/domain:<Domain>` | Specifies the domain to query for information. If you don't specify this parameter, then `netdom query` uses the domain to which the current computer belongs. |
| `/server:<Server>` | Specifies the name of the domain controller that performs the query. |
| `/userd:<User>` | Specifies the user account that makes the connection with the domain that you specify using the `/domain` parameter. If you don't specify this parameter, `netdom query` uses the current user account. |
| `/passwordd:<Password>` | `*` | Specifies the password of the user account that you specify using the `/userd` parameter. If you specify the value of this parameter as a wildcard character (`*`), this parameter prompts you for the password. |
| `/verify` | Verifies the secure channel secrets for all listed memberships or trusts and displays the results. Only outbound trusts are verified. Domain administrator credentials are required for accurate verification. |
| `/reset` | Specifies resynchronization of the secure channel secrets for all enumerated memberships or trusts that are currently broken. Domain administrator credentials are required to reset all enumerated trusts or memberships. |
| `/direct` | Indicates that the query for trust relationships returns only direct trust relationships, rather than direct and indirect relationships. This parameter can't be used with the `/verify` parameter. |
| `/securepasswordprompt` | Opens a secure credentials popup for entering credentials. This is useful when specifying smartcard credentials. This option is effective only when the password is entered as `*`. |
| `workstation` | `server` | `dc` | `ou` | `pdc` | `fsmo` | `trust` | Specifies the type of list to generate. The following list shows the possible objects:- **Workstation**: Queries the domain for the list of workstations.- **Server**: Queries the domain for the list of servers.- **DC**: Queries the domain for the list of domain controllers.- **OU**: Queries the domain for the list of OUs under which the user that you specify can create a computer object.- **PDC**: Queries the domain for the current primary domain controller.- **FSMO**: Queries the domain for the current list of flexible single master operations (FSMO) role owners. - **Trust**: Queries the domain for the list of its trusts. |
| `help` | `/?` | Displays help at the command prompt. |

## Examples

To list all the *servers* in the domain **NorthAmerica**, run the following command:

```cmd
netdom query /domain:NorthAmerica SERVER
```

To list all servers and verify the secure channel secret in the domain **NorthAmerica**, run the following command:

```cmd
netdom query /domain:NorthAmerica SERVER /verify
```

To list all the direct trust relationships for the domain **NorthAmerica**, run the following command:

```cmd
netdom query /domain:NorthAmerica /Direct TRUST
```