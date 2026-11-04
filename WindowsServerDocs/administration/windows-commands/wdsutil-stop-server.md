---
layout: Conceptual
title: wdsutil stop-server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-stop-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for Subcommand stop-Server, which stops all services on a Windows Deployment Services server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 3a42b23f-932d-2486-cb13-169ab08a8326
document_version_independent_id: c1af9e04-c6e3-78d4-3e13-e898bdad8d77
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-stop-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-stop-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-stop-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: a52d9c21-687f-f0be-a717-86ecec6ca181
---

# wdsutil stop-server | Microsoft Learn

Stops all services on a Windows Deployment Services server.

## Syntax

```
wdsutil [Options] /Stop-Server [/Server:<Server name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |

## Examples

To stop the services, type one of the following:

```
wdsutil /Stop-Server
wdsutil /verbose /Stop-Server /Server:MyWDSServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil disable-server command](wdsutil-disable-server)
- [wdsutil enable-server command](wdsutil-enable-server)
- [wdsutil get-server command](wdsutil-get-server)
- [wdsutil initialize-server command](wdsutil-initialize-server)
- [wdsutil set-server command](wdsutil-set-server)
- [wdsutil start-server command](wdsutil-start-server)
- [wdsutil uninitialize-server command](wdsutil-uninitialize-server)