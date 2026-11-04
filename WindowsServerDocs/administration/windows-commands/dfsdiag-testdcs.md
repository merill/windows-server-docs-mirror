---
layout: Conceptual
title: dfsdiag testdcs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/dfsdiag-testdcs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the dfsdiag testdcs command, which checks the configuration of domain controllers in the specified domain.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f6488fa4-b2da-d836-4feb-28034a3da08d
document_version_independent_id: bdf2891c-a413-3f53-3d06-3c646d00c40a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/dfsdiag-testdcs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/dfsdiag-testdcs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/dfsdiag-testdcs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 42d6eb59-0c87-ecfc-55a8-a439f90809f8
---

# dfsdiag testdcs | Microsoft Learn

Checks the configuration of domain controllers by performing the following tests on each domain controller in the specified domain:

- Verifies that the Distributed File System (DFS) Namespace service is running and that its startup type is set to **Automatic**.
- Checks for the support of site-costed referrals for NETLOGON and SYSvol.
- Verifies the consistency of the site association by hostname and IP address.

## Syntax

```
dfsdiag /testdcs [/domain:<domain_name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /domain:`<domain_name>` | Name of the domain to check. This parameter is optional. The default value is the local domain to which the local host is joined. |

## Examples

To verify the configuration of domain controllers in the *contoso.com* domain, type:

```
dfsdiag /testdcs /domain:contoso.com
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [dfsdiag command](dfsdiag)