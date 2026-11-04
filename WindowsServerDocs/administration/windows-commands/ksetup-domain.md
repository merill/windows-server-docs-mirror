---
layout: Conceptual
title: ksetup domain | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-domain
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup domain command, which sets the domain name for all Kerberos operations.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 43fa796a-522e-225a-dc15-fd8888adcf7d
document_version_independent_id: 97cf7952-1ed0-88c0-8460-8db0d60cab71
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-domain.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-domain
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-domain.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: d90eb351-a3f6-2143-2231-c98163a0ffdc
---

# ksetup domain | Microsoft Learn

Sets the domain name for all Kerberos operations.

## Syntax

```
ksetup /domain <domainname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<domainname>` | Name of the domain to which you want to establish a connection. Use the fully-qualified domain name or a simple form of the name, such as contoso.com or contoso. |

### Examples

To establish a connection to a valid domain, such as Microsoft, by using the `ksetup /mapuser` subcommand, type:

```
ksetup /mapuser principal@realm domain-user /domain domain-name
```

After a successful connection, you'll receive a new TGT or an existing TGT will be refreshed.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)
- [ksetup mapuser command](ksetup-mapuser)