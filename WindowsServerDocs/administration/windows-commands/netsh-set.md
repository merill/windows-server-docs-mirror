---
layout: Conceptual
title: netsh set | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-set
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh set command targets local or remote devices to perform network configuration tasks in Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-29T00:00:00.0000000Z
locale: en-us
document_id: c703d109-fe2c-6931-f36f-df6e484e55fb
document_version_independent_id: c703d109-fe2c-6931-f36f-df6e484e55fb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-set.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-set
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-set.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c8b772c7-70a2-932d-3dde-2694cc043669
---

# netsh set | Microsoft Learn

The `netsh set` command allows administrators to specify the target machine for subsequent network configuration tasks, enabling operations on either local or remote systems. If a machine name isn't specified, the local machine is used. A username and password can't be used to connect to the local machine.

## Syntax

```
netsh set machine [name=]<string> [user=][[DomainName\]UserName] [pwd=][Password | *]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<name>` | Specifies the device name or network address of the machine on which you want to perform actions. |
| `<user>` | Provides the username credentials required to authenticate and connect to the remote machine. If your network uses a domain, specify the username in the format `DomainName\UserName`. |
| `<pwd>` | Supplies the password associated with the specified user account. If you enter an asterisk (`*`) instead of a password, you're prompted to input the password interactively for added security. |

## Examples

To specify a target machine using its IP address in a domain environment where the password is prompted, run the following command:

```cmd
netsh set machine name=192.168.1.10 user=DOMAIN\Admin pwd=*
```