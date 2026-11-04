---
layout: Conceptual
title: bitsadmin getproxybypasslist | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-getproxybypasslist
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin getproxybypasslist command that retrieves the proxy bypass list for the specified job.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-01-06T00:00:00.0000000Z
locale: en-us
document_id: 04085693-1bf1-1cdc-408b-c9f94fb78f06
document_version_independent_id: 37efed71-850c-2108-bb71-939491ebee30
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-getproxybypasslist.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-getproxybypasslist
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-getproxybypasslist.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 55e77865-99e1-8a7c-ca35-e52fa8aa9cf3
---

# bitsadmin getproxybypasslist | Microsoft Learn

Applies to: Applies to: Windows Server (All supported versions)

The `bitsadmin /getproxybypasslist` command retrieves the proxy bypass list for the specified job.

## Syntax

```
bitsadmin /getproxybypasslist <job>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |

### Remarks

The bypass list contains the host names or IP addresses, or both, that aren't routed through a proxy. The list can contain `<local>` to refer to all servers on the same LAN. The list can be semicolon (;) or space-delimited.

## Examples

To retrieve the proxy bypass list for the job named *myDownloadJob*:

```
bitsadmin /getproxybypasslist myDownloadJob
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)