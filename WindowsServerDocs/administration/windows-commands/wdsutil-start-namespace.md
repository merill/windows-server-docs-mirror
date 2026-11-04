---
layout: Conceptual
title: wdsutil start-namespace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-start-namespace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for Subcommand start-Namespace, which starts a Scheduled-Cast namespace.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 65d76d42-b006-771b-6c84-73f95c7ce168
document_version_independent_id: 6315e036-9e1b-f167-28af-4df574c071f2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-start-namespace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-start-namespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-start-namespace.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8e4c992f-52f0-7888-cc44-1c6c96f55e82
---

# wdsutil start-namespace | Microsoft Learn

Starts a Scheduled-Cast namespace.

## Syntax

```
wdsutil /start-Namespace /Namespace:<Namespace name[/Server:<Server name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /Namespace:&lt;Namespace name&gt; | Specifies the name of the namespace. Note that this is not the friendly name, and it must be unique.<br>- **Deployment Server**: The syntax for namespace name is /Namspace:WDS:&lt;Image group&gt;/&lt;Image name&gt;/&lt;Index&gt;. For example: **WDS:ImageGroup1/install.wim/1**- **Transport Server**: This name must match the name given to the namespace when it was created on the server. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |

## Examples

To start a namespace, type one of the following:

```
wdsutil /start-Namespace /Namespace:Custom Auto 1
wdsutil /start-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-allnamespaces command](wdsutil-get-allnamespaces)
- [wdsutil new-namespace command](wdsutil-new-namespace)
- [wdsutil remove-namespace command](wdsutil-remove-namespace)