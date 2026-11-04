---
layout: Conceptual
title: Cluster affinity | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/failover-clustering/cluster-affinity
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: failover-clustering
ms.update-cycle: 1095-days
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-20T00:00:00.0000000Z
description: This article describes failover cluster affinity and antiaffinity levels
locale: en-us
document_id: 9e3fbba0-6f07-6b29-a184-fb2b31414b69
document_version_independent_id: baafd6b1-5edd-944a-5c2b-9f22c285c4cb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/failover-clustering/Cluster-Affinity.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: failover-clustering/cluster-affinity
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/failover-clustering/Cluster-Affinity.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: e2741bd6-ea1d-b86c-49a4-6be89e1ee703
---

# Cluster affinity | Microsoft Learn

A failover cluster can hold many roles that can move between nodes and run. There are times when certain roles (that is, virtual machines, resource groups, and so on) should not run on the same node. This could be because of resource consumption, memory usage, and so on. For example, there are two virtual machines that are memory and CPU intensive and if the two virtual machines are running on the same node, one or both of the virtual machines could have performance impact issues. This article will explain cluster antiaffinity levels and how you can use them.

## What is Affinity and AntiAffinity?

Affinity is a rule you would set up that establishes a relationship between two or more roles (i,e, virtual machines, resource groups, and so on) to keep them together. AntiAffinity is the same but is used to try to keep the specified roles apart from each other. Failover Clusters use AntiAffinity for its roles. More specifically, the [AntiAffinityClassNames](/en-us/previous-versions/windows/desktop/mscs/groups-antiaffinityclassnames) parameter defined on the roles so they do not run on the same node.

## AntiAffinityClassnames

When looking at the properties of a group, the parameter AntiAffinityClassNames is blank as a default. In the examples below, Group1 and Group2 should be separated from running on the same node. To view the property, the PowerShell command and result would be:

```powershell
Get-ClusterGroup Group1 | fl AntiAffinityClassNames
    AntiAffinityClassNames : {}

Get-ClusterGroup Group2 | fl AntiAffinityClassNames
    AntiAffinityClassNames : {}
```

Because AntiAffinityClassNames are not defined as a default, these roles can run together or apart. The goal is to keep them separated. The value for AntiAffinityClassNames can be whatever you want them to be, they just have to be the same. Say that Group1 and Group2 are domain controllers running in virtual machines and they would be best served running on different nodes. Because these are domain controllers, I will use DC for the class name. To set the value, the PowerShell command and results would be:

```powershell
$AntiAffinity = New-Object System.Collections.Specialized.StringCollection
$AntiAffinity.Add("DC")
(Get-ClusterGroup -Name "Group1").AntiAffinityClassNames = $AntiAffinity
(Get-ClusterGroup -Name "Group2").AntiAffinityClassNames = $AntiAffinity

$AntiAffinity = New-Object System.Collections.Specialized.StringCollection
$AntiAffinity.Add("DC")
(Get-ClusterGroup -Name "Group1").AntiAffinityClassNames = $AntiAffinity
(Get-ClusterGroup -Name "Group2").AntiAffinityClassNames = $AntiAffinity

Get-ClusterGroup "Group1" | fl AntiAffinityClassNames
    AntiAffinityClassNames : {DC}

Get-ClusterGroup "Group2" | fl AntiAffinityClassNames
    AntiAffinityClassNames : {DC}
```

Now that they are set, failover clustering will attempt to keep them apart.

The AntiAffinityClassName parameter is a "soft" block. Meaning, it will try to keep them apart, but if it cannot, it will still allow them to run on the same node. For example, the groups are running on a two-node failover cluster. If one node needs to go down for maintenance, it would mean both groups would be up and running on the same node. In this case, it would be okay to have this. It may not be the most ideal, but both virtual machines will still run within acceptable performance ranges.

## I need more

As mentioned, AntiAffinityClassNames is a soft block. But what if a hard block is needed? The virtual machines cannot be run on the same node; otherwise, performance impact will occur and cause some services to possibly go down.

For those cases, there is another cluster property of ClusterEnforcedAntiAffinity. This antiaffinity level will prevent at all costs any of the same AntiAffinityClassNames values from running on the same node.

To view the property and value, the PowerShell command (and result) would be:

```powershell
Get-Cluster | fl ClusterEnforcedAntiAffinity
    ClusterEnforcedAntiAffinity : 0
```

The value of "0" means it is disabled and not to be enforced. The value of "1" enables it and is the hard block. To enable this hard block, the command (and result) is:

```powershell
(Get-Cluster).ClusterEnforcedAntiAffinity = 1
    ClusterEnforcedAntiAffinity : 1
```

When both of these are set, the group will be prevented from coming online together. If they are on the same node, this is what you would see in Failover Cluster Manager.

![Cluster Affinity](media/cluster-affinity/cluster-affinity-1.png)

In a PowerShell listing of the groups, you would see this:

```powershell
Get-ClusterGroup

Name       State
----       -----
Group1     Offline(Anti-Affinity Conflict)
Group2     Online
```

## Additional Comments

- Ensure you are using the proper AntiAffinity setting depending on the needs.
- Keep in mind that in a two-node scenario and ClusterEnforcedAntiAffinity, if one node is down, both groups will not run.
- The use of Preferred Owners on groups can be combined with AntiAffinity in a three or more node cluster.
- The AntiAffinityClassNames and ClusterEnforcedAntiAffinity settings will only take place after a recycling of the resources. That is, you can set them, but if both groups are online on the same node when set, they will both continue to remain online.