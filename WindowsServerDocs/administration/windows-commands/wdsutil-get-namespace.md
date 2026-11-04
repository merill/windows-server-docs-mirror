---
layout: Conceptual
title: wdsutil get-namespace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-namespace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil get-namespace, which displays information about a custom namespace.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b412c169-7b28-519d-319f-14716c16e20b
document_version_independent_id: 5d19a454-bb28-1825-9b56-fac9270bd3d2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-namespace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-namespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-namespace.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9e0fa196-0085-e8ff-5542-1415198838fa
---

# wdsutil get-namespace | Microsoft Learn

Displays information about a custom namespace.

## Syntax

Windows Server 2008 R2

```
wdsutil /Get-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/Show:Clients]
```

Windows Server 2008 R2

```
wdsutil /Get-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/details:Clients]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /Namespace:&lt;Namespace name&gt; | Specifies the name of the namespace. Note that this is not the friendly name, and it must be unique.<br>- Deployment Server: The syntax for namespace name is /Namspace:WDS:&lt;ImageGroup&gt;/&lt;ImageName&gt;/&lt;Index&gt;. For example: **WDS:ImageGroup1/install.wim/1**- Transport Server: This value should match the name given to the namespace when it was created on the server. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |
| [/Show:Clients] or [/details:Clients] | Displays information about client computers that are connected to the specified namespace. |

## Examples

To view information about a namespace, type:

```
wdsutil /Get-Namespace /Namespace:Custom Auto 1
```

To view information about a namespace and the clients that are connected, type one of the following:

- Windows Server 2008: `wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /Show:Clients`
- Windows Server 2008 R2: `wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /details:Clients`

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-allnamespaces command](wdsutil-get-allnamespaces)
- [wdsutil new-namespace command](wdsutil-new-namespace)
- [wdsutil remove-namespace command](wdsutil-remove-namespace)
- [wdsutil start-namespace command](wdsutil-start-namespace)