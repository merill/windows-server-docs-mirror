---
layout: Conceptual
title: scwcmd rollback | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/scwcmd-rollback
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the scwcmd rollback command, which applies the most recent rollback policy available, and then deletes that rollback policy.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 51aa97f9-060f-6f1a-9a99-ae1deac9a4ed
document_version_independent_id: 32b8e364-9a05-2cb4-2024-f2a9ce8ffe9a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/scwcmd-rollback.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/scwcmd-rollback
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/scwcmd-rollback.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 50561d99-811b-b509-73e1-506f1ee52315
---

# scwcmd rollback | Microsoft Learn

Applies the most recent rollback policy available, and then deletes that rollback policy.

## Syntax

```
scwcmd rollback /m:<computername> [/u:<username>] [/pw:<password>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /m:`<computername>` | Specifies the NetBIOS name, DNS name, or IP address of a computer where the rollback operation should be performed. |
| /u:`<username>` | Specifies an alternate user account to use when performing a remote rollback. The default is the logged on user. |
| /pw:`<password>` | Specifies an alternate user credential to use when performing a remote rollback. The default is the logged on user. |
| /? | Displays help at the command prompt. |

## Examples

To roll back the security policy on a computer at IP address *172.16.0.0*, type:

```
scwcmd rollback /m:172.16.0.0
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [scwcmd analyze command](scwcmd-analyze)
- [scwcmd configure command](scwcmd-configure)
- [scwcmd register command](scwcmd-register)
- [scwcmd transform command](scwcmd-transform)
- [scwcmd view command](scwcmd-view)