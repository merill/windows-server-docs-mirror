---
layout: Conceptual
title: tapicfg removescp | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tapicfg-removescp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tapicfg removescp command, which removes a service connection point for a TAPI application directory partition.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-09-29T00:00:00.0000000Z
locale: en-us
document_id: e68264dd-a5c0-8b6e-e941-0430303a9340
document_version_independent_id: ac87e6d4-3514-c43c-1eb4-1df4104f27a5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tapicfg-removescp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tapicfg-removescp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tapicfg-removescp.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 69b1ba07-e312-1652-54b2-874dd46dfba6
---

# tapicfg removescp | Microsoft Learn

Removes a service connection point for a TAPI application directory partition.

## Syntax

```
tapicfg removescp /directory:<partitionname> [/domain:<domainname>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| removescp `/directory:<partitionname>` | Required. Specifies the DNS name of the TAPI application directory partition for which a service connection point is removed. |
| /domain: `<domainname>` | Specifies the DNS name of the domain from which the service connection point is removed. If the domain name isn't specified, the name of the local domain is used. |
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
- [tapicfg show](tapicfg-show)
- [tapicfg makedefault](tapicfg-makedefault)