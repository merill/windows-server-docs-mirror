---
layout: Conceptual
title: Removing servers in Storage Spaces Direct | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/remove-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
ms.author: roharwoo
ms.topic: how-to
author: robinharwood
description: How to remove servers from a Storage Spaces Direct cluster in Windows Server.
ms.date: 2017-02-05T00:00:00.0000000Z
locale: en-us
document_id: 0256700b-cb40-0a0f-99bd-b4ce983109ca
document_version_independent_id: 4b86bed0-6f83-5cbd-5008-80e611f4c401
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/remove-servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/remove-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/remove-servers.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: bd199841-3a86-aa84-bf71-dedf9448272b
---

# Removing servers in Storage Spaces Direct | Microsoft Learn

This topic describes how to remove servers in [Storage Spaces Direct](storage-spaces-direct-overview) using PowerShell.

## Remove a server but leave its drives

If you intend to add the server back into the cluster soon, or if you intend to keep its drives by moving them to another server, you can remove the server from the cluster *without* removing its drives from the storage pool. This is the default behavior if you use Failover Cluster Manager to remove the server.

Use the [Remove-ClusterNode](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831694%28v=ws.11%29) cmdlet in PowerShell:

```PowerShell
Remove-ClusterNode <Name>
```

This cmdlet succeeds quickly, regardless of any capacity considerations, because the storage pool "remembers" the missing drives and expects them to come back. There is no data movement away from the missing drives. While they remain missing, their **OperationalStatus** will show as "Lost Communication", and your volumes will show "Incomplete".

When the drives come back, they are automatically detected and re-associated with the pool, even if they are now in a new server.

Warning

Do not distribute drives with pool data from one server into multiple other servers. For example, if one server with ten drives fails (because its motherboard or boot drive failed, for instance), you **can** move all ten drives into one new server, but you **cannot** move each of them separately into different other servers.

## Remove a server and its drives

If you want to permanently remove a server from the cluster (sometimes referred to as scaling-in), you can remove the server from the cluster *and* remove its drives from the storage pool.

Use the **Remove-ClusterNode** cmdlet with the optional **-CleanUpDisks** flag:

```PowerShell
Remove-ClusterNode <Name> -CleanUpDisks
```

This cmdlet might take a long time (sometimes many hours) to run because Windows must move all the data stored on that server to other servers in the cluster. Once this is complete, the drives are permanently removed from the storage pool, returning affected volumes to a healthy state.

### Requirements

To permanently scale-in (remove a server *and* its drives), your cluster must meet the following two requirements. If it doesn't, the **Remove-ClusterNode -CleanUpDisks** cmdlet will return an error immediately, before it begins any data movement, to minimize disruption.

#### Enough capacity

First, you must have enough storage capacity in the remaining servers to accommodate all your volumes.

For example, if you have four servers, each with 10 x 1 TB drives, you have 40 TB of total physical storage capacity. After removing one server and all its drives, you will have 30 TB of capacity left. If the footprints of your volumes are more than 30 TB together, they won't fit in the remaining servers, so the cmdlet will return an error and not move any data.

#### Enough fault domains

Second, you must have enough fault domains (typically servers) to provide the resiliency of your volumes.

For example, if your volumes use three-way mirroring at the server level for resiliency, they cannot be fully healthy unless you have at least three servers. If you have exactly three servers, and then attempt to remove one and all its drives, the cmdlet will return an error and not move any data.

This table shows the minimum number of fault domains required for each resiliency type.

| Resiliency | Minimum required fault domains |
| --- | --- |
| Two-way mirror | 2 |
| Three-way mirror | 3 |
| Dual parity | 4 |

Note

It is okay to briefly have fewer servers, such as during failures or maintenance. However, in order for volumes to return to a fully healthy state, you must have the minimum number of servers listed above.

## Additional References

- [Storage Spaces Direct overview](storage-spaces-direct-overview)