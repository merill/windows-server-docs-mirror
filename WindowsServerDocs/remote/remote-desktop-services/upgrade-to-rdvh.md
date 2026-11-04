---
layout: Conceptual
title: Upgrading your Remote Desktop Virtualization Host | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/upgrade-to-rdvh
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to upgrade your existing Remote Desktop Virtualization Host.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: upgrade-and-migration-article
author: robinharwood
locale: en-us
document_id: b5406d58-7dcd-08f0-5ffe-d4c720cacf49
document_version_independent_id: ee9d4632-7041-8155-612d-40ac0e635c85
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/upgrade-to-rdvh.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/upgrade-to-rdvh
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/upgrade-to-rdvh.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 037aa1ad-f15c-960c-dedc-f48b211f6f3b
---

# Upgrading your Remote Desktop Virtualization Host | Microsoft Learn

## RD Virtualization Host servers in the deployment where VMs are stored locally

These servers should be upgraded all at once. Complete the following steps to upgrade:

1. Log off all users.
2. Turn off or save all virtual machines on each host.
3. Upgrade the servers to the new Windows Server version.
4. All collections should be available and functional after the upgrades are complete.

## RD Virtualization Host servers in the deployment where VMs are stored in Cluster Shared Volumes (CSV)

1. Determine an upgrade strategy where some of the RDVH servers are upgraded and some continue to host VMs on the earlier version of Windows Server.
2. Isolate one or more of the RDVH servers targeted for the initial round of upgrading. By migrating all VMs to other 'not to be upgraded yet' RDVH servers that remain part of the original cluster.

    1. Open Failover Cluster Manager.
    2. Select **Roles**.
    3. Select one or more VMs. Right-click to open the context menu.
    4. Select **Move** and choose either **Live** or **Quick Migration** to move the VMs to one or more of the RD Virtualization Host Servers that aren't part of the initial upgrade. Use **Live** or **Quick** Migration depending on factors such as hardware compatibility or online requirements.
3. Evict the RDVH servers, prepared for upgrading, from the original cluster.
4. Upgrade the isolated RDVH servers.
5. After the targeted RDVH servers have been successfully upgraded, create a new cluster and CSV, which needs to be on an entirely different SAN volume.
6. Join all upgraded RDVH servers to the new cluster.
7. Create a folder structure in the new CSV that mimics the existing folder structure in the existing CSV. This includes the collection folders and each VM's top level subfolders.
8. From the various VM Collection folders on the original CSV, copy over the /IMGS folder and contents to the new collection folders in the same locations on the new CSV.
9. On the source RDVH machine, use Cluster Manager to remove the VM's configuration for high availability:

    1. Launch Cluster Manager.
    2. Select **Roles**.
    3. Right-click the VM objects, and then select **Remove**.
10. On one of the nonupgraded RDVH servers, use Hyper-V Manager to move all VMs to one of the upgraded RDVH servers and new Cluster CSV:

    1. Open Hyper-V Manager.
    2. Select one of the nonupgraded RDVH servers.
    3. Right-click one of the VMs to be moved, and then select **Move**.
    4. Choose **Move the virtual machine**, and then select **Next**.
    5. Provide the targeted upgraded RDVH server's name on the **Specify Destination Computer** page, and then select **Next**.
    6. Choose **Move the virtual machine's data to a single location**, and then select **Next**.
    7. Browse to the destination location.

        Important

        Ensure this path is to an empty folder for the specific VM.

        Note

        As mentioned, you need to have already created a new destination subfolder prior to this step. The Select Folder dialog won't allow you to create a subfolder in this step.

        Select **Next**, and then select **Finished**.
11. Once the VMs are relocated, add them as cluster **High Availability** objects:

    1. Open Failover Cluster Manager on an upgraded RD Virtualization Host Server.
    2. Right-click the **Roles** node, and then select **Configure Role**. Select **Next** on the **Start** page of the High Availability wizard.
    3. Choose **Virtual Machine** from the list of available roles, and then select **Next**. A list of VMs that aren't configured is shown.
    4. Select all the VMs. Select **Next** and then select **Next** again on the confirmation page to start the configuration task.
12. Once you have relocated all VMs, upgrade the remaining RDVH servers. Use the above steps for balancing VM locations as appropriate.

Note

Heterogeneous Hyper-V servers in a cluster aren't supported.