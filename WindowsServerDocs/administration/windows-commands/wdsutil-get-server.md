---
layout: Conceptual
title: wdsutil get-server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil get-server, which retrieves information from the specified Windows Deployment Services server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 1552f451-0c84-0c66-5964-c84ac808e2fd
document_version_independent_id: 00c59478-5c1c-2021-cd52-7f724777b591
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 280318a7-b578-7ed1-03e1-a2003370bd87
---

# wdsutil get-server | Microsoft Learn

Retrieves information from the specified Windows Deployment Services server.

## Syntax

```
wdsutil [Options] /Get-Server [/Server:<Server name>] /Show:{Config | Images | All} [/detailed]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |
| /Show:{Config | Images | All} | Specifies the type of information to return.<br>- **Config** returns configuration information.- **Images** returns information about image groups, boot images, and install images.- **All** returns configuration information and image information. |
| [/detailed] | You can use this option with **/Show:Images** or **/Show:All** to indicate that all image metadata from each image should be returned. If the **/detailed** option is not used, the default behavior is to return the image name, description, and file name. |

## Examples

To view information about the server, type:

```
wdsutil /Get-Server /Show:Config
```

To view detailed information about the server, type:

```
wdsutil /verbose /Get-Server /Server:MyWDSServer /Show:All /detailed
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil disable-server command](wdsutil-disable-server)
- [wdsutil enable-server command](wdsutil-enable-server)
- [wdsutil initialize-server command](wdsutil-initialize-server)
- [wdsutil set-server command](wdsutil-set-server)
- [wdsutil start-server command](wdsutil-start-server)
- [wdsutil stop-server command](wdsutil-stop-server)
- [wdsutil uninitialize-server command](wdsutil-uninitialize-server)