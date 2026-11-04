---
layout: Conceptual
title: Create Hyper-V VHD Set files | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/manage/create-vhdset-file
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Steps to create a VHDset file on Hyper-v 2016
author: robinharwood
ms.author: roharwoo
ms.date: 2017-01-26T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 5562d8e6-31f9-e752-6cb1-ce6fe8648f2e
document_version_independent_id: 9dd01d1b-5510-4134-6dac-c3ddfddf88a8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/manage/Create-VHDSet-file.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/manage/create-vhdset-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/manage/Create-VHDSet-file.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 9993f65a-ba20-5b57-83b4-eb521c7eed3d
---

# Create Hyper-V VHD Set files | Microsoft Learn

VHD Set files are a new shared Virtual Disk model for guest clusters in Windows Server 2016. VHD Set files support online resizing of shared virtual disks, support Hyper-V Replica, and can be included in application-consistent checkpoints.

VHD Set files use a new VHD file type, .VHDS. VHD Set files store checkpoint information about the group virtual disk used in guest clusters, in the form of metadata.

Hyper-V handles all aspects of managing the checkpoint chains and merging the shared VHD set. Management software can run disk operations like online resizing on VHD Set files in the same way it does for .VHDX files. This means that management software doesn't need to know about the VHD Set file format.

Note

It's important to evaluate the impact of VHD Set files before deployment into production. Make sure that there is no performance or functional degradation in your environment, such as disk latency.

## Create a VHD Set file from Hyper-V Manager

1. Open Hyper-V Manager. Click **Start**, point to **Administrative Tools**, and then click **Hyper-V Manager**.
2. In the Action pane, click **New**, and then click **Hard Disk**.
3. On the **Choose Disk Format** page, select **VHD Set** as the format of the virtual hard disk.
4. Continue through the pages of the wizard to customize the virtual hard disk. You can click **Next** to move through each page of the wizard, or you can click the name of a page in the left pane to move directly to that page.
5. After you have finished configuring the virtual hard disk, click **Finish**.

## Create a VHD Set file from Windows PowerShell

Use the [New-VHD](/en-us/powershell/module/hyper-v/new-vhd) cmdlet, with the file type .VHDS in the file path. This example creates a VHD Set file named base.vhds that is 10 Gigabytes in size.

```PowerShell
PS c:\>New-VHD -Path c:\base.vhds -SizeBytes 10GB
```

## Migrate a shared VHDX file to a VHD Set file

Migrating an existing shared VHDX to a VHDS requires taking the VM offline. This is the recommended process using Windows PowerShell:

1. Remove the VHDX from the VM. For example, run:

    ```PowerShell
    PS c:\>Remove-VMHardDiskDrive existing.vhdx
    ```
2. Convert the VHDX to a VHDS. For example, run:

    ```PowerShell
    PS c:\>Convert-VHD existing.vhdx new.vhds
    ```
3. Add the VHDS to the VM. For example, run:

    ```PowerShell
    PS c:\>Add-VMHardDiskDrive new.vhds
    ```