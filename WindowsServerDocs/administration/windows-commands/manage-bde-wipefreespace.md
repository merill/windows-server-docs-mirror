---
layout: Conceptual
title: manage-bde wipefreespace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/manage-bde-wipefreespace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the manage-bde wipefreespace command, which wipes the free space on the volume removing any data fragments that may have existed in the space.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f3812dfb-f308-4556-c90c-856a77e9b1ae
document_version_independent_id: c1d1c8d4-ec53-8463-e24d-c7258e2d4a58
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/manage-bde-wipefreespace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/manage-bde-wipefreespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/manage-bde-wipefreespace.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4d3e79d8-801a-2cf4-b380-d96d8456b63b
---

# manage-bde wipefreespace | Microsoft Learn

Wipes the free space on the volume, removing any data fragments that may have existed in the space. Running this command on a volume encrypted using the **Used Space Only** encryption method provides the same level of protection as the **Full Volume Encryption** encryption method.

## Syntax

```
manage-bde -wipefreespace|-w [<drive>] [-cancel] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<drive>` | Represents a drive letter followed by a colon. |
| -cancel | Cancels a wipe of free space that is in process. |
| -computername | Specifies that manage-bde.exe will be used to modify BitLocker protection on a different computer. You can also use **-cn** as an abbreviated version of this command. |
| `<name>` | Represents the name of the computer on which to modify BitLocker protection. Accepted values include the computer's NetBIOS name and the computer's IP address. |
| -? or /? | Displays brief Help at the command prompt. |
| -help or -h | Displays complete Help at the command prompt. |

### Examples

To wipe the free space on drive C, type either:

```
manage-bde -w C:
```

```
manage-bde -wipefreespace C:
```

To cancel the wipe of the free space on drive C, type either:

```
manage-bde -w -cancel C:
```

```
manage-bde -wipefreespace -cancel C:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [manage-bde command](manage-bde)