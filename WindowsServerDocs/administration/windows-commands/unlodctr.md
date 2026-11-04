---
layout: Conceptual
title: unlodctr | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/unlodctr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the unlodctr command, which removes Performance counter names and Explain text for a service or device driver from the system registry.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-10-22T00:00:00.0000000Z
locale: en-us
document_id: 307761e1-d870-64d9-17d0-22660ce2ddb1
document_version_independent_id: bc3289bf-9bd4-e986-02e6-3c8c11da0db6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/unlodctr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/unlodctr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/unlodctr.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: be43fea4-bb33-23a4-4d50-399912790ca7
---

# unlodctr | Microsoft Learn

Removes **Performance counter names** and **Explain text** for a service or device driver from the system registry.

Warning

Incorrectly editing the registry may severely damage your system. Before making changes to the registry, you should back up any valued data on the computer.

## Syntax

```
unlodctr <drivername>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<drivername>` | Removes the **Performance counter name** settings and **Explain text** for driver or service `<drivername>` from the Windows Server registry. If your `<drivername>` includes spaces, you must use quotation marks around the text, for example "Driver name". |
| /? | Displays help at the command prompt. |

#### Remarks

An exit code of **0** indicates the command line syntax was correct. It doesn't mean the operation was successful. Check the output from the command for potential error messages.

## Examples

To remove the current **Performance counter names** and **Explain text** for the Simple Mail Transfer Protocol (SMTP) service, type:

```
unlodctr SMTPSVC
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)