---
layout: Conceptual
title: nslookup lserver | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup-lserver
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nslookup lserver command, which changes the initial server to the specified Domain Name System (DNS) domain.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 0d2f1781-6022-e06f-08af-81bc9826e57c
document_version_independent_id: 972162f1-3b51-c1dd-c6cf-802677308546
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nslookup-lserver.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nslookup-lserver
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nslookup-lserver.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7d3fe017-1c34-e36c-8816-70f2b5789a9c
---

# nslookup lserver | Microsoft Learn

Changes the initial server to the specified Domain Name System (DNS) domain.

This command uses the initial server to look up the information about the specified DSN domain. If you want to lookup information using the current default server, use the [nslookup server](nslookup-server) command.

## Syntax

```
lserver <DNSdomain>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<DNSdomain>` | Specifies the DNS domain for the initial server. |
| /? | Displays help at the command prompt. |
| /help | Displays help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [nslookup server](nslookup-server)