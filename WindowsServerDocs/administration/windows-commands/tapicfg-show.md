---
layout: Conceptual
title: tapicfg show | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tapicfg-show
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tapicfg show command, which displays the names and locations of the TAPI application directory partitions in the domain.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-09-29T00:00:00.0000000Z
locale: en-us
document_id: 8316e787-eb43-26ee-639d-fa7be4beba86
document_version_independent_id: f872cad1-c80b-5546-f322-5cad74626292
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tapicfg-show.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tapicfg-show
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tapicfg-show.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: ebaec494-26a3-17fb-2679-eeb2fb8e8c8a
---

# tapicfg show | Microsoft Learn

Displays the names and locations of the TAPI application directory partitions in the domain.

## Syntax

```
tapicfg show [/defaultonly] [/domain:<domainname>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /default only | Displays the names and locations of only the default TAPI application directory partition in the domain. |
| /domain: `<domainname>` | Specifies the DNS name of the domain for which the TAPI application directory partitions are displayed. If the domain name isn't specified, the name of the local domain is used. |
| /? | Displays help at the command prompt. |

#### Remarks

- This command-line tool can be run on any computer that is a member of the domain.
- User-supplied text (such as the names of TAPI application directory partitions, servers, and domains) with International or Unicode characters are only displayed correctly if appropriate fonts and language support are installed.
- You can still use Internet Locator Service (ILS) servers in your organization, if ILS is needed to support certain applications, because TAPI clients running Windows XP or a Windows Server 2003 operating system can query either ILS servers or TAPI application directory partitions.
- You can use **tapicfg** to create or remove service connection points. If the TAPI application directory partition is renamed for any reason (for example, if you rename the domain in which it resides), you must remove the existing service connection point and create a new one that contains the new DNS name of the TAPI application directory partition to be published. Otherwise, TAPI clients are unable to locate and access the TAPI application directory partition. You can also remove a service connection point for maintenance or security purposes (for example, if you do not want to expose TAPI data on a specific TAPI application directory partition).

## Example

To display the name of the default TAPI application directory partition for the new domain, type:

```
tapicfg show /defaultonly
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [tapicfg install](tapicfg-install)
- [tapicfg remove](tapicfg-remove)
- [tapicfg publishscp](tapicfg-publishscp)
- [tapicfg removescp](tapicfg-removescp)
- [tapicfg makedefault](tapicfg-makedefault)