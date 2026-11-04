---
layout: Conceptual
title: Cross Domain Cluster Migration in Windows Server 2016/2019 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/failover-clustering/cluster-domain-migration
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: failover-clustering
ms.update-cycle: 1095-days
description: This article describes moving a Windows Server 2019 cluster from one domain to another
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2023-11-02T00:00:00.0000000Z
locale: en-us
document_id: 9847497d-26a0-d1e5-9562-18d01498f398
document_version_independent_id: 0e4cad5b-d3f9-7e4d-d86b-6c2d7fdb642e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/failover-clustering/Cluster-Domain-Migration.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: failover-clustering/cluster-domain-migration
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/failover-clustering/Cluster-Domain-Migration.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: b576d969-66fc-9873-3479-3823787e5dd5
---

# Cross Domain Cluster Migration in Windows Server 2016/2019 | Microsoft Learn

This article provides an overview for moving Windows Server failover clusters from one domain to another.

## Why migrate between domains

There are several scenarios where migrating a cluster from one domain to another is necessary.

- Company A merges with Company B and must move all clusters into Company A domain
- Clusters are built in the main datacenter and shipped out to remote locations
- Cluster was built as a workgroup cluster and now needs to be part of a domain
- Cluster was built as a domain cluster and now needs to be part of a workgroup
- Cluster is being moved to one area of the company to another and is a different subdomain

Microsoft doesn't provide support to administrators who try to move resources from one domain to another if the underlying application operation is unsupported. For example, Microsoft doesn't provide support to administrators who try to move a Microsoft Exchange server from one domain to another.

Warning

We recommend that you perform a full backup of all shared storage in the cluster before you move the cluster.

## Windows Server 2016 and earlier

In Windows Server 2016 and earlier, the Cluster service didn't have the capability of moving from one domain to another. This was due to the increased dependence on Active Directory Domain Services and the virtual names created.

## Options

In order to do such a move, there are two options.

The first option involves destroying the cluster and rebuilding it in the new domain.

![An animation of the steps to destroy a cluster, move nodes to a new domain, and recreate the cluster in a new domain.](media/cross-domain-cluster-migration/cross-cluster-domain-migration-1.gif)

As the animation shows, this option is destructive with the steps being:

1. Destroy the Cluster.
2. Change the domain membership of the nodes into the new domain.
3. Recreate the Cluster as new in the updated domain. This would entail having to recreate all the resources.

The second option is less destructive but requires additional hardware as a new cluster would need to be built in the new domain. Once the cluster is in the new domain, run the **Cluster Migration Wizard** to migrate the resources. The Cluster Migration Wizard doesn't migrate data, another tool is required, such as [Storage Migration Service](../storage/storage-migration-service/overview) once cluster support is added.

![An animation of the steps to create a new cluster in a new domain using the Cluster Migration Wizard, including decommissioning the old cluster.](media/cross-domain-cluster-migration/cross-cluster-domain-migration-2.gif)

As the animation shows, this option isn't destructive but does require either different hardware or a node from the existing cluster that has been removed.

1. Create a new cluster in the new domain while still having the old cluster available.
2. Use the [Cluster Migration Wizard](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754481%28v=ws.10%29) to migrate all the resources to the new cluster. Reminder, the Cluster Migration Wizard doesn't copy data, which needs to be done separately.
3. Decommission or destroy the old cluster.

In both options, the new cluster would need to have all [cluster-aware applications](/en-us/previous-versions/windows/desktop/mscs/cluster-aware-applications) installed, drivers updated, and testing to ensure functionality. If data also needs to be moved, this increases the time it takes to complete this process.

## Windows Server 2019

In Windows Server 2019, we introduced cross cluster domain migration capabilities. The scenarios, as previously mentioned, can easily be performed as the need of rebuilding is no longer needed.

Moving a cluster from one domain is a straight-forward process that can be accomplished using two PowerShell cmdlets:

- `New-ClusterNameAccount` – creates a Cluster Name Account in Active Directory
- `Remove-ClusterNameAccount` – removes the Cluster Name Accounts from Active Directory

    Note

    The cmdlet `Remove-ClusterNameAccount` might not run successfully. If you encounter an issue, follow the steps for Windows Server 2016 and earlier. Microsoft is aware of the problem.

The process is to change the cluster from one domain to a workgroup and back to the new domain. The need to destroy a cluster, rebuild a cluster, or install applications isn't a requirement. For example:

![An animation demonstrating how a cluster is migrated from the previous domain to a new domain.](media/cross-domain-cluster-migration/cross-cluster-domain-migration-3.gif)

## Migrating a cluster to a new domain

In the following steps, a cluster is being moved from the Contoso.com domain to the new Fabrikam.com domain. The cluster name is *CLUSCLUS* and with a file server role called *FS-CLUSCLUS*.

1. Create a local Administrator account with the same name and password on all servers in the cluster. This might be needed to log in while the servers are moving between domains.
2. Sign in to the first server with a domain user or administrator account that has Active Directory permissions to the Cluster Name Object (CNO), Virtual Computer Objects (VCO), has access to the Cluster, and open PowerShell.
3. Ensure all Cluster Network Name resources are in an offline state and run the following command to remove the Active Directory objects that the cluster might have.

    Note

    - If you can't delete cluster name objects using the `-Cluster CLUSCLUS` option, either remove the `-Cluster` option or execute `-Cluster <Node Name>`
    - If you can't delete cluster name objects using the `-DeleteComputerObjects` option, update the CNO object permissions to give the VCO account full control of the CNO in advance.

    ```powershell
    Remove-ClusterNameAccount -Cluster CLUSCLUS -DeleteComputerObjects
    ```
4. Use **Active Directory Users and Computers** to ensure the CNO and VCO computer objects associated with all clustered names have been removed.

    Note

    Stop the Cluster service on all servers in the cluster and set the service startup type to Manual so that the Cluster service doesn't start when the servers are restarting while changing domains.

    ```powershell
    Stop-Service -Name ClusSvc
    
    Set-Service -Name ClusSvc -StartupType Manual
    ```
5. Change the servers' domain membership to a workgroup, restart the servers, join the servers to the new domain, and restart again.
6. Once the servers are in the new domain, sign in to a server with a domain user or administrator account that has Active Directory permissions to create objects, has access to the cluster, and open PowerShell. Start the Cluster Service, and set it back to Automatic.

    ```powershell
    Start-Service -Name ClusSvc
    
    Set-Service -Name ClusSvc -StartupType Automatic
    ```
7. Bring the Cluster Name and all other cluster Network Name resources to an online state.

    ```powershell
    Start-ClusterResource -Name "Cluster Name"
    
    Start-ClusterResource -Name FS-CLUSCLUS
    ```

    Note

    If the subsequent [New-ClusterNameAccount](/en-us/powershell/module/failoverclusters/new-clusternameaccount) fails, bring the Cluster Name and all other cluster Network Name resources to an offline state before retrying.
8. Change the cluster to be a part of the new domain with associated active directory objects. The following command recreates the name objects in Active Directory and the network name resources must be in an online state:

    ```powershell
    New-ClusterNameAccount -Name ClusterName -Domain NewDomainName.com -UpgradeVCOs
    ```

    Note

    - If you don't have any additional groups with network names, such as a Hyper-V Cluster with only virtual machines, the `-UpgradeVCOs` parameter isn't needed.
    - If the VCO is not created when running [New-ClusterNameAccount](/en-us/powershell/module/failoverclusters/new-clusternameaccount), please use the *Repair* function on the Cluster Network Name resources from the Failover Cluster Manager.
9. Use **Active Directory Users and Computers** to check the new domain and ensure the associated computer objects were created. If they have, then bring the remaining resources in the groups online.

    ```powershell
    Start-ClusterGroup -Name "Cluster Group"
    
    Start-ClusterGroup -Name FS-CLUSCLUS
    ```

## Known issues

If you're using the new USB witness feature, you'll be unable to add the cluster to the new domain due to the file share witness type that must utilize Kerberos for authentication. Change the witness to **none** before adding the cluster to the domain. Once this step is complete, recreate the USB witness. The error you'll see is:

```
New-ClusternameAccount : Cluster name account cannot be created. This cluster contains a file share witness with invalid permissions for a cluster of type AdministrativeAccesssPoint ActiveDirectoryAndDns. To proceed, delete the file share witness. After this you can create the cluster name account and recreate the file share witness. The new file share witness will be automatically created with valid permissions.
```