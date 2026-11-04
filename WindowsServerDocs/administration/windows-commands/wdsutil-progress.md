---
layout: Conceptual
title: wdsutil progress | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-progress
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil progress, which displays progress while a command is running.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: eea1ab99-6964-dea5-7220-3ba3d8fd777e
document_version_independent_id: 95b0bae2-bf77-a12a-25e0-52b36d3da053
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-progress.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-progress
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-progress.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8e7178ef-ab85-65f0-4361-d90766a7a0db
---

# wdsutil progress | Microsoft Learn

Displays progress while a command is running. You can use **/progress** with any other wdsutil commands that you run. If you want to turn on verbose logging for this command, you must specify **/verbose** and **/progress** directly after **wdsutil**.

## Syntax

```
wdsutil /progress <commands>
```

## Examples

To initialize the server and display progress, type:

```
wdsutil /verbose /progress /Initialize-Server /Server:MyWDSServer /RemInst:C:\RemoteInstall
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)