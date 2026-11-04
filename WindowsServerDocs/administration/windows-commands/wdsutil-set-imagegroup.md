---
layout: Conceptual
title: wdsutil set-imagegroup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-set-imagegroup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for Subcommand set-ImageGroup, which changes the attributes of an image group.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 412bdd64-59b6-3726-77a2-19380bbb511f
document_version_independent_id: 46693e19-bed9-5afd-4b42-10bbb1101a13
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-set-imagegroup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-set-imagegroup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-set-imagegroup.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: aaa3e1bb-be6d-92a7-637c-2e5d563842f8
---

# wdsutil set-imagegroup | Microsoft Learn

Changes the attributes of an image group.

## Syntax

```
wdsutil [Options] /set-imagegroup:<Image group name> [/Server:<Server name>] [/Name:<New image group name>] [/Security:<SDDL>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /set-imagegroup:&lt;Image group name&gt; | Specifies the name of the image group. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If not specified, the local server will be used. |
| [/Name:&lt;New image group name&gt;] | Specifies the new name of the image group. |
| [/Security:&lt;SDDL&gt;] | Specifies the new Security Descriptor of the image group, in security descriptor definition language (SDDL) format. |

## Examples

To set the name for an image group, type:

```
wdsutil /Set-ImageGroup:ImageGroup1 /Name:New Image Group Name
```

To specify various settings for an image group, type:

```
wdsutil /verbose /Set-ImageGroupGroup:ImageGroup1 /Server:MyWDSServer /Name:New Image Group Name
/Security:O:BAG:S-1-5-21-2176941838-3499754553-4071289181-513 D:AI(A;ID;FA;;;SY)(A;OICIIOID;GA;;;SY)(A;ID;FA;;;BA)(A;OICIIOID;GA;;;BA) (A;ID;0x1200a9;;;AU)(A;OICIIOID;GXGR;;;AU)
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-imagegroup command](wdsutil-add-imagegroup)
- [wdsutil get-allimagegroups command](wdsutil-get-allimagegroups)
- [wdsutil get-imagegroup command](wdsutil-get-imagegroup)
- [wdsutil remove-imagegroup command](wdsutil-remove-imagegroup)