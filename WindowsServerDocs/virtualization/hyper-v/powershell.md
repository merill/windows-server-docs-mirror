---
layout: Conceptual
title: Working with Hyper-V and Windows PowerShell | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/powershell
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Learn about working with Hyper-V and how to automate tasks using Windows PowerShell.
keywords: windows 10, windows 11, hyper-v
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-29T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: e78eb19e-db0e-29cc-3a7d-185282edf40b
document_version_independent_id: e78eb19e-db0e-29cc-3a7d-185282edf40b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/powershell.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/powershell
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/powershell.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 146d5aef-1dc7-3954-48eb-0730b1eabef5
---

# Working with Hyper-V and Windows PowerShell | Microsoft Learn

Now that you have walked through the basics of deploying Hyper-V, creating virtual machines and managing these virtual machines, let’s explore how you can automate many of these activities with PowerShell.

## Return a list of Hyper-V commands

1. Select the Windows start button, and then type **PowerShell**.
2. Run the following command to display a searchable list of PowerShell commands available with the Hyper-V PowerShell Module.

```powershell
Get-Command -Module hyper-v | Out-GridView
```

You get something like this:

![Screenshot of the Out Grid View showing the Command Type, Name, Version, and Source fields.](media/powershell/command-grid.png)

1. To learn more about a particular PowerShell command use `Get-Help`. For instance, running the following command returns information about the `Get-VM` Hyper-V command.

    ```powershell
    Get-Help Get-VM
    ```

    The output shows you how to structure the command, what the required and optional parameters are, and the aliases that you can use.

    ![Screenshot of the Administrator Windows Power Shell screen, showing the output of how to structure commands.](media/powershell/get-help.png)

## Return a list of virtual machines

Use the `Get-VM` command to return a list of virtual machines.

1. In PowerShell, run the following command:

    ```powershell
    Get-VM
    ```

    This displays something like this:

    ![Screenshot of the Administrator Windows Power Shell screen showing the output after entering Get V M.](media/powershell/get-vm.png)
2. To return a list of only powered on virtual machines add a filter to the `Get-VM` command. A filter can be added by using the `Where-Object` command. For more information on filtering, see [Using the Where-Object](/en-us/powershell/module/microsoft.powershell.core/where-object) documentation.

    ```powershell
    Get-VM | where {$_.State -eq 'Running'}
    ```
3. To list all virtual machines in a powered off state, run the following command. This command is a copy of the command from step 2 with the filter changed from 'Running' to 'Off'.

    ```powershell
    Get-VM | where {$_.State -eq 'Off'}
    ```

## Start and shut down virtual machines

1. To start a particular virtual machine, run the following command with name of the virtual machine:

    ```powershell
    Start-VM -Name <virtual machine name>
    ```
2. To start all currently powered off virtual machines, get a list of those machines and pipe the list to the `Start-VM` command:

    ```powershell
    Get-VM | where {$_.State -eq 'Off'} | Start-VM
    ```
3. To shut down all running virtual machines, run the following command:

```powershell
Get-VM | where {$_.State -eq 'Running'} | Stop-VM
```

## Create a virtual machine checkpoint

To create a checkpoint using PowerShell, select the virtual machine using the `Get-VM` command and pipe this to the `Checkpoint-VM` command. Finally give the checkpoint a name using `-SnapshotName`. The complete command looks like the following:

```powershell
Get-VM -Name <VM Name> | Checkpoint-VM -SnapshotName <name for snapshot>
```

## Create a new virtual machine

The following example shows how to create a new virtual machine in the PowerShell Integrated Scripting Environment (ISE). This is a simple example and could be expanded on to include additional PowerShell features and more advanced VM deployments.

1. To open the PowerShell ISE click on start, type **PowerShell ISE**.
2. Run the following code to create a virtual machine. See the [New-VM](/en-us/powershell/module/hyper-v/new-vm) documentation for detailed information on the `New-VM` command.

    ```powershell
     $VMName = "VMNAME"
    
     $VM = @{
         Name = $VMName
         MemoryStartupBytes = 2147483648
         Generation = 2
         NewVHDPath = "C:\Virtual Machines\$VMName\$VMName.vhdx"
         NewVHDSizeBytes = 53687091200
         BootDevice = "VHD"
         Path = "C:\Virtual Machines\$VMName"
         SwitchName = (Get-VMSwitch).Name
     }
    
     New-VM @VM
    ```

## Wrap up and References

This document has shown some simple steps to explore the Hyper-V PowerShell module as well as some sample scenarios. For more information on the Hyper-V PowerShell module, see the [Hyper-V Cmdlets in Windows PowerShell reference](/en-us/powershell/module/hyper-v/index).