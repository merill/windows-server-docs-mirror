---
layout: Conceptual
title: ksetup setenctypeattr | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-setenctypeattr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup setenctypeattr command, which sets the encryption type attribute for the domain.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 79a15d2b-08b6-c468-45f6-1cfcf12af35d
document_version_independent_id: e713f06a-6443-5396-6fc7-f8c62b254dfd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-setenctypeattr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-setenctypeattr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-setenctypeattr.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: c098b1b6-2686-5295-d014-cc33c69ea7f7
---

# ksetup setenctypeattr | Microsoft Learn

Sets the encryption type attribute for the domain. A status message is displayed upon successful or failed completion.

You can view the encryption type for the Kerberos ticket-granting ticket (TGT) and the session key, by running the **klist** command and viewing the output. You can set the domain to connect to and use, by running the `ksetup /domain <domainname>` command.

## Syntax

```
ksetup /setenctypeattr <domainname> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<domainname>` | Name of the domain to which you want to establish a connection. Use the fully qualified domain name or a simple form of the name, such as corp.contoso.com or contoso. |
| encryption type | Must be one of the following supported encryption types:<br>- DES-CBC-CRC<br>- DES-CBC-MD5<br>- RC4-HMAC-MD5<br>- AES128-CTS-HMAC-SHA1-96<br>- AES256-CTS-HMAC-SHA1-96 |

#### Remarks

- You can set or add multiple encryption types by separating the encryption types in the command with a space. However, you can only do so for one domain at a time.

### Examples

To view the encryption type for the Kerberos ticket-granting ticket (TGT) and the session key, type:

```
klist
```

To set the domain to corp.contoso.com, type:

```
ksetup /domain corp.contoso.com
```

To set the encryption type attribute to AES-256-CTS-HMAC-SHA1-96 for the domain corp.contoso.com, type:

```
ksetup /setenctypeattr corp.contoso.com AES-256-CTS-HMAC-SHA1-96
```

To verify that the encryption type attribute was set as intended for the domain, type:

```
ksetup /getenctypeattr corp.contoso.com
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [klist command](klist)
- [ksetup command](ksetup)
- [ksetup domain command](ksetup-domain)
- [ksetup addenctypeattr command](ksetup-addenctypeattr)
- [ksetup getenctypeattr command](ksetup-getenctypeattr)
- [ksetup delenctypeattr command](ksetup-delenctypeattr)