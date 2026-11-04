---
layout: Conceptual
title: automount | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/automount
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the automount command, which enables or disables the automount feature.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f0a74de9-f1e4-5155-1f15-a032791a2794
document_version_independent_id: 37116043-c59b-78ad-fef4-038ff4141940
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/automount.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/automount
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/automount.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 0b79817c-2f79-f09a-ea08-a7aabebafa61
---

# automount | Microsoft Learn

- [Command-Line Syntax Key](command-line-syntax-key)

Important

In storage area network (SAN) configurations, disabling automount prevents Windows from automatically mounting or assigning drive letters to any new basic volumes that are visible to the system.

## Syntax

automount [ { enable | disable | scrub } ] [noerr]

### Parameters

| Parameter | Description |
| --- | --- |
| enable | Enables Windows to automatically mount new basic and dynamic volumes that are added to the system and to assign them drive letters. |
| disable | Prevents Windows from automatically mounting any new basic and dynamic volumes that are added to the system.<br>**Note**: Disabling automount can cause failover clusters to fail the storage portion of the Validate a Configuration Wizard. |
| scrub | Removes volume mount point directories and registry settings for volumes that are no longer in the system. This prevents volumes that were previously in the system from being automatically mounted and given their former volume mount point(s) when they are added back to the system. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Examples

To see if the automount feature is enabled, type the following commands from within the diskpart command:

```
automount
```

To enable the automount feature, type:

```
automount enable
```

To disable the automount feature, type:

```
automount disable
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [diskpart commands](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc770877%28v%3dws.11%29)