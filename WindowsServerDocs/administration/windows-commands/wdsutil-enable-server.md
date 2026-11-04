---
layout: Conceptual
title: wdsutil enable-server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-enable-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil enable-server command, which enables all services for Windows Deployment Services.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 401fa207-0c88-0ae0-37fc-969443362ed1
document_version_independent_id: a0c37e25-d452-fc0d-bf24-8400172e1e52
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-enable-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-enable-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-enable-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: eef91ee1-ae56-b271-a3ac-ccc588f13d9f
---

# wdsutil enable-server | Microsoft Learn

Enables all services for Windows Deployment Services.

## Syntax

```
wdsutil [options] /Enable-Server [/Server:<Servername>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:`<Servername>`] | Specifies the name of the server. This can be the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |

## Examples

To enable the services on the server, type either:

```
wdsutil /Enable-Server
```

```
wdsutil /verbose /Enable-Server /Server:MyWDSServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil disable-server command](wdsutil-disable-server)
- [wdsutil get-Server command](wdsutil-get-server)
- [wdsutil initialize-server command](wdsutil-initialize-server)
- [wdsutil set-server command](wdsutil-set-server)
- [wdsutil start-server command](wdsutil-start-server)
- [wdsutil stop-server command](wdsutil-stop-server)
- [wdsutil uninitialize-server command](wdsutil-uninitialize-server)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)