---
layout: Conceptual
title: dfsutil | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/dfsutil
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the dfsutil command, which manages DFS Namespaces, servers and clients.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 616ae26d-ed30-096c-6937-6d54b5103c80
document_version_independent_id: 616ae26d-ed30-096c-6937-6d54b5103c80
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/dfsutil.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/dfsutil
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/dfsutil.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1e9a9d92-8d66-6ef0-48a1-6883e1f7bb10
---

# dfsutil | Microsoft Learn

The dfsutil command manages DFS Namespaces, servers, and clients.

## Functionality available in PowerShell

The [DFSN](/en-us/powershell/module/dfsn/) PowerShell module provides equivalent functionality to the following dfsutil parameters.

| Parameter | Description |
| --- | --- |
| root | Displays, creates, removes, imports, exports namespace roots. |
| link | Displays, creates, removes, or moves folders (links). |
| target | Displays, create, remove folder target or namespace server. |
| property | Displays or modifies a folder target or namespace server. |
| server | Displays or modifies namespace configuration. |
| domain | Displays all domain-based namespaces in a domain. |

## Functionality available only in dfsutil

The following functionality is available only as dfsutil parameters:

| Parameter | Description |
| --- | --- |
| client | Displays or modifies client information or registry keys. |
| diag | Perform diagnostics or view dfsdirs/dfspath. |
| cache | Displays or flushes the client cache. |

For more info about each of these commands, open a command prompt on a server with the DFS Namespaces management tools installed, and then type `dfsutil client /?`, `dfsutil diag /?`, or `dfsutil cache /?`.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)