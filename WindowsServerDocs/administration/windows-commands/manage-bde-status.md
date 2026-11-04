---
layout: Conceptual
title: manage-bde status | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/manage-bde-status
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the manage-bde status command, which provides information about all drives on the computer, regardless whether they are BitLocker protected.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 1b834000-8842-2b0a-68f5-97992566ed40
document_version_independent_id: 44bd7270-93da-850b-cc9a-d7de8fc7687c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/manage-bde-status.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/manage-bde-status
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/manage-bde-status.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: 3f9b8043-354e-14bb-d385-1526f8eab98c
---

# manage-bde status | Microsoft Learn

Provides information about all drives on the computer; whether or not they are BitLocker-protected, including:

- Size
- BitLocker version
- Conversion status
- Percentage encrypted
- Encryption method
- Protection status
- Lock status
- Identification field
- Key protectors

## Syntax

```
manage-bde -status [<drive>] [-protectionaserrorlevel] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<drive>` | Represents a drive letter followed by a colon. |
| -protectionaserrorlevel | Causes the manage-bde command-line tool to send the return code of **0** if the volume is protected and **1** if the volume is unprotected; most commonly used for batch scripts to determine if a drive is BitLocker-protected. You can also use **-p** as an abbreviated version of this command. |
| -computername | Specifies that manage-bde.exe will be used to modify BitLocker protection on a different computer. You can also use **-cn** as an abbreviated version of this command. |
| `<name>` | Represents the name of the computer on which to modify BitLocker protection. Accepted values include the computer's NetBIOS name and the computer's IP address. |
| -? or /? | Displays brief Help at the command prompt. |
| -help or -h | Displays complete Help at the command prompt. |

### Examples

To display the status of drive C, type:

```
manage-bde -status C:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [manage-bde command](manage-bde)