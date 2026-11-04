---
layout: Conceptual
title: nslookup server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nslookup server command, which changes the default server to the specified Domain Name System (DNS) domain.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e8646f52-b3af-dbc4-2a56-5024a34073c2
document_version_independent_id: f1bdbf55-8801-1bd3-3a7a-d5d94c548429
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nslookup-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nslookup-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nslookup-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 61db6a01-4588-258b-617d-63ed425fa685
---

# nslookup server | Microsoft Learn

Changes the default server to the specified Domain Name System (DNS) domain.

This command uses the current default server to look up the information about the specified DNS domain. If you want to lookup information using the initial server, use the [nslookup lserver](nslookup-lserver) command.

## Syntax

```
server <DNSdomain>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<DNSdomain>` | Specifies the DNS domain for the default server. |
| /? | Displays help at the command prompt. |
| /help | Displays help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [nslookup lserver](nslookup-lserver)