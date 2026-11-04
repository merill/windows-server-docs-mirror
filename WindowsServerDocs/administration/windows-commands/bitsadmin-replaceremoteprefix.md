---
layout: Conceptual
title: bitsadmin replaceremoteprefix | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-replaceremoteprefix
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin replaceremoteprefix command, which changes the remote URL for all files in the job from *oldprefix* to *newprefix*, as necessary.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 91dd50ea-ba61-73f2-4fca-42efa26dbc4b
document_version_independent_id: 37417571-eb07-1b68-8c40-ca153683fd2a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-replaceremoteprefix.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-replaceremoteprefix
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-replaceremoteprefix.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 712800ef-e9de-91da-6003-341d52aa526c
---

# bitsadmin replaceremoteprefix | Microsoft Learn

Changes the remote URL for all files in the job from *oldprefix* to *newprefix*, as necessary.

## Syntax

```
bitsadmin /replaceremoteprefix <job> <oldprefix> <newprefix>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| oldprefix | Existing URL prefix. |
| newprefix | New URL prefix. |

## Examples

To change the remote URL for all files in job named *myDownloadJob*, from *http://stageserver* to *http://prodserver*.

```
bitsadmin /replaceremoteprefix myDownloadJob http://stageserver http://prodserver
```

## Additional information

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)