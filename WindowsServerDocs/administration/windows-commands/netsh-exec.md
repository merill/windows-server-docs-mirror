---
layout: Conceptual
title: netsh exec | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-exec
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the netsh exec command that runs a script file containing a series of netsh commands to automate network configuration tasks.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-25T00:00:00.0000000Z
locale: en-us
document_id: 16edafee-7a1e-5191-5267-59ce21ac7b37
document_version_independent_id: 16edafee-7a1e-5191-5267-59ce21ac7b37
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-exec.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-exec
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-exec.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2703f224-9bce-76bb-93dd-c6dac0660bdd
---

# netsh exec | Microsoft Learn

The `netsh exec` command executes a script file. This script file contains a series of `netsh` commands that are run sequentially when the script is executed. It automates network configuration tasks by performing complex operations without you needing to manually enter the entries.

## Syntax

```
netsh exec <ScriptFile>
```

## Parameters

| Command | Description |
| --- | --- |
| exec `<ScriptFile>` | Loads and runs the target script file. |

## Example

To load and run your script from the location **C:\NetshScripts\network\_script.txt**, run the following command:

```cmd
netsh exec "C:\NetshScripts\network_script.txt"
```