---
layout: Conceptual
title: bitsadmin util | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-util
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin util command, which lists the Util switches.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7537b624-95b2-6b3b-8c8d-9b20f1897331
document_version_independent_id: 0924c9d7-1df5-f70d-c867-a1cda4ca5984
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-util.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-util
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-util.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e191d027-c6d5-eb5c-7ca0-84be25497e3b
---

# bitsadmin util | Microsoft Learn

Lists the **/util** switches.

Lists the **util** switches.

## Syntax

```
bitsadmin /util /help
bitsadmin /util /getieproxy
bitsadmin /util /repairservice
bitsadmin /util /setieproxy
bitsadmin /util /version
```

### Parameters

| Parameter | Description |
| --- | --- |
| [bitsadmin util and help](bitsadmin-util-and-help) | Displays the command-line usage for the /Util switches. You can also specify /?. |
| [bitsadmin util and getieproxy](bitsadmin-util-and-getieproxy) | Retrieves the proxy usage for the given service account. |
| [bitsadmin util and repairservice](bitsadmin-util-and-repairservice) | Repairs known issues with BITS service. |
| [bitsadmin util and setieproxy](bitsadmin-util-and-setieproxy) | Specifies proxy settings to use when transferring files using a service account. |
| [bitsadmin util and version](bitsadmin-util-and-version) | Displays the version of the BITS service. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)