---
layout: Conceptual
title: ksetup setrealm | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-setrealm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup setrealm command, which sets the name of a Kerberos realm.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: fda30bce-9367-0d07-fbfa-a477a4fa045f
document_version_independent_id: 8e591823-dd24-f761-2f57-24b7ee3447bd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-setrealm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-setrealm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-setrealm.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 6f9f0f72-eb57-fc72-b9a3-8c9a21fdb443
---

# ksetup setrealm | Microsoft Learn

Sets the name of a Kerberos realm.

Important

Setting the Kerberos realm on a domain controller isn't supported. Attempting to do so causes a warning and a command failure.

## Syntax

```
ksetup /setrealm <DNSdomainname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<DNSdomainname>` | Specifies the uppercase DNS name, such as CORP.CONTOSO.COM. You can use the fully-qualified domain name or a simple form of the name. If you don't use uppercase for the DNS name, you'll be asked for verification to continue. |

### Examples

To set the realm of this computer to a specific domain name, and to restrict access by a non-domain controller just to the CONTOSO Kerberos realm, type:

```
ksetup /setrealm CONTOSO
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)
- [ksetup removerealm](ksetup-removerealm)