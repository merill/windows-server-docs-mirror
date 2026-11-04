---
layout: Conceptual
title: ksetup delenctypeattr | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-delenctypeattr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup delenctypeattr, which removes the encryption type attribute for the domain.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9c8d936e-f30b-878f-e49d-adc89a4e34ea
document_version_independent_id: 3c0904e9-b06d-7629-b8a7-24d07f94a668
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-delenctypeattr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-delenctypeattr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-delenctypeattr.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: f5194e30-f87c-cff2-5b54-a01c472e9aa7
---

# ksetup delenctypeattr | Microsoft Learn

Removes the encryption type attribute for the domain. A status message is displayed upon successful or failed completion.

You can view the encryption type for the Kerberos ticket-granting ticket (TGT) and the session key, by running the **klist** command and viewing the output. You can set the domain to connect to and use, by running the `ksetup /domain <domainname>` command.

## Syntax

```
ksetup /delenctypeattr <domainname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<domainname>` | Name of the domain to which you want to establish a connection. You can use either the fully-qualified domain name or a simple form of the name, such as corp.contoso.com or contoso. |

### Examples

To determine the current encryption types that are set on this computer, type:

```
klist
```

To set the domain to mit.contoso.com, type:

```
ksetup /domain mit.contoso.com
```

To verify what the encryption type attribute is for the domain, type:

```
ksetup /getenctypeattr mit.contoso.com
```

To remove the set encryption type attribute for the domain mit.contoso.com, type:

```
ksetup /delenctypeattr mit.contoso.com
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [klist command](klist)
- [ksetup command](ksetup)
- [ksetup domain command](ksetup-domain)
- [ksetup addenctypeattr command](ksetup-addenctypeattr)
- [ksetup setenctypeattr command](ksetup-setenctypeattr)