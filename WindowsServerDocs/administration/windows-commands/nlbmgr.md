---
layout: Conceptual
title: nlbmgr | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nlbmgr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nlbmgr command, which helps you to configure and manage your Network Load Balancing clusters and all cluster hosts from a single computer, using the Network Load Balancing Manager.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4896598b-46a6-111b-24e1-c402f1e2a6c0
document_version_independent_id: 42ea21d2-a08f-e19b-047f-2fda9c26a1ce
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nlbmgr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nlbmgr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nlbmgr.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 45f99987-d099-d9c1-4c92-1a0b904acc1e
---

# nlbmgr | Microsoft Learn

Configure and manage your Network Load Balancing clusters and all cluster hosts from a single computer, using the Network Load Balancing Manager. You can also use this command to replicate the cluster configuration to other hosts.

You can start the Network Load Balancing Manager from the command-line using the command **nlbmgr.exe**, which is installed in the **systemroot\System32** folder.

## Syntax

```
nlbmgr [/noping][/hostlist <filename>][/autorefresh <interval>][/help | /?]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /noping | Prevents the Network Load Balancing Manager from pinging the hosts prior to trying to contact them through Windows Management Instrumentation (WMI). Use this option if you have disabled Internet Control Message Protocol (ICMP) on all available network adapters. If the Network Load Balancing Manager attempts to contact a host that isn't available, you'll experience a delay when using this option. |
| /hostlist `<filename>` | Loads the hosts specified in filename into the Network Load Balancing Manager. |
| /autorefresh `<interval>` | Causes the Network Load Balancing Manager to refresh its host and cluster information every `<interval>` seconds. If no interval is specified, the information is refreshed every 60 seconds. |
| /? | Displays help at the command prompt. |
| /help | Displays help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [NetworkLoadBalancingClusters cmdlets reference](/en-us/powershell/module/networkloadbalancingclusters)