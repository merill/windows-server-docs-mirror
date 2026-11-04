---
layout: Conceptual
title: wdsutil enable-transportserver | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-enable-transportserver
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil enable-transportserver command, which enables all services for the Transport Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 71a24b61-531d-bb70-4bbb-5e3bc51cbb13
document_version_independent_id: 7ff168a7-5271-bbca-21ef-2cd3eb78185c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-enable-transportserver.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-enable-transportserver
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-enable-transportserver.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 208ec3d3-65ec-e51b-71e1-5779239a13e7
---

# wdsutil enable-transportserver | Microsoft Learn

Enables all services for the Transport Server.

## Syntax

```
wdsutil [options] /Enable-TransportServer [/Server:<Servername>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:`<Servername>`] | Specifies the name of the server. This can be the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |

## Examples

To enable the services on the server, type either:

```
wdsutil /Enable-TransportServer
```

```
wdsutil /verbose /Enable-TransportServer /Server:MyWDSServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil disable-transportserver command](wdsutil-disable-transportserver)
- [wdsutil get-transportserver command](wdsutil-get-transportserver)
- [wdsutil set-transportserver command](wdsutil-set-transportserver)
- [wdsutil start-transportserver command](wdsutil-start-transportserver)
- [wdsutil stop-transportserver command](wdsutil-stop-transportserver)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)