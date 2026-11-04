---
layout: Conceptual
title: wdsutil get-transportserver | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-transportserver
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil get-transportserver, which displays information about a specified Transport Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: da19413e-1a99-7711-3807-bdba9d6a7d4c
document_version_independent_id: 02d4cc25-8590-c9c6-419d-a0f9aa2779c5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-transportserver.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-transportserver
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-transportserver.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2011f805-6167-a163-d3a5-7709383d4061
---

# wdsutil get-transportserver | Microsoft Learn

Displays information about a specified Transport Server.

## Syntax

```
wdsutil [Options] /Get-TransportServer [/Server:<Server name>] /Show:{Config}
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| /Show:{Config} | Returns configuration information about the specified Transport Server. |

## Examples

To view information about the server, type:

```
wdsutil /Get-TransportServer /Show:Config
```

To view configuration information, type:

```
wdsutil /Get-TransportServer /Server:MyWDSServer /Show:Config
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil disable-transportserver command](wdsutil-disable-transportserver)
- [wdsutil enable-transportserver command](wdsutil-enable-transportserver)
- [wdsutil set-transportserver command](wdsutil-set-transportserver)
- [wdsutil start-transportserver command](wdsutil-start-transportserver)
- [wdsutil stop-transportserver command](wdsutil-stop-transportserver)