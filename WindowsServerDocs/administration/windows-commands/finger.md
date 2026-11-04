---
layout: Conceptual
title: finger | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/finger
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the finger command, which displays information about users on a specified remote computer running the finger service or daemon.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c5b8b320-68fd-8968-f83a-9fa3a19b9a5e
document_version_independent_id: c9161306-b9b9-5772-1fef-5472a2471a9a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/finger.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/finger
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/finger.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ca6e0856-63bd-93b0-0d70-0d5b9d68a1de
---

# finger | Microsoft Learn

Displays information about users on a specified remote computer (typically a computer running UNIX) that is running the finger service or daemon. The remote computer specifies the format and output of the user information display. Used without parameters, **finger** displays help.

Important

This command is available only if the Internet Protocol (TCP/IP) protocol is installed as a component in the properties of a network adapter in Network Connections.

## Syntax

```
finger [-l] [<user>] [@<host>] [...]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -l | Displays user information in long list format. |
| `<user>` | Specifies the user about which you want information. If you omit the *user* parameter, this command displays information about all users on the specified computer. |
| `@<host>` | Specifies the remote computer running the finger service where you are looking for user information. You can specify a computer name or IP address. |
| /? | Displays help at the command prompt. |

#### Remarks

- You must prefix **finger** parameters with a hyphen (-) rather than a slash (/).
- Multiple `user@host` parameters can be specified.

### Examples

To display information for *user1* on the computer *users.microsoft.com*, type:

```
finger user1@users.microsoft.com
```

To display information for *all users* on the computer *users.microsoft.com*, type:

```
finger @users.microsoft.com
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)