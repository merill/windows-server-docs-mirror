---
layout: Conceptual
title: tapicfg makedefault | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tapicfg-makedefault
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tapicfg makedefault command, which sets the default TAPI application directory partition for the domain.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-09-29T00:00:00.0000000Z
locale: en-us
document_id: 937a863f-e2a1-bed0-da77-e9234dfa6d21
document_version_independent_id: 5e7b141c-0284-edfc-4ff8-4afac65b41b1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tapicfg-makedefault.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tapicfg-makedefault
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tapicfg-makedefault.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: f9b83787-c41d-9e1f-1b68-d29f570a9df5
---

# tapicfg makedefault | Microsoft Learn

Sets the default TAPI application directory partition for the domain.

## Syntax

```
tapicfg makedefault /directory:<partitionname> [/domain:<domainname>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| makedefault `/directory:<partitionname>` | Required. Specifies the DNS name of the TAPI application directory partition set as the default partition for the domain. This name must be a fully-qualified domain name. |
| /domain: `<domainname>` | Specifies the DNS name of the domain for which the TAPI application directory partition is set as the default. If the domain name is not specified, the name of the local domain is used. |
| /? | Displays help at the command prompt. |

#### Remarks

- This command-line tool can be run on any computer that is a member of the domain.
- User-supplied text (such as the names of TAPI application directory partitions, servers, and domains) with International or Unicode characters are only displayed correctly if appropriate fonts and language support are installed.
- You can still use Internet Locator Service (ILS) servers in your organization, if ILS is needed to support certain applications, because TAPI clients running Windows XP or a Windows Server 2003 operating system can query either ILS servers or TAPI application directory partitions.
- You can use **tapicfg** to create or remove service connection points. If the TAPI application directory partition is renamed for any reason (for example, if you rename the domain in which it resides), you must remove the existing service connection point and create a new one that contains the new DNS name of the TAPI application directory partition to be published. Otherwise, TAPI clients are unable to locate and access the TAPI application directory partition. You can also remove a service connection point for maintenance or security purposes (for example, if you do not want to expose TAPI data on a specific TAPI application directory partition).

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [tapicfg install](tapicfg-install)
- [tapicfg remove](tapicfg-remove)
- [tapicfg publishscp](tapicfg-publishscp)
- [tapicfg removescp](tapicfg-removescp)
- [tapicfg show](tapicfg-show)