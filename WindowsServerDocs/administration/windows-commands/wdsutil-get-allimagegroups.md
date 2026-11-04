---
layout: Conceptual
title: wdsutil get-allimagegroups | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-allimagegroups
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil get-allimagegroups command, which retrieves information about all image groups on a server and all images in those image groups.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 35ac0b0b-ae4c-dab8-590b-b04035759289
document_version_independent_id: 1f5d2983-9ff2-696c-648c-516453c944d1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-allimagegroups.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-allimagegroups
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-allimagegroups.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 91094645-e381-f988-821c-1483d89cb97d
---

# wdsutil get-allimagegroups | Microsoft Learn

Retrieves information about all image groups on a server and all images in those image groups.

## Syntax

```
wdsutil [options] /get-allimagegroups [/server:<servername>] [/detailed]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[/server:<servername>]` | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |
| [/detailed] | Returns the image metadata from each image. If this parameter isn't used, the default behavior is to return only the image name, description, and file name for each image. |

## Examples

To view information about the image groups, type either:

```
wdsutil /get-allimagegroups
```

```
wdsutil /verbose /get-allimagegroups /server:MyWDSServer /detailed
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-imagegroup command](wdsutil-add-imagegroup)
- [wdsutil remove-imagegroup command](wdsutil-remove-imagegroup)
- [wdsutil set-imagegroup command](wdsutil-set-imagegroup)