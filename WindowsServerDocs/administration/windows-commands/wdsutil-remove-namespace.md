---
layout: Conceptual
title: wdsutil remove-namespace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-remove-namespace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil remove-namespace, which removes a custom namespace.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 04b0be20-ac40-8d50-a41b-eff2e34f5f92
document_version_independent_id: 1dd0deb2-7f45-d8a0-65ce-f03160daabd1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-remove-namespace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-remove-namespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-remove-namespace.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e4e6e639-49c9-b503-a63d-c1c320759025
---

# wdsutil remove-namespace | Microsoft Learn

Removes a custom namespace.

## Syntax

```
wdsutil /remove-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/force]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /Namespace:&lt;Namespace name&gt; | Specifies the name of the namespace. This is not the friendly name, and it must be unique.<br>- **Deployment Server role service**: The syntax for namespace name is /Namespace:WDS:&lt;ImageGroup&gt;/&lt;ImageName&gt;/&lt;Index&gt;. For example: **WDS:ImageGroup1/install.wim/1**- **Transport Server role service**: This value must match the name given to the namespace when it was created on the server. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |
| [/force] | removes the namespace immediately and terminates all clients. Note that unless you specify **/force**, existing clients can complete the transfer, but new clients are not able to join. |

## Examples

To stop a namespace (current clients can complete the transfer but new clients are not able to join), type:

```
wdsutil /remove-Namespace /Namespace:Custom Auto 1
```

To force termination of all clients, type:

```
wdsutil /remove-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /force
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-allnamespaces command](wdsutil-get-allnamespaces)
- [wdsutil new-namespace command](wdsutil-new-namespace)
- [wdsutil start-namespace command](wdsutil-start-namespace)