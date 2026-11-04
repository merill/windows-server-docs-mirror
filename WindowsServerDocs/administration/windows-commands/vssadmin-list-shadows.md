---
layout: Conceptual
title: vssadmin list shadows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/vssadmin-list-shadows
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: A description of the vssadmin list shadows command, which lists all existing shadow copies of a specified volume.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2018-05-18T00:00:00.0000000Z
locale: en-us
document_id: 2d740706-3408-a5f3-4bcf-c18eebce8ec3
document_version_independent_id: 5059601f-750a-0226-5ce0-6182f278c37d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/vssadmin-list-shadows.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/vssadmin-list-shadows
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/vssadmin-list-shadows.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a6e13029-337a-7608-64de-91852f8022c4
---

# vssadmin list shadows | Microsoft Learn

Lists all existing shadow copies of a specified volume. If you use this command without parameters, it displays all volume shadow copies on the computer in the order dictated by **Shadow Copy Set**.

## Syntax

```
vssadmin list shadows [/for=<ForVolumeSpec>] [/shadow=<ShadowID>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /for=`<ForVolumeSpec>` | Specifies which volume the shadow copies will be listed for. |
| /shadow=`<ShadowID>` | Lists the shadow copy specified by ShadowID. To get the shadow copy ID, use the [vssadmin list shadows command](vssadmin-list-shadows). When you type a shadow copy ID, use the following format, where each *X* represents a hexadecimal character:<br>`{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}` |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [vssadmin command](vssadmin)
- [vssadmin list shadows command](vssadmin-list-shadows)