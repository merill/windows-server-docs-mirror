---
layout: Conceptual
title: dfsdiag testreferral | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/dfsdiag-testreferral
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the dfsdiag testreferral command, which checks Distributed File System (DFS) referrals.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4770b0fa-fcc8-00ea-138f-7afa99589468
document_version_independent_id: 76cf5ef5-2d84-8143-cfb8-161ca32a2579
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/dfsdiag-testreferral.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/dfsdiag-testreferral
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/dfsdiag-testreferral.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bec8e365-6efb-400e-c899-73469b837576
---

# dfsdiag testreferral | Microsoft Learn

Checks Distributed File System (DFS) referrals by performing the following tests:

- If you use the **DFSpath**\* parameter without arguments, the command validates that the referral list includes all trusted domains.
- If you specify a domain, the command performs a health check of domain controllers (`dfsdiag /testdcs`) and tests the site associations and domain cache of the local host.
- If you specify a domain and \SYSvol or \NETLOGON, the command performs the same domain controller health checks, along with checking that the time **To Live (TTL)** of SYSvol or NETLOGON referrals matches the default value of 900 seconds.
- If you specify a namespace root, the command performs the same domain controller health checks, along with performing a DFS configuration check (`dfsdiag /testdfsconfig`) and a namespace integrity check (`dfsdiag /testdfsintegrity`).
- If you specify a DFS folder (link), the command performs the same namespace root health checks, along with validating the site configuration for folder targets (dfsdiag /testsites) and validating the site association of the local host.

## Syntax

```
dfsdiag /testreferral /DFSpath:<DFS path to get referrals> [/full]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /DFSpath:`<path to get referrals>` | Can be one of the following:<br>- **Blank:** Tests only trusted domains.<br>- `\\Domain:` Tests only domain controller referrals.<br>- `\\Domain\SYSvol:` Tests only SYSvol referrals.<br>- `\\Domain\NETLOGON:` Tests only NETLOGON referrals.<br>- `\\<domain or server>\<namespace root>:` Tests only namespace root referrals.<br>- `\\<domain or server>\<namespace root>\<DFS folder>:` Tests only the DFS folder (link) referrals. |
| /full | Applies only to Domain and Root referrals. Verifies the consistency of site association information between the registry and active directory Domain Services (AD DS). |

## Examples

To check the Distributed File System (DFS) referrals in *contoso.com\MyNamespace*, type:

```
dfsdiag /testreferral /DFSpath:\\contoso.com\MyNamespace
```

To check the Distributed File System (DFS) referrals in all trusted domains, type:

```
dfsdiag /testreferral /DFSpath:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [dfsdiag command](dfsdiag)