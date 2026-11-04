---
layout: Conceptual
title: wdsutil remove-imagegroup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-remove-imagegroup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil remove-imagegroup, which removes an image group from a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4e376462-951d-c9db-ad08-dafd4f4378cc
document_version_independent_id: afc4747d-187f-3ebb-d2e7-d8205eecdbc4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-remove-imagegroup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-remove-imagegroup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-remove-imagegroup.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 49790c18-834d-d826-e4b1-afb43ba9d7a2
---

# wdsutil remove-imagegroup | Microsoft Learn

Removes an image group from a server.

## Syntax

```
wdsutil [Options] /remove-ImageGroup Group:<Image group name> [/Server:<Server name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| imagegroup:&lt;Image group name&gt; | Specifies the name of the image group to be removed |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |

## Examples

To remove the image group, type one of the following:

```
wdsutil /remove-ImageGroumediaGroup:ImageGroup1
wdsutil /verbose /remove-ImageGroumediaGroup:My Image Group /Server:MyWDSServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-imagegroup command](wdsutil-add-imagegroup)
- [wdsutil get-allimagegroups command](wdsutil-get-allimagegroups)
- [wdsutil get-imagegroup command](wdsutil-get-imagegroup)
- [wdsutil set-imagegroup command](wdsutil-set-imagegroup)