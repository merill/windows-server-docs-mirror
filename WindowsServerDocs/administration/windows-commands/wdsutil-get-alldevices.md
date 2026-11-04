---
layout: Conceptual
title: wdsutil get-alldevices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-alldevices
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil get-alldevices command, which displays the Windows Deployment Services properties of all pre-staged computers.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 5bb67822-0681-3cf3-39e6-8d9068f96650
document_version_independent_id: 586fa9a8-2822-423a-720d-1da9c551c5d4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-alldevices.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-alldevices
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-alldevices.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 10e9d3d6-3def-3c87-9745-2d026074dedf
---

# wdsutil get-alldevices | Microsoft Learn

Displays the Windows Deployment Services properties of all pre-staged computers. A pre-staged computer is a physical computer that has been linked to a computer account in active directory Domain Services.

## Syntax

```
wdsutil [options] /get-alldevices [/forest:{Yes | No}] [/referralserver:<servername>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[/forest:{Yes | No}]` | Specifies whether Windows Deployment Services should return computers in the entire forest or the local domain. The default setting is **No**, meaning that only the computers in the local domain are returned. |
| `[/referralserver:<servername>]` | Returns only those computers that are pre-staged for the specified server. |

## Examples

To view all computers, type either:

```
wdsutil /get-alldevices
```

```
wdsutil /verbose /get-alldevices /forest:Yes /referralserver:MyWDSServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil set-device command](wdsutil-set-device)
- [wdsutil add-device command](wdsutil-add-device)
- [wdsutil get-device command](wdsutil-get-device)