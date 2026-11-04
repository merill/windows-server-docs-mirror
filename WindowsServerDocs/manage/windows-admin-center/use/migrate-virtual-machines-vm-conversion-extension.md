---
layout: Conceptual
title: Migrate virtual machines using the VM Conversion Extension in Windows Admin Center (Preview) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/use/migrate-virtual-machines-vm-conversion-extension
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Discover how to install and use the VM Conversion extension to seamlessly migrate VMware VMs to Hyper-V with Windows Admin Center.
author: pmiddha
ms.topic: how-to
ms.date: 2025-08-13T00:00:00.0000000Z
ms.author: pmiddha
ms.reviewer: shsathee,pmiddha
locale: en-us
document_id: 2fee6259-006a-e2a9-fd03-57d6f695da1b
document_version_independent_id: 2fee6259-006a-e2a9-fd03-57d6f695da1b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/use/migrate-virtual-machines-vm-conversion-extension.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/use/migrate-virtual-machines-vm-conversion-extension
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/use/migrate-virtual-machines-vm-conversion-extension.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 0439de11-5cf6-4f0f-3cd4-eaad30e9a50c
---

# Migrate virtual machines using the VM Conversion Extension in Windows Admin Center (Preview) | Microsoft Learn

Important

The VM Conversion extension is currently in PREVIEW. This document provides information about a prerelease product that might change substantially before its release. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

As a preview extension, the VM Conversion extension is governed by the [Windows Admin Center prerelease extension software license terms](/en-us/legal/windows-server/windows-admin-center/windows-pre-release-extension-eula). Microsoft isn't obligated under this agreement to provide any support services for the software. Issues, questions, and feedback not covered in this documentation can be filed [here](https://github.com/MicrosoftDocs/Windows-Admin-Center-Ideas-and-Feedback).

This article describes how to migrate VMware virtual machines to Hyper-V using the VM Conversion extension in Windows Admin Center. You learn how to install and configure the extension, synchronize virtual machines, and complete the migration.

For an overview of the VM Conversion extension, including key features and supported scenarios, see [Overview of VMware to Hyper-V migration](vm-conversion-extension-overview).

## Prerequisites

Before you begin, review the prerequisites and make sure your environment meets the requirements.

- VMware vCenter version, 6.x, 7.x, or 8.x with privileges access to the virtual machines you want to migrate.
- Ensure that the Hyper-V role is installed on the target Hyper-V host. You'll also need membership to the local Administrators group or the Hyper-V Administrators group to create and manage virtual machines on the Hyper-V host.
- Review the [guest operating systems](vm-conversion-extension-overview#vcenter-versions-and-guest-operating-systems) to ensure the VMs you're migrating are compatible.

On the Windows Admin Center Gateway machine, ensure you have the following:

- Administrator privileges, or equivalent, to install the extension and perform migrations.
- Windows Admin Center Gateway version `2410` build number `2.4.12.10` or later.
- The latest version of PowerCLI installed. To download and install PowerCLI, see the [PowerCLI Installation Guide](https://developer.broadcom.com/powercli/installation-guide).
- [VMware Virtual Disk Development Kit (VDDK) version 8.0.3](https://developer.broadcom.com/sdks/vmware-virtual-disk-development-kit-vddk/latest/) downloaded and extracted to the directory: `C:\Program Files\WindowsAdminCenter\Service\VDDK`. Ensure you download **VDDK version 8.0.3** specifically. Other versions aren't supported.
- [Visual Studio 2015 (VC++ 14.0) Redistributable](/en-us/cpp/windows/latest-supported-vc-redist#visual-studio-2015-vc-140-no-longer-supported) and [Visual C++ Redistributable Packages for Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40784) installed.

## Install the VM Conversion extension

Complete the following steps to install the **VM Conversion** extension:

1. Open Windows Admin Center.
2. Select the **Settings** button in the top-right. In the left pane, select **Extensions**.
3. The **Available Extensions** tab lists the extensions on the feed that you can install.
4. Search for **VM Conversion (Preview)** in **Available extensions** and select **Install**.

    [![Screenshot of the VM Conversion extension in the list of all Available extensions.](media/migrate-virtual-machines-vm-conversion-extension/vm-conversion-available-extensions.png)](media/migrate-virtual-machines-vm-conversion-extension/vm-conversion-available-extensions.png#lightbox)
5. After installation, make sure the **VM Conversion** extension appears in Windows Admin Center under: **Installed Extensions** &gt; **VM Conversion (Preview)**.

## Connect to vCenter

When you first visit the extension, you need to connect your vSphere client endpoint.

1. Go to the Windows Admin Center home page by selecting the **Windows Admin Center** logo in the top-left corner.
2. Either connect to an existing Hyper-V server or cluster, or add a new Hyper-V server or cluster in Windows Admin Center. Choose one of the following options:

    1. To connect to an existing Hyper-V server or cluster, select the server or cluster from the list on the Windows Admin Center home page.

    Or

    1. To add a new Hyper-V server or cluster, select **+ Add** and then select **Server** or **Cluster**. Follow the prompts to add and connect to your Hyper-V host.
3. In the left panel, under **Extensions**, select **VM Conversion (Preview)**.
4. Select **Connect to vCenter**.

    [![Screenshot of the connect to vCenter option.](media/migrate-virtual-machines-vm-conversion-extension/connect-to-v-center.png)](media/migrate-virtual-machines-vm-conversion-extension/connect-to-v-center.png#lightbox)
5. Enter the vCenter FQDN, vCenter username, and vCenter password.

    [![Screenshot showing how to configure VMware settings.](media/migrate-virtual-machines-vm-conversion-extension/configure-vmware-settings.png)](media/migrate-virtual-machines-vm-conversion-extension/configure-vmware-settings.png#lightbox)

## Synchronize virtual machines

Before you synchronize virtual machines, the extension automatically runs a set of prechecks and reports any problems. These prechecks verify that:

- No active snapshots exist on the virtual machine.
- VMware PowerCLI is installed on the Windows Admin Center Gateway machine.
- Microsoft Visual C++ Redistributable packages (versions 2013 and latest) are installed on the Windows Admin Center Gateway machine.
- VDDK package is present at: `C:\Program Files\WindowsAdminCenter\Service\VDDK` on the Windows Admin Center Gateway machine.
- Target disk path for synchronization is valid.
- Destination Hyper-V host has sufficient memory and disk space.
- Change Block Tracking (CBT) is supported on the VM.

To synchronize virtual machines, complete the following steps:

1. Connect to the Hyper-V server in Windows Admin Center that you want the VM to be migrated.
2. Go to the VM Conversion extension in the left panel under **Extensions** &gt; **VM Conversion (Preview)**.
3. In the virtual machine list, select up to 10 virtual machines to synchronize.

    [![Screenshot of the synchronize tab.](media/migrate-virtual-machines-vm-conversion-extension/bulk-vm-selection-for-synchronization.png)](media/migrate-virtual-machines-vm-conversion-extension/bulk-vm-selection-for-synchronization.png#lightbox)
4. In the Synchronize VM window, enter the **Path to store data**. Select **Synchronize**.

    [![Screenshot of the dialog to enter the path to store data and confirm the synchronization can start.](media/migrate-virtual-machines-vm-conversion-extension/synchronize-vm-path-selection.png)](media/migrate-virtual-machines-vm-conversion-extension/synchronize-vm-path-selection.png#lightbox)
5. You see notifications appear with the progress for: running prechecks, preparing the environment, creating a snapshot, and finalizing synchronization. Confirm that the Hyper-V Virtual Hard Disk (VHDX) file is created in the folder path you specified.

    [![Screenshot of the notifications that appear while the synchronization is in progress.](media/migrate-virtual-machines-vm-conversion-extension/synchronization-in-progress.png)](media/migrate-virtual-machines-vm-conversion-extension/synchronization-in-progress.png#lightbox)
6. Wait for the sync to complete.

## Migrate virtual machines

Before migration begins, the extension automatically runs a set of prechecks. These prechecks verify:

- The destination Hyper-V host has enough available vCPUs.
- No virtual machine with the same name exists on the destination Hyper-V host.
- The Hyper-V role is enabled on the target Hyper-V host.
- The synchronized `.vhdx` file exists at the specified destination storage path on the Hyper-V host.
- The virtual machine has no active snapshots.

To migrate virtual machines, complete the following steps:

1. Go to the **Migrate** tab, and select the VM to migrate. Select **Migrate**.

    [![Screenshot of the migrate tab and virtual machines selected to migrate.](media/migrate-virtual-machines-vm-conversion-extension/vm-selection-for-migration.png)](media/migrate-virtual-machines-vm-conversion-extension/vm-selection-for-migration.png#lightbox)
2. In the **Migrate VM** window, select **Proceed** to start the migration.

    [![Screenshot of the dialog confirming that the migration can start.](media/migrate-virtual-machines-vm-conversion-extension/confirm-migration.png)](media/migrate-virtual-machines-vm-conversion-extension/confirm-migration.png#lightbox)

    During the migration, the process performs the following steps: runs migration prechecks, ensures sufficient disk space, performs delta replication, powers off source VM, executes final delta sync, and imports VM into Hyper-V.
3. Wait for virtual machine migration to complete.

    [![Screenshot of the progress of virtual machine migration.](media/migrate-virtual-machines-vm-conversion-extension/migration-in-progress.png)](media/migrate-virtual-machines-vm-conversion-extension/migration-in-progress.png#lightbox)
4. You can manage the migrated virtual machine using the Hyper-V Manager or Windows Admin Center.

    Note

    Migration requires the user to stay signed in with an active browser session. If the session is closed or times out, the migration might pause or stop progressing.

## View logs

During synchronization and migration, view logs in the following locations to help troubleshoot any problems that arise:

- Browser console logs
- Event viewer logs
- VM conversion logs

### Browser console logs

Browser console logs are useful for identifying any failing API calls from Windows Admin Center. To view the browser console logs, follow these steps:

1. Open your browser settings, and go to **More Tools** &gt; **Developer Tools**.
2. Check the **Console** tab.
3. Look for any error or warning messages and share them as needed.

### Event viewer logs

Event Viewer logs capture server-side errors and warnings from the Windows Admin Center gateway, including authentication problems, service failures, and extension errors. To view the Event Viewer logs for Windows Admin Center, follow these steps:

1. On the Windows Admin Center server, open **Event Viewer**.
2. Expand **Applications and Services Logs** in the left pane.
3. Select **WindowsAdminCenter**.
4. Filter and review logs for **Errors**, **Warnings**, and **Informational** messages relevant to the VM Conversion extension.
5. Look for events with the source **WebREST** and Event ID **422** for VM conversion-related problems.

### VM conversion logs

VM conversion logs provide detailed information about the synchronization and migration process, including disk copy progress, error details, and operation timestamps. To view the VM conversion logs, follow these steps:

1. Connect to the Windows Admin Center server.
2. Find the file located at `C:\Program Files\WindowsAdminCenter\Service\VMConversion_log.txt`.