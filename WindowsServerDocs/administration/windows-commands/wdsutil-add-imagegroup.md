---
layout: Conceptual
title: wdsutil add-imagegroup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-add-imagegroup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil add-imagegroup command, which adds an image group to a Windows Deployment Services server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e920277e-e5d1-1c34-c416-0d046daf7d41
document_version_independent_id: 914ec133-f783-534e-66ee-c5e77e4368bc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-add-imagegroup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-add-imagegroup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-add-imagegroup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 0f9fd2a6-8c16-7367-c0ed-9fe9bc40ae24
---

# wdsutil add-imagegroup | Microsoft Learn

Adds an image group to a Windows Deployment Services server.

## Syntax

```
wdsutil [Options] /add-ImageGroup imageGroup:<Imagegroupname> [/Server:<Server name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| imageGroup:`<Imagegroupname>`] | Specifies the name of the image to be added. |
| [/Server:`<Servername>`] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If a server name is not specified, the local server is used. |

## Examples

To add an image group, type either:

```
wdsutil /add-ImageGroup imageGroup:ImageGroup2
```

```
wdsutil /verbose /add-Imagegroup imageGroup:My Image Group /Server:MyWDSServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-allimagegroups command](wdsutil-get-allimagegroups)
- [wdsutil get-imagegroup command](wdsutil-get-imagegroup)
- [wdsutil remove-imagegroup command](wdsutil-remove-imagegroup)
- [wdsutil set-imagegroup command](wdsutil-set-imagegroup)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)