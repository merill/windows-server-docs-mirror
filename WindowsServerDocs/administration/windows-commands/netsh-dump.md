---
layout: Conceptual
title: netsh dump | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-dump
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the netsh dump command that allows exporting network configuration settings to a text file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-25T00:00:00.0000000Z
locale: en-us
document_id: a9ab7550-ce42-169c-98a9-813530b483d7
document_version_independent_id: a9ab7550-ce42-169c-98a9-813530b483d7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-dump.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-dump
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-dump.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5cbb4867-1e1f-d821-b0ad-ab9d8fc32fc6
---

# netsh dump | Microsoft Learn

The `netsh dump` command generates a script that saves the system's current network settings. By running this command, you produce a script that can be used to recreate the same settings later or on a different device.

## Syntax

```
netsh dump
```

## Parameters

| Command | Description |
| --- | --- |
| dump | Exports the network configuration details and settings to your device. |

## Example

To export your network configuration settings to a file named "netsh\_config.txt" and save it in **C:\NetConfig**, run the following command:

```cmd
netsh dump > "C:\NetConfig\netsh_config.txt"
```