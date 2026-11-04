---
layout: Conceptual
title: netsh add | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-add
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the netsh add command that adds a helper dll.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-24T00:00:00.0000000Z
locale: en-us
document_id: 2a8c436b-2414-309f-9025-461d33bcf374
document_version_independent_id: 2a8c436b-2414-309f-9025-461d33bcf374
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-add.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-add
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-add.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 580dbfaf-e048-861d-48b9-9ce01ecf1e7e
---

# netsh add | Microsoft Learn

The `netsh add` command is used to install helper Dynamic Link Libraries (DLL) allowing for more specialized network configurations.

## Syntax

```
netsh add helper [file]
```

## Parameters

| Command | Description |
| --- | --- |
| helper | Adds a helper DLL file. |

## Example

To add a helper DLL located at **C:\dlls\HelperDLL.dll**, run the following command:

```cmd
netsh add helper C:\dlls\HelperDLL.dll
```