---
layout: Conceptual
title: tapicfg remove | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tapicfg-remove
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tapicfg remove command, which removes a TAPI application directory partition.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-09-29T00:00:00.0000000Z
locale: en-us
document_id: 2dd8f973-ba2e-65e4-3cde-288eda573883
document_version_independent_id: ea22283a-62dc-c2e3-667d-84ee9d844f73
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tapicfg-remove.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tapicfg-remove
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tapicfg-remove.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 4253250d-e46f-0e0d-454f-14ee5c711c50
---

# tapicfg remove | Microsoft Learn

Removes a TAPI application directory partition.

Important

You must be a member of the Enterprise Admins group in active directory to run this command.

## Syntax

```
tapicfg remove /directory:<partitionname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| remove `/directory:<partitionname>` | Required. Specifies the DNS name of the TAPI application directory partition to be removed. Note that this name must be a fully-qualified domain name. |
| /? | Displays help at the command prompt. |

#### Remarks

- This command-line tool can be run on any computer that is a member of the domain.
- User-supplied text (such as the names of TAPI application directory partitions, servers, and domains) with International or Unicode characters are only displayed correctly if appropriate fonts and language support are installed.
- You can still use Internet Locator Service (ILS) servers in your organization, if ILS is needed to support certain applications, because TAPI clients running Windows XP or a Windows Server 2003 operating system can query either ILS servers or TAPI application directory partitions.
- You can use **tapicfg** to create or remove service connection points. If the TAPI application directory partition is renamed for any reason (for example, if you rename the domain in which it resides), you must remove the existing service connection point and create a new one that contains the new DNS name of the TAPI application directory partition to be published. Otherwise, TAPI clients are unable to locate and access the TAPI application directory partition. You can also remove a service connection point for maintenance or security purposes (for example, if you do not want to expose TAPI data on a specific TAPI application directory partition).

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [tapicfg install](tapicfg-install)
- [tapicfg publishscp](tapicfg-publishscp)
- [tapicfg removescp](tapicfg-removescp)
- [tapicfg show](tapicfg-show)
- [tapicfg makedefault](tapicfg-makedefault)