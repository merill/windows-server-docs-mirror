---
layout: Conceptual
title: nslookup set class | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup-set-class
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nslookup set class command, which changes the query class.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 2808d0cb-b9b7-3250-8669-bfbf7ab08363
document_version_independent_id: 089ce72c-1340-6cfb-cd34-4f35325edbea
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nslookup-set-class.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nslookup-set-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nslookup-set-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 405db201-1e98-d486-f611-ae9bd8206bfd
---

# nslookup set class | Microsoft Learn

Changes the query class. The class specifies the protocol group of the information.

## Syntax

```
set class=<class>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<class>` | The valid values include:<br>- **IN:** Specifies the Internet class. This is the default value.<br>- **CHAOS:** Specifies the Chaos class.<br>- **HESIOD:** Specifies the MIT Athena Hesiod class.<br>- **ANY:** Specifies to use any of the previously listed values. |
| /? | Displays help at the command prompt. |
| /help | Displays help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)