---
layout: Conceptual
title: Create a virtual machine in Hyper-V | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/get-started/create-a-virtual-machine-in-hyper-v
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Learn how to create a virtual machine in Hyper-V using Hyper-V Manager or PowerShell. Follow step-by-step instructions to get started quickly.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-11-27T00:00:00.0000000Z
locale: en-us
document_id: 67b14ead-0e41-e6bf-0584-9f49a891963b
document_version_independent_id: 0b362756-b903-fc48-238d-f235130b610b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/get-started/Create-a-virtual-machine-in-Hyper-V.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/get-started/create-a-virtual-machine-in-hyper-v
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/get-started/Create-a-virtual-machine-in-Hyper-V.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 3fb7b29c-a383-f300-8db9-dc6f0ce6b4b9
---

# Create a virtual machine in Hyper-V | Microsoft Learn

Learn how to create a virtual machine by using Hyper-V Manager and Windows PowerShell and what options you have when you create a virtual machine in Hyper-V Manager.

## Prerequisites

Before you create a virtual machine, make sure you have the following prerequisites:

- A computer running Windows Server or Windows client with Hyper-V enabled. For more information, see [Install the Hyper-V role on Windows Server](install-the-hyper-v-role-on-windows-server).
- Membership in the local **Administrators** group or the **Hyper-V Administrators** group.
- Sufficient physical memory on the host to allocate to the virtual machine.
- Sufficient disk space for virtual machine configuration files and virtual hard disks.
- (Optional) A virtual switch configured if you want network connectivity for the virtual machine. See [Create a virtual switch for Hyper-V virtual machines](create-a-virtual-switch-for-hyper-v-virtual-machines).
- (Optional) An operating system installation media (.iso file) or an existing virtual hard disk (.vhd or .vhdx) if you want to install an operating system.

## Create a virtual machine

To create a virtual machine, use either Hyper-V Manager or Windows PowerShell. Select the method you prefer:

# [Hyper-V Manager](#tab/hyper-v-manager)
To create a virtual machine in Hyper-V Manager, follow these steps:

1. Select the **Start** button, type **Hyper-V Manager**, and then select it from the list.

    Note

    If you don't see Hyper-V Manager, make sure that the Hyper-V role is installed. For more information, see [Install the Hyper-V role on Windows Server](install-the-hyper-v-role-on-windows-server).
2. In the left pane, under **Hyper-V Manager**, select your server.
3. From the **Actions** pane, select **New**, then select **Virtual Machine**.
4. From the **New Virtual Machine Wizard**, select **Next**.
5. For the **Specify Name and Location** page, enter a name for the virtual machine and choose a location to store the virtual machine configuration files. Select **Next**.

    (Optionally) If you want to store the virtual machine configuration files in a different location, select the **Store the virtual machine in a different location** check box and then browse to the folder where you want to store the files.
6. In the **Specify Generation** page, select the generation of the virtual machine. For more information, see [Should I create a generation 1 or 2 virtual machine in Hyper-V?](../plan/should-i-create-a-generation-1-or-2-virtual-machine-in-hyper-v). Create a generation 2 virtual machine unless you have a specific reason to create a generation 1 virtual machine. Select **Next**.
7. For the **Assign Memory** page, enter the amount of memory to allocate to the virtual machine at startup. You can also choose to enable Dynamic Memory. For more information, see [Hyper-V Dynamic Memory Overview](../dynamic-memory). Select **Next**.

    Note

    The minimum amount of memory you can assign is 32 MB and the maximum is 5,902 MB.
8. For the **Configure Networking** page, select a virtual switch to connect the virtual machine to the network. If you don't have a virtual switch created, you can skip this step and configure networking later. Select **Next**.
9. In the **Connect Virtual Hard Disk** page, choose one of the following options, then select **Next**:

    - **Create a virtual hard disk** - Enter a name for the virtual hard disk, choose a location to store it, and specify its size.
    - **Use an existing virtual hard disk** - Browse to the location of an existing virtual hard disk (`.vhd` or `.vhdx`).
    - **Attach a virtual hard disk later** - You can attach a virtual hard disk later.
10. For the **Installation Options** page, choose how you want to install the operating system on the virtual machine. You can choose one of the following options, then select **Next**:

    - **Install an operating system later**
    - **Install an operating system from a bootable image file** - Browse to the location of an `.iso` file that contains the operating system installation media.
    - **Install an operating system from a bootable floppy disk** - Select a floppy disk drive that contains the operating system installation media.
    - **Install an operating system from a network-based installation server** - This option is for using Windows Deployment Services (WDS) or another network-based installation service.
11. After verifying your choices in the **Summary** page, select **Finish**.

# [PowerShell](#tab/powershell)
To create a virtual machine with Windows PowerShell using [New-VM](/en-us/powershell/module/hyper-v/new-vm), follow these steps:

1. On the Windows desktop, select the Start button and type **Windows PowerShell**.
2. Right-click on **Windows PowerShell** and select **Run as administrator**.
3. Use the [Get-VMSwitch](/en-us/powershell/module/hyper-v/get-vmswitch) cmdlet to get the name of the virtual switch that you want the virtual machine to use:

    ```powershell
    Get-VMSwitch * | Format-Table Name
    ```
4. Use the [New-VM](/en-us/powershell/module/hyper-v/new-vm) cmdlet to create the virtual machine. See the following examples:

    Note

    Use the **-Version** parameter if you need to move this virtual machine to a host running an older Windows Server version. See [Supported virtual machine configuration versions](../deploy/upgrade-virtual-machine-version-in-hyper-v-on-windows-or-windows-server#supported-virtual-machine-configuration-versions).

    - **Existing virtual hard disk** - To create a virtual machine with an existing virtual hard disk, use the following command where,

        - **-Name** is the name that you provide for the virtual machine that you're creating.
        - **-MemoryStartupBytes** is the amount of memory that's available to the virtual machine at startup.
        - **-BootDevice** is the device that the virtual machine boots to when it starts, like the network adapter (NetworkAdapter) or virtual hard disk (VHD).
        - **-VHDPath** is the path to the virtual machine disk that you want to use.
        - **-Path** is the path to store the virtual machine configuration files.
        - **-Generation** is the virtual machine generation. Use generation 1 for VHD and generation 2 for VHDX. See [Should I create a generation 1 or 2 virtual machine in Hyper-V?.](../plan/should-i-create-a-generation-1-or-2-virtual-machine-in-hyper-v)
        - **-Switch** is the name of the virtual switch that you want the virtual machine to use to connect to other virtual machines or the network. See [Create a virtual switch for Hyper-V virtual machines](create-a-virtual-switch-for-hyper-v-virtual-machines).

            ```powershell
            New-VM -Name <Name> -MemoryStartupBytes <Memory> -BootDevice <BootDevice> -VHDPath <VHDPath> -Path <Path> -Generation <Generation> -Switch <SwitchName>
            ```

            For example:

            ```powershell
            New-VM -Name TestVM -MemoryStartupBytes 4GB -BootDevice VHD -VHDPath .\VMs\Test.vhdx -Path .\VMData -Generation 2 -Switch ExternalSwitch
            ```

            This example creates a generation 2 virtual machine named TestVM with 4 GB of memory. It boots from the folder VMs\Test.vhdx in the current directory and uses the virtual switch named ExternalSwitch. The virtual machine configuration files are stored in the folder VMData.
    - **New virtual hard disk** - To create a virtual machine with a new virtual hard disk, replace the **-VHDPath** parameter from the previous example with **-NewVHDPath** and add the **-NewVHDSizeBytes** parameter. For example,

        ```powershell
        New-VM -Name TestVM -MemoryStartupBytes 4GB -BootDevice VHD -NewVHDPath .\VMs\Test.vhdx -Path .\VMData -NewVHDSizeBytes 20GB -Generation 2 -Switch ExternalSwitch
        ```
    - **New virtual hard disk that boots to operating system image** - To create a virtual machine with a new virtual disk that boots to an operating system image, see the PowerShell example in [Create virtual machine walkthrough for Hyper-V on Windows](/en-us/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).

---

## Start and connect to the virtual machine

After you create the virtual machine, you can start it and connect to it. You can use either Hyper-V Manager or Windows PowerShell. Select the method you prefer:

# [Hyper-V Manager](#tab/hyper-v-manager)
To start and connect to the virtual machine in Hyper-V Manager, follow these steps:

1. In Hyper-V Manager, right-click the virtual machine and select **Connect...**.
2. In the Virtual Machine Connection window, select **Action** &gt; **Start**.

# [PowerShell](#tab/powershell)
To start and connect to the virtual machine using Windows PowerShell, follow these steps:

1. Start the virtual machine by using the [Start-VM](/en-us/powershell/module/hyper-v/start-vm) cmdlet. Run the following cmdlet where Name is the name of the virtual machine you created:

    ```powershell
    Start-VM -Name <Name>
    ```

    For example:

    ```powershell
    Start-VM -Name TestVM
    ```
2. Connect to the virtual machine by using Virtual Machine Connection (VMConnect):

    ```powershell
    VMConnect.exe <ServerName> <VMName>
    ```

    For example:

    ```powershell
    VMConnect.exe localhost "TestVM"
    ```

---