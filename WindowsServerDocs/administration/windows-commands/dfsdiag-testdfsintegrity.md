---
layout: Conceptual
title: dfsdiag testdfsintegrity | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/dfsdiag-testdfsintegrity
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the dfsdiag testdfsintegrity command, which checks the integrity of the Distributed File System (DFS) namespace.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 802850c4-0365-5fc3-bda1-cf8c9c1afbd2
document_version_independent_id: ead601fc-9e80-53e3-b697-2edc4289639d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/dfsdiag-testdfsintegrity.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/dfsdiag-testdfsintegrity
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/dfsdiag-testdfsintegrity.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4bbd7e1f-f811-7c01-8d6d-e26d857efab9
---

# dfsdiag testdfsintegrity | Microsoft Learn

Checks the integrity of the Distributed File System (DFS) namespace by performing the following tests:

- Checks for DFS metadata corruption or inconsistencies between domain controllers.
- Validates the configuration of access-based enumeration to ensure that it is consistent between DFS metadata and the namespace server share.
- Detects overlapping DFS folders (links), duplicate folders, and folders with overlapping folder targets.

## Syntax

```
dfsdiag /testdfsintegrity /DFSroot: <DFS root path> [/recurse] [/full]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /DFSroot: `<DFS root path>` | The DFS namespace to diagnose. |
| /recurse | Performs the testing, including any namespace interlinks. |
| /full | Verifies the consistency of the share and NTFS ACLs, along with the client side configuration on all folder targets. It also verifies that the online property is set. |

## Examples

To verify the integrity and consistency of the Distributed File System (DFS) namespaces in *contoso.com\MyNamespace*, including any interlinks, type:

```
dfsdiag /testdfsintegrity /DFSRoot:\contoso.com\MyNamespace /recurse /full
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [dfsdiag command](dfsdiag)