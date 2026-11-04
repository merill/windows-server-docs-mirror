---
layout: Conceptual
title: bitsadmin util and getieproxy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-util-and-getieproxy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin util and getieproxy command, which retrieves the proxy usage for the given service account.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e2ccc5ba-d91d-1913-77e1-f81e70cd4d3f
document_version_independent_id: aa3f8b50-b35d-54b6-f30c-33606bcc5d44
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-util-and-getieproxy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-util-and-getieproxy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-util-and-getieproxy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cce76975-d14c-934f-acbb-c14c51525ace
---

# bitsadmin util and getieproxy | Microsoft Learn

Retrieves the proxy usage for the given service account. This command shows the value for each proxy usage, not just the proxy usage you specified for the service account. For details about setting the proxy usage for specific service accounts, see the [bitsadmin util and setieproxy](bitsadmin-util-and-setieproxy) command.

## Syntax

```
bitsadmin /util /getieproxy <account> [/conn <connectionname>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| account | Specifies the service account whose proxy settings you want to retrieve. Possible values include:<br>- LOCALSYSTEM<br>- NETWORKSERVICE<br>- LOCALSERVICE. |
| connectionname | Optional. Used with the **/conn** parameter to specify which modem connection to use. If you don't specify the **/conn** parameter, BITS uses the LAN connection. |

## Examples

To display the proxy usage for the NETWORK SERVICE account:

```
bitsadmin /util /getieproxy NETWORKSERVICE
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin util command](bitsadmin-util)
- [bitsadmin command](bitsadmin)