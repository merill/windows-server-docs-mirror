---
layout: Conceptual
title: get-AllServers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-allservers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for get-AllServers, which retrieves information about all Windows Deployment Services servers.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b17b8ce8-4090-2413-fb0b-7524c7917794
document_version_independent_id: 4da95f4c-1053-01ed-a813-eb3d61018efe
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-allservers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-allservers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-allservers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 10cfd148-7363-ec1b-108c-1de7a8d047ba
---

# get-AllServers | Microsoft Learn

Retrieves information about all Windows Deployment Services servers.

Note

This command may take an extended amount of time to complete if there are many Windows Deployment Services servers in your environment or if the network connection linking the servers is slow.

## Syntax

```
wdsutil [Options] /Get-AllServers /Show:{Config | Images | All} [/Detailed] [/Forest:{Yes | No}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /Show:{Config | Images |
| [/Detailed] | When used in conjunction with the **/Show:Images** or **/Show:All**, returns all image metadata from each image. If the **/Detailed** option is not specified, the default behavior is to return the image name, description, and file name. |
| [/Forest:{Yes | No}] |

## Examples

To view information about all servers, type:

```
wdsutil /Get-AllServers /Show:Config
```

To view detailed information about all servers, type:

```
wdsutil /Verbose /Get-AllServers /Show:All /Detailed /Forest:Yes
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)