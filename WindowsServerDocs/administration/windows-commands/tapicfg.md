---
layout: Conceptual
title: tapicfg | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tapicfg
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tapicfg commands, which creates, removes, or displays a TAPI application directory partition, or sets a default TAPI application directory partition.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: ff026783-8c6f-3eb8-b834-724879aaa361
document_version_independent_id: e7247191-7356-c4dc-3f18-39695d7a182d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tapicfg.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tapicfg
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tapicfg.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: b8009d39-5425-e823-6ab0-5f70ffd5ee88
---

# tapicfg | Microsoft Learn

Creates, removes, or displays a TAPI application directory partition, or sets a default TAPI application directory partition. TAPI 3.1 clients can use the information in this application directory partition with the directory service locator service to find and communicate with TAPI directories. You can also use **tapicfg** to create or remove service connection points, which enable TAPI clients to efficiently locate TAPI application directory partitions in a domain.

This command-line tool can be run on any computer that is a member of the domain.

## Syntax

```
tapicfg install
tapicfg remove
tapicfg publishscp
tapicfg removescp
tapicfg show
tapicfg makedefault
```

### Parameters

| Parameters | Description |
| --- | --- |
| [tapicfg install](tapicfg-install) | Creates a TAPI application directory partition. |
| [tapicfg remove](tapicfg-remove) | Removes a TAPI application directory partition. |
| [tapicfg publishscp](tapicfg-publishscp) | Creates a service connection point to publish a TAPI application directory partition. |
| [tapicfg removescp](tapicfg-removescp) | Removes a service connection point for a TAPI application directory partition. |
| [tapicfg show](tapicfg-show) | Displays the names and locations of the TAPI application directory partitions in the domain. |
| [tapicfg makedefault](tapicfg-makedefault) | Sets the default TAPI application directory partition for the domain. |

#### Remarks

- You must be a member of the **Enterprise Admins** group in Active Directory to run either **tapicfg install** (to create a TAPI application directory partition) or **tapicfg remove** (to remove a TAPI application directory partition).
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
- [tapicfg makedefault](tapicfg-makedefault)