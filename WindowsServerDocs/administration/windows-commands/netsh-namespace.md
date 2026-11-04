---
layout: Conceptual
title: netsh namespace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-namespace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh namespace command retrieves namespace policies in Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-29T00:00:00.0000000Z
locale: en-us
document_id: 75cd5ce3-2bd7-528f-1ee9-7c0c3dafd2b1
document_version_independent_id: 75cd5ce3-2bd7-528f-1ee9-7c0c3dafd2b1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-namespace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-namespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-namespace.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 79569106-74c6-333e-c70d-58c724b542ab
---

# netsh namespace | Microsoft Learn

The `netsh namespace` command retrieves and displays namespace policy information from a Windows system.

## Syntax

```
netsh namespace [dump] [show] [help] [?]
netsh namespace show <effectivepolicy> <policy> [namespace=] <string>
```

## Parameters

| Parameter | Description |
| --- | --- |
| `dump` | Outputs a configuration script containing the current namespace policy settings. This script can be saved and used to restore settings if needed. |
| `show` | Displays information about namespace policies. - `effectivepolicy` - Displays the effective namespace policies in place. You can specify a namespace to view only the relevant policy entries for that namespace.<br>- `policy` - Displays the entries in the namespace policy table. You can specify a namespace to restrict the output to policies specific to that namespace. |
| `help` or `?` | Provides help for the list of commands available in the `netsh namespace` context. |

## Examples

To retrieve the policies for a specific namespace, run the following command:

```cmd
netsh namespace show policy namespace=[YourNamespace]
```