---
layout: Conceptual
title: pushprinterconnections | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pushprinterconnections
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pushprinterconnections command, which reads Deployed Printer Connection settings from Group Policy and deploys/removes printer connections as needed.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 17679e17-7b25-7778-3672-b155f742a901
document_version_independent_id: d078658d-5f35-8c81-10b4-7f6919754278
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pushprinterconnections.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pushprinterconnections
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pushprinterconnections.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 949b3d28-bffb-4eba-f7c9-969dca2bfc19
---

# pushprinterconnections | Microsoft Learn

Reads Deployed Printer Connection settings from Group Policy and deploys/removes printer connections as needed.

Important

This utility is for use in machine startup or user logon scripts, and shouldn't be run from the command line.

## Syntax

```
pushprinterconnections <-log> <-?>
```

### Parameters

| Parameter | Description |
| --- | --- |
| &lt;-log&gt; | Writes a per user debug log file to *%temp*, or writes a per machine debug log to *%windir%\temp*. |
| &lt;-?&gt; | Displays Help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Print Command Reference](print-command-reference)
- [Deploy Printers by Using Group Policy](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc722179%28v=ws.10%29)