---
layout: Conceptual
title: load metadata | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/load-metadata
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the load metadata command, which loads a metadata .cab file prior to importing a transportable shadow copy or loads the writer metadata in the case of a restore.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 222b7eb0-bb24-9585-8185-c1016ce269dd
document_version_independent_id: a583db79-4604-9386-f58c-c0b3c11e8220
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/load-metadata.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/load-metadata
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/load-metadata.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 61045b53-20a0-ff56-26d1-b1df9bd0916e
---

# load metadata | Microsoft Learn

Loads a metadata .cab file prior to importing a transportable shadow copy or loads the writer metadata in the case of a restore. If used without parameters, **load metadata** displays help at the command prompt.

## Syntax

```
load metadata [<drive>:][<path>]<metadata.cab>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<drive>:][<path>]` | Specifies the location of the metadata file. |
| metadata.cab | Specifies the metadata .cab file to load. |

## Remarks

- You can use the **import** command to import a transportable shadow copy based on the metadata specified by **load metadata**.
- You must run this command before the **begin restore** command, to load the selected writers and components for the restore.

## Examples

To load a metadata file called metafile.cab from the default location, type:

```
load metadata metafile.cab
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [import diskshadow command](import)
- [begin restore command](begin-restore)