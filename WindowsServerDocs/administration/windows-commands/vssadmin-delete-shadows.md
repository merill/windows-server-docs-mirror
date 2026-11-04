---
layout: Conceptual
title: vssadmin delete shadows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/vssadmin-delete-shadows
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: A description of the vssadmin delete shadows command, which deletes a specified volume's shadow copies.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2018-05-18T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 24216239-6472-41ca-d9a7-bd55deef82b9
document_version_independent_id: 749ed1bf-3e73-3269-382b-c80b45ed2250
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/vssadmin-delete-shadows.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/vssadmin-delete-shadows
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/vssadmin-delete-shadows.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 37669e61-b4a6-b0b7-28f7-1a3b678e4bd2
---

# vssadmin delete shadows | Microsoft Learn

Deletes a specified volume's shadow copies. You can only delete shadow copies with the *client-accessible* type.

Note

If you encounter the error "Error: Snapshots were found, but they were outside of your allowed context," the shadow copies are not client-accessible and cannot be deleted with `vssadmin`. Use the [diskshadow](diskshadow) command instead to manage and delete those shadow copies.

## Syntax

```
vssadmin delete shadows /for=<ForVolumeSpec> [/oldest | /all | /shadow=<ShadowID>] [/quiet]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /for=`<ForVolumeSpec>` | Specifies which volume's shadow copy will be deleted. |
| /oldest | Deletes only the oldest shadow copy. |
| /all | Deletes all of the specified volume's shadow copies. |
| /shadow=`<ShadowID>` | Deletes the shadow copy specified by ShadowID. To get the shadow copy ID, use the [vssadmin list shadows command](vssadmin-list-shadows). When you enter a shadow copy ID, use the following format, where each *X* represents a hexadecimal character:<br>XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX |
| /quiet | Specifies that the command won't display messages while running. |

## Examples

Caution

Deleting a shadow copy is permanent. You can't recover a deleted shadow copy, and you lose any previous versions or restore points that depend on it. Target only the volume or shadow copy you intend to remove, and confirm the shadow copy IDs with [vssadmin list shadows](vssadmin-list-shadows) before you delete anything. This command deletes only shadow copies that have the *client-accessible* type.

To delete the oldest shadow copy of volume C, type:

```
vssadmin delete shadows /for=c: /oldest
```

To delete all client-accessible shadow copies of volume D, type:

```
vssadmin delete shadows /for=d: /all
```

To delete a single client-accessible shadow copy by its ID, first run [vssadmin list shadows](vssadmin-list-shadows) to find the shadow copy ID. Then run the following command, replacing `c:` with the volume that hosts the shadow copy and `<ShadowID>` with the ID you want to delete. Enter the ID in the format *XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX*, where each *X* is a hexadecimal character:

```
vssadmin delete shadows /for=c: /shadow=<ShadowID>
```

To delete all client-accessible shadow copies of volume D without showing progress messages, add the `/quiet` parameter:

```
vssadmin delete shadows /for=d: /all /quiet
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [vssadmin command](vssadmin)
- [vssadmin list shadows command](vssadmin-list-shadows)
- [diskshadow command](diskshadow)