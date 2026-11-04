---
layout: Conceptual
title: Deploy Hyperconverged Infrastructure with Windows Admin Center | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/use/deploy-hyperconverged-infrastructure
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn how to deploy a hyperconverged infrastructure by using Windows Admin Center.
ms.topic: install-set-up-deploy
author: davannaw-msft
ms.author: dawhite
ms.date: 2019-11-04T00:00:00.0000000Z
locale: en-us
document_id: 5b3875df-4df3-5f7b-0c59-5ae332234e0b
document_version_independent_id: 2bce00dd-296f-0132-7f02-70b89f300285
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/use/deploy-hyperconverged-infrastructure.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/use/deploy-hyperconverged-infrastructure
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/use/deploy-hyperconverged-infrastructure.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 05f3fa68-aad8-be52-673f-fc2ae353de78
---

# Deploy Hyperconverged Infrastructure with Windows Admin Center | Microsoft Learn

You can use Windows Admin Center [version 1910](../overview) or later to deploy a hyperconverged infrastructure by using two or more suitable Windows servers. This feature takes the form of a multistage workflow that guides you through installing features, configuring networking, creating the cluster, and deploying Storage Spaces Direct and/or software-defined networking (SDN).

Important

Windows Admin Center doesn't support Azure Stack HCI OS deployment. To learn about deploying Azure Local infrastructure, see the [Azure Local documentation](/en-us/azure/azure-local/deploy/create-cluster).

## Undo and start over

Use the following Windows PowerShell cmdlets to undo changes that the workflow made and start over.

### Remove virtual machines or other clustered resources

If you created any virtual machines or other clustered resources, such as the network controllers for SDN, remove them first.

For example, to remove resources by name, use this cmdlet:

```PowerShell
Get-ClusterResource -Name "<NAME>" | Remove-ClusterResource
```

### Undo the storage steps

If you enabled Storage Spaces Direct, disable it by using the following script.

Warning

These cmdlets permanently delete any data in Storage Spaces Direct volumes. You can't undo this action.

```PowerShell
Get-VirtualDisk | Remove-VirtualDisk
Get-StoragePool -IsPrimordial $False | Remove-StoragePool
Disable-ClusterS2D
```

### Undo the clustering steps

If you created a cluster, remove it by using this cmdlet:

```PowerShell
Remove-Cluster -CleanUpAD
```

To also remove cluster validation reports, run this cmdlet on every server that was part of the cluster:

```PowerShell
Get-ChildItem C:\Windows\cluster\Reports\ | Remove-Item
```

### Undo the networking steps

Run the following cmdlets on every server that was part of the cluster.

If you created a Hyper-V virtual switch, use this cmdlet:

```PowerShell
Get-VMSwitch | Remove-VMSwitch
```

The `Remove-VMSwitch` cmdlet automatically removes any virtual adapters and undoes switch-embedded teaming of physical adapters.

If you modified network adapter properties such as name, IPv4 address, and VLAN ID, use the following cmdlets.

Warning

These cmdlets remove network adapter names and IP addresses. Make sure that you have the information that you need to connect afterward, such as an adapter for management that's excluded from the script. Also make sure that you know how the servers are connected in terms of physical properties like MAC address, not just the adapter's name in Windows.

```PowerShell
Get-NetAdapter | Where Name -Ne "Management" | Rename-NetAdapter -NewName $(Get-Random)
Get-NetAdapter | Where Name -Ne "Management" | Get-NetIPAddress -ErrorAction SilentlyContinue | Where AddressFamily -Eq IPv4 | Remove-NetIPAddress
Get-NetAdapter | Where Name -Ne "Management" | Set-NetAdapter -VlanID 0
```

You're now ready to start the workflow.