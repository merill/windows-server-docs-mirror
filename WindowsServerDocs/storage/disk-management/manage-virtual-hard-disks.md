---
layout: Conceptual
title: Manage Virtual Hard Disks (VHD) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/disk-management/manage-virtual-hard-disks
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Manage virtual hard disks (VHDs) with the Disk Management utility in Windows, where you can view, create, attach, and detach a VHD.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-24T00:00:00.0000000Z
locale: en-us
document_id: 6e79e0e4-0f7a-79dc-270e-136c87fcea26
document_version_independent_id: 5d75b46e-b689-0761-5cfb-b1af0d0b31de
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/disk-management/manage-virtual-hard-disks.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/disk-management/manage-virtual-hard-disks
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/disk-management/manage-virtual-hard-disks.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1ae43d8e-9469-c39f-da81-cc65dff0fc54
---

# Manage Virtual Hard Disks (VHD) | Microsoft Learn

You can create, attach, and detach virtual hard disks (VHDs) with the Disk Management system utility in Windows. VHDs are disk image file formats that have similar functionalities to a physical hard drive. The VHD file type is `.vhd` or `.vhdx` (recommended). VHDs are designed primarily for use with Hyper-V virtual machines.

A VHD is created and initialized at the same time. In the Disk Management view, the VHD looks just like a physical disk. When the VHD is attached and available for use, the disk icon is colored blue. When the VHD is detached and unavailable, the disk icon is colored gray.

## Prerequisites

To complete the procedures in this article, the following prerequisite must be met:

- The user account must be a member of the **Backup Operators** or **Administrators** group.

## Create a VHD

To create a VHD, follow these steps:

1. From the Windows **Start** menu, search for and open Disk Management with Administrator permissions.
2. Expand the **Action** menu and select **Create VHD**.
3. In the **Create and Attach Virtual Hard Disk** dialog, specify the location on the physical computer where you want to store the VHD file:

    1. For the **Location** field, select **Browse**. Locate and select the folder to store the new VHD, and select **OK**.

        Note

        The location must be a fully qualified path that doesn't include the *\Windows* directory.
    2. For the **File name** field, enter a name for the new VHD.
    3. Expand the **Save as type** dropdown list and select **Virtual Disk files (\*.vhdx)**.
    4. Select **Save**.
4. For the **Virtual hard disk size** field, enter the file size for the new VHD.

    Note

    A VHD can be only a basic disk with a minimum size of 3 megabytes (MB). A large fixed-size VHD can take extra time to create.
5. For the **Virtual hard disk type** field, select **Dynamically expanding** or **Fixed size**.
6. Select **OK** to finish.

## Attach a VHD

To make a VHD available for use (either a disk you created or another existing VHD), follow these steps:

1. From the Windows **Start** menu, search for and open Disk Management with Administrator permissions.
2. Expand the **Action** menu and select **Attach VHD**.
3. In the **Attach Virtual Hard Disk** dialog, select **Browse**. Locate and select the `.vhdx` or `.vhd` file for the VHD, and select **OK**.
4. In the **Attach Virtual Hard Disk** dialog, select **OK** to finish.

## Detach a VHD

When you detach a VHD, you make the disk unavailable. You don't delete the VHD or any data stored on the disk.

Detach a VHD by following these steps:

1. From the Windows **Start** menu, search for and open Disk Management with Administrator permissions.
2. Locate the VHD that you want to attach in the list of disks.
3. Right-click the VHD, select **Detach VHD**, and then select **OK**.