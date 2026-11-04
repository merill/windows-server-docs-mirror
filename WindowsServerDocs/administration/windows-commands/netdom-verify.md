---
layout: Conceptual
title: Netdom verify | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netdom-verify
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Netdom verify is a command-line utility that verifies the secure channel between a specified computer and a domain controller in Windows Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-09T00:00:00.0000000Z
locale: en-us
document_id: c890fe03-7f27-2e80-50e2-9d7434df18e7
document_version_independent_id: c890fe03-7f27-2e80-50e2-9d7434df18e7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netdom-verify.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netdom-verify
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netdom-verify.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 61021146-a96a-f2ce-8e33-b883f2486f31
---

# Netdom verify | Microsoft Learn

The `netdom verify` command checks the secure channel between a specified computer and a domain controller to ensure trust and connectivity are intact. It's available if you have the Active Directory Domain Services (AD DS) server role installed. It's also available if you install the AD DS tools that are part of the Remote Server Administration Tools (RSAT). For more information, see [How to Administer Microsoft Windows Client and Server Computers Locally and Remotely](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee649281%28v=ws.10%29).

To use `netdom verify`, you must run the command from an elevated command prompt.

## Syntax

```
netdom verify machine [/Domain:domain] [/UserO:user] [/PasswordO:[password | *]] [/SecurePasswordPrompt]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<machine>` | Specifies the name of the computer whose secure connection you want to verify. |
| `/domain:<Domain>` | Specifies the domain with which to verify the secure connection. If not specified, `netdom verify` uses the domain to which the current computer belongs. |
| `/usero:<User>` | Specifies the user account to use for verification. If not specified, the current user account is used. |
| `/passwordo:<Password>` | `*` | Specifies the password for the user account specified used with the `/usero` parameter. If set to `*`, you're prompted for the password. |
| `/securepasswordprompt` | Opens a secure credentials popup for entering credentials. This is useful when specifying smartcard credentials. This option is effective only when the password is entered as `*`. |
| `help` | `/?` | Displays help at the command prompt. |

## Examples

To verify that netdom maintains the secure channel secret between **mywksta** and **devgroup.contoso.com**, run the following command:

```cmd
netdom verify mywksta /domain:devgroup.contoso.com
```