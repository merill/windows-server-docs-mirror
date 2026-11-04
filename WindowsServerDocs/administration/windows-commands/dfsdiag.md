---
layout: Conceptual
title: dfsdiag | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/dfsdiag
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the dfsdiag command, which provides diagnostic information for DFS Namespaces.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7764fcee-3045-4e3a-75e0-377704928ecb
document_version_independent_id: 177a1324-d102-7bdf-764b-0823a545eb4b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/dfsdiag.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/dfsdiag
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/dfsdiag.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 232fc627-4b8a-90e1-03ef-1c6b9ccdf043
---

# dfsdiag | Microsoft Learn

Provides diagnostic information for DFS Namespaces.

## Syntax

```
dfsdiag /testdcs [/domain:<domain name>]
dfsdiag /testsites </machine:<server name>| /DFSPath:<namespace root or DFS folder> [/recurse]> [/full]
dfsdiag /testdfsconfig /DFSRoot:<namespace>
dfsdiag /testdfsintegrity /DFSRoot:<DFS root path> [/recurse] [/full]
dfsdiag /testreferral /DFSpath:<DFS path to get referrals> [/full]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [dfsdiag testdcs](dfsdiag-testdcs) | Checks domain controller configuration. |
| [dfsdiag testsites](dfsdiag-testsites) | Checks site associations. |
| [dfsdiag testdfsconfig](dfsdiag-testdfsconfig) | Checks DFS Namespace configuration. |
| [dfsdiag testdfsintegrity](dfsdiag-testdfsintegrity) | Checks DFS Namespace integrity. |
| [dfsdiag testreferral](dfsdiag-testreferral) | Checks referral responses. |
| /? | Displays help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)