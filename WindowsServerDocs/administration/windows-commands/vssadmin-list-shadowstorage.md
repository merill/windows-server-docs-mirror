---
layout: Conceptual
title: vssadmin list shadowstorage - in Windows and Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/vssadmin-list-shadowstorage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Learn how to use the vssadmin list shadowstorage command to list all shadow copy storage associations on a system or a specified volume.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2026-09-07T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: d631d6cc-f97a-2b3a-ce4c-b55c850e9931
document_version_independent_id: d631d6cc-f97a-2b3a-ce4c-b55c850e9931
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/vssadmin-list-shadowstorage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/vssadmin-list-shadowstorage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/vssadmin-list-shadowstorage.md
platformId: 3b28fb33-ee6b-3074-63ec-61153c6fd73e
---

# vssadmin list shadowstorage - in Windows and Windows Server | Microsoft Learn

Lists the shadow copy storage associations on the system. A shadow copy storage association links a volume that has shadow copies to the volume that stores those copies, and reports the disk space that storage uses.

Run this command to find out where shadow copy storage resides and how much space it consumes, such as before you change its size.

## Syntax

```
vssadmin list shadowstorage [/for=<ForVolumeSpec>|/on=<OnVolumeSpec>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /for=`<ForVolumeSpec>` | Lists the shadow copy storage associations for the specified volume. Don't use this parameter together with **/on**. |
| /on=`<OnVolumeSpec>` | Lists the shadow copy storage associations on the specified volume. Don't use this parameter together with **/for**. |

## Examples

To list all shadow copy storage associations located on volume C, type:

```
vssadmin list shadowstorage /on=C:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [vssadmin command](vssadmin)