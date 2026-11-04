---
layout: Conceptual
title: vssadmin | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/vssadmin
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the vssadmin commands, which shows current volume shadow copy backups and all installed shadow copy writers and providers.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2018-05-18T00:00:00.0000000Z
locale: en-us
document_id: b44128eb-0f09-9d9c-ded5-8533b0ce07c1
document_version_independent_id: a3d345a9-dd5d-88b1-d135-b22ddb427f6d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/vssadmin.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/vssadmin
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/vssadmin.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c1abe480-6a76-1db6-d971-f7ccab9fab10
---

# vssadmin | Microsoft Learn

Shows current volume shadow copy backups and all installed shadow copy writers and providers. The following table lists the available `vssadmin` commands. Select a command name to view its syntax.

| Command | Description | Availability |
| --- | --- | --- |
| [vssadmin delete shadows](vssadmin-delete-shadows) | Deletes volume shadow copies. | Client and Server |
| [vssadmin list providers](vssadmin-list-providers) | Lists registered volume shadow copy providers. | Client and Server |
| [vssadmin list shadows](vssadmin-list-shadows) | Lists existing volume shadow copies. | Client and Server |
| [vssadmin list shadowstorage](vssadmin-list-shadowstorage) | Lists volume shadow copy storage associations. | Client and Server |
| [vssadmin list volumes](vssadmin-list-volumes) | Lists volumes eligible for shadow copies. | Client and Server |
| [vssadmin list writers](vssadmin-list-writers) | Lists all subscribed volume shadow copy writers on the system. | Client and Server |
| [vssadmin resize shadowstorage](vssadmin-resize-shadowstorage) | Resizes the maximum size for a shadow copy storage association. | Client and Server |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)