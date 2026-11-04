---
layout: Conceptual
title: ksetup delkpasswd | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-delkpasswd
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup delkpasswd command, which removes a Kerberos password server (kpasswd) for a realm.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e090cfb7-932a-f6bc-21c9-9d76d5267f84
document_version_independent_id: a2027484-9bd7-e541-7a9f-352d2d858813
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-delkpasswd.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-delkpasswd
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-delkpasswd.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ed39e0f9-b063-ee20-3446-f7ca5d2b3408
---

# ksetup delkpasswd | Microsoft Learn

Removes a Kerberos password server (kpasswd) for a realm.

## Syntax

```
ksetup /delkpasswd <realmname> <kpasswdname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<realmname>` | Specifies the uppercase DNS name, such as CORP.CONTOSO.COM, and is listed as the default realm or **Realm=** when **ksetup** is run. |
| `<kpasswdname>` | Specifies the Kerberos password server. It's stated as a case-insensitive, fully-qualified domain name, such as mitkdc.contoso.com. If the KDC name is omitted, DNS might be used to locate KDCs. |

### Examples

To make sure the realm CORP.CONTOSO.COM uses the non-Windows KDC server mitkdc.contoso.com as the password server, type:

```
ksetup /delkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```

To make sure the realm CORP.CONTOSO.COM is not mapped to a Kerberos password server (the KDC name), type `ksetup` on the Windows computer and then view the output.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)
- [ksetup delkpasswd command](ksetup-delkpasswd)