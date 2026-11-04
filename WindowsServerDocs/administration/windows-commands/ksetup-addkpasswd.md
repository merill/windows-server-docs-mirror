---
layout: Conceptual
title: ksetup addkpasswd | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-addkpasswd
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup addkpasswd command, which adds a Kerberos password (kpasswd) server address for a realm.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 88257da5-8b6e-2fec-3537-1f9d63bff8ea
document_version_independent_id: 6bb20a85-e796-e442-3dec-887c67966b39
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-addkpasswd.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-addkpasswd
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-addkpasswd.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 61efb2d8-8437-c41e-6c34-7ffb86760a4d
---

# ksetup addkpasswd | Microsoft Learn

Adds a Kerberos password (kpasswd) server address for a realm.

## Syntax

```
ksetup /addkpasswd <realmname> [<kpasswdname>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<realmname>` | Specifies the uppercase DNS name, such as CORP.CONTOSO.COM, and is listed as the default realm or **Realm=** when **ksetup** is run. |
| `<kpasswdname>` | Specifies the Kerberos password server. It's stated as a case-insensitive, fully-qualified domain name, such as mitkdc.contoso.com. If the KDC name is omitted, DNS might be used to locate KDCs. |

#### Remarks

- If the Kerberos realm that the workstation will be authenticating to supports the Kerberos change password protocol, you can configure a client computer running the Windows operating system to use a Kerberos password server.
- You can add additional KDC names one at a time.

### Examples

To configure the CORP.CONTOSO.COM realm to use the non-Windows KDC server, mitkdc.contoso.com, as the password server, type:

```
ksetup /addkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```

To verify the KDC name is set, type `ksetup` and then view the output, looking for the text, **kpasswd =**. If you don't see the text, it means the mapping hasn't been configured.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)
- [ksetup delkpasswd command](ksetup-delkpasswd)