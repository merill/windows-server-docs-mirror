---
layout: Conceptual
title: refsutil | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/refsutil
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the refsutil tool, which manages and repairs Resilient File System (ReFS) volumes in Windows ensuring their integrity, performance, and optimization.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-04-02T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 6a32ad5a-e2ce-a010-2e33-00fd128b25aa
document_version_independent_id: e9c6f167-65fd-6c02-efdc-cfd0143fabe7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/refsutil.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/refsutil
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/refsutil.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 0671d448-27e7-0dbc-cd05-f9badeb06f4b
---

# refsutil | Microsoft Learn

The `refsutil` tool is a command-line utility designed to manage and repair volumes formatted with the Resilient File System (ReFS) in Windows. This utility provides a wide range of functionalities to ensure the integrity, performance, and optimization of ReFS volumes. It's an essential tool for maintaining robust file system operations and addressing various issues that might arise.

## Commands

| Command | Description |
| --- | --- |
| [compression](refsutil-compression) | Enables and manages volume compression to save storage space. |
| [dedup](refsutil-dedup) | Identifies and consolidates duplicate clusters to optimize storage usage. |
| [fixboot](refsutil-fixboot) | Repairs boot sectors to ensure proper system startup. |
| [iometrics](refsutil-iometrics) | Tracks and reports input/output metrics for volume performance analysis. |
| [leak](refsutil-leak) | Detects and resolves memory or resource leaks in the file system. |
| [salvage](refsutil-salvage) | Performs recovery operations on a corrupt volume to retrieve data. |
| [streamsnapshot](refsutil-streamsnapshot) | Manages snapshots of data streams for backup or recovery purposes. |
| [triage](refsutil-triage) | Analyzes and addresses file system corruptions. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)