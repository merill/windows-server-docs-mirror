---
layout: Conceptual
title: dfsdiag testsites | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/dfsdiag-testsites
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for dfsdiag testsites, which checks the configuration of active directory Domain Services (AD DS) sites by verifying that servers that act as namespace servers or folder (link) targets have the same site associations on all domain controllers.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9d808e26-ba18-cdb3-1369-f114b8270bb9
document_version_independent_id: 2acf171f-e1cb-8265-23b5-77406702a5de
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/dfsdiag-testsites.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/dfsdiag-testsites
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/dfsdiag-testsites.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 47b8a7d2-8d52-dc33-ef10-f317e35803b8
---

# dfsdiag testsites | Microsoft Learn

Checks the configuration of active directory Domain Services (AD DS) sites by verifying that servers that act as namespace servers or folder (link) targets have the same site associations on all domain controllers.

## Syntax

```
dfsdiag /testsites </machine:<server name>| /DFSpath:<namespace root or DFS folder> [/recurse]> [/full]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `/machine:<server name>` | The name of the server on which to verify the site association. |
| `/DFSpath:<namespace root or DFS folder>` | The namespace root or Distributed File System (DFS) folder (link) with targets for which to verify the site association. |
| /recurse | Enumerates and verifies the site associations for all folder targets under the specified namespace root. |
| /full | Verifies that AD DS and the registry of the server contain the same site association information. |

## Examples

To check the site associations on *machine\MyServer*, type:

```
dfsdiag /testsites /machine:MyServer
```

To check a Distributed File System (DFS) folder to verify the site association, along with verifying that AD DS and the registry of the server contain the same site association information, type:

```
dfsdiag /TestSites /DFSpath:\\contoso.com\namespace1\folder1 /full
```

To check a namespace root to verify the site association, along with enumerating and verifying the site associations for all folder targets under the specified namespace root, and verifying that AD DS and the registry of the server contain the same site association information, type:

```
dfsdiag /testsites /DFSpath:\\contoso.com\namespace2 /recurse /full
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [dfsdiag command](dfsdiag)