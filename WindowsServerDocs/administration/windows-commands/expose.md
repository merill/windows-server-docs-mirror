---
layout: Conceptual
title: expose | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/expose
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the expose command, which exposes a persistent shadow copy as a drive letter, share, or mount point.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ecd1b0cb-78b7-5316-6f3b-cd9af153ccc5
document_version_independent_id: 8c88969a-f45b-e31d-bfc8-9f635c89d4e8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/expose.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/expose
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/expose.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6c6d6b3c-c836-5847-5b57-e268d4a076da
---

# expose | Microsoft Learn

Exposes a persistent shadow copy as a drive letter, share, or mount point.

## Syntax

```
expose <shadowID> {<drive:> | <share> | <mountpoint>}
```

### Parameters

| Parameter | Description |
| --- | --- |
| shadowID | Specifies the shadow ID of the shadow copy you want to expose. You can also use an existing alias or an environment variable in place of *shadowID*. Use **add** without parameters to see existing aliases. |
| `<drive:>` | Exposes the specified shadow copy as a drive letter (for example, `p:`). |
| `<share>` | Exposes the specified shadow copy at a share (for example, `\\machinename`). |
| `<mountpoint>` | Exposes the specified shadow copy to a mount point (for example, `C:\shadowcopy`). |

### Examples

To expose the persistent shadow copy associated with the VSS\_SHADOW\_1 environment variable as drive X, type:

```
expose %vss_shadow_1% x:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [diskshadow command](diskshadow)