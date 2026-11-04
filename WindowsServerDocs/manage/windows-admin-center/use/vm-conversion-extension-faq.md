---
layout: FAQ
title: VM Conversion extension in Windows Admin Center Frequently Asked Questions (Preview) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/use/vm-conversion-extension-faq
summary: >
  <div class="IMPORTANT">

  <p>Important</p>

  <p>The VM Conversion extension is currently in PREVIEW.

  This document provides information about a prerelease product that might change substantially before its release. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.</p>

  <p>As a preview extension, the VM Conversion extension is governed by the <a href="/legal/windows-server/windows-admin-center/windows-pre-release-extension-eula">Windows Admin Center prerelease extension software license terms</a>.

  Microsoft isn't obligated under this agreement to provide any support services for the software. Issues, questions, and feedback not covered in this documentation can be filed <a href="https://github.com/MicrosoftDocs/Windows-Admin-Center-Ideas-and-Feedback">here</a>.</p>

  </div>

  <p>Here are answers to the most commonly asked questions about migrating VMware virtual machines to Hyper-V using the VM Conversion extension in Windows Admin Center.</p>
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
description: Get answers to frequently asked questions about migrating VMware virtual machines to Hyper-V with Windows Admin Center (Preview).
author: robinharwood
ms.author: roharwoo
ms.topic: faq
ms.date: 2026-02-05T00:00:00.0000000Z
ms.reviewer: shsathee,pmiddha
locale: en-us
document_id: d2dd507a-7dba-e685-6cf4-3d356ba2803b
document_version_independent_id: d2dd507a-7dba-e685-6cf4-3d356ba2803b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/use/vm-conversion-extension-faq.yml
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: faq
toc_rel: ../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/use/vm-conversion-extension-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/use/vm-conversion-extension-faq.yml
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 095c6cd6-cad8-d652-3b57-71bc1b162817
---

# VM Conversion extension in Windows Admin Center Frequently Asked Questions (Preview) | Microsoft Learn

Important

The VM Conversion extension is currently in PREVIEW. This document provides information about a prerelease product that might change substantially before its release. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

As a preview extension, the VM Conversion extension is governed by the [Windows Admin Center prerelease extension software license terms](/en-us/legal/windows-server/windows-admin-center/windows-pre-release-extension-eula). Microsoft isn't obligated under this agreement to provide any support services for the software. Issues, questions, and feedback not covered in this documentation can be filed [here](https://github.com/MicrosoftDocs/Windows-Admin-Center-Ideas-and-Feedback).

Here are answers to the most commonly asked questions about migrating VMware virtual machines to Hyper-V using the VM Conversion extension in Windows Admin Center.

## Does the tool support both Static and Dynamic Host Configuration Protocol (DHCP) IP addresses?

Yes, both DHCP and Static IP addresses are supported.

Static IP is supported using scripts. When a static IP is detected, the VM credentials are collected to run the script and capture the IP address details. This data persists on the target Hyper-V host after the cutover phase.

## How does the tool handle VM boot types?

The tool automatically detects the source VM's boot type. **BIOS boot** creates a Generation 1 VM on Hyper-V. **UEFI boot** creates a Generation 2 VM on Hyper-V.

## Why are migrated VM disks showing as Dynamic instead of Static (Fixed)?

The VM Conversion tool currently migrates disks as **dynamically expanding (thin provisioned)** VHDX files, which means only the used portion of the disk is copied—not the full allocated size.

During migration, a VM with a **provisioned size of 500 GB** but **actual usage of 250 GB** results in a 250 GB dynamic VHDX on the destination. While this approach is space-efficient, it might cause storage management issues later.

After migration, customers should convert the VHDX to a fixed size to reflect the full provisioned storage using the PowerShell command:

```powershell
Convert-VHD -Path "C:\VMs\MyDisk.vhdx" -DestinationPath "C:\VMs\MyDisk_Fixed.vhdx" -VHDType Fixed
```

## Is VMware to Azure Local migration supported?

No, the tool doesn't support migration to Azure Local. Use [Azure Migrate to migrate virtual machines to Azure Local](/en-us/azure/azure-local/migrate/migration-azure-migrate-vmware-overview).

## Does the tool support virtual machines running on a virtual storage area network (vSAN)?

No, the tool doesn't support virtual machines running on vSAN.

## Is this tool available in Windows Admin Center in the Azure portal?

No, the conversion tool is only available in Windows Admin Center on-premises.

## How is memory configured during virtual machine migration?

During migration, memory is configured as static, even if the source virtual machine is set to use dynamic memory. This design choice to ensure migration stability and compatibility between VMware and Hyper-V memory management.

To re-enable dynamic memory of change RAM parameters after migration:

1. Open **Windows Admin Center**.
2. Navigate to the **Virtual machines** extension.
3. Power off the migrated virtual machine.
4. Select **Settings**.
5. Update the required memory parameters: Startup memory, Enable dynamic memory, Minimum memory, Maximum memory, and Memory buffer.
6. Save changes and **power on** the virtual machine.

## What are the current limitations of this migration tool?

- The Resync option, which allows data synchronization between initial replication and delta replication, isn't currently supported.
- VMware Tools aren't automatically uninstalled post-migration—remove them manually if needed.
- Hyper-V drivers must be installed on Linux machines before starting migration. Download and install [Linux Integration Services v4.3](https://www.microsoft.com/download/details.aspx?id=55106) for Hyper-V and Azure.
- During virtual machine conversion, the BIOS GUID on the destination virtual machine doesn't match the source virtual machine unless it's manually updated. This behavior might affect virtual machine identity synchronization, or licensing checks that rely on consistent BIOS-level identifiers. BIOS-level identifiers must be updated in virtual machine identity synchronization, and migration.

Expand this section and use the script provided to update the BIOS GUID on the migrated Hyper-V virtual machine.

    To update the BIOS GUID for a Hyper-V virtual machine:

    1. Extract the following script into a file named `Update-VMBiosInfo.ps1`.
    2. Open PowerShell as Administrator.
    3. Run the script with the required parameters: `.\Update-VMBiosInfo.ps1 -VMName "VM Name" -BiosGuid "New BIOS GUID"`

    ```powershell
    <#
    .SYNOPSIS
    Updates the BIOS GUID of a specified Hyper-V virtual machine.
    
    .DESCRIPTION
    This script stops a specified Hyper-V virtual machine, updates its BIOS GUID using CIM (Common Information Model), and WMIv2 (root\virtualization\v2), and then restarts the VM. It handles both synchronous and asynchronous operations triggered by the Hyper-V Management Service.
    
    It's useful in scenarios such as VM identity synchronization, VM migration, or reconfiguration where BIOS-level identifiers are required to be updated.
    
    .PARAMETER VMName
    The name of the Hyper-V virtual machine whose BIOS GUID is to be updated.
    
    .PARAMETER BiosGuid
    The new BIOS GUID to assign to the virtual machine. The script automatically formats the GUID with braces if not provided.
    
    .EXAMPLE
    .\Update-VMBiosInfo.ps1 -VMName "Contoso" -BiosGuid "{423A2700-F96D-561B-B421-C3088111A97B}"
    
    This command updates the BIOS GUID of the virtual machine named "Contoso" to the specified GUID.
    
    .NOTES
    Author: MICROSOFT Corporation
    Version: 1.0
    Date: 2025-08-07
    Requirements:
    - Run with administrator privileges
    - Requires Hyper-V and access to the root\virtualization\v2 namespace
    - Tested on Windows Server 2019/2022 and Windows 10/11 with Hyper-V enabled
    
    .RETURNS
    Outputs success messages and job details. Throws descriptive errors if there is a failure.
    
    .LINK
    https://learn.microsoft.com/windows-server/virtualization/hyper-v/
    
    #>
    
    param (
        [Parameter(Mandatory = $true)]
        [string]$VMName,
    
        [Parameter(Mandatory = $true)]
        [string]$BiosGuid
    )
    
    # Helper function to serialize
    function ConvertTo-CimEmbeddedString {
        [CmdletBinding()]
        param(
            [Parameter(ValueFromPipeline)]
            [Microsoft.Management.Infrastructure.CimInstance]$CimInstance
        )
    
        if ($null -eq $CimInstance) {
            return ""
        }
    
        $cimSerializer = [Microsoft.Management.Infrastructure.Serialization.CimSerializer]::Create()
        $serializedObj = $cimSerializer.Serialize($CimInstance, [Microsoft.Management.Infrastructure.Serialization.InstanceSerializationOptions]::None)
    
        return [System.Text.Encoding]::Unicode.GetString($serializedObj)
    }
    
    # Stop VM
    Write-Output "Stopping VM '$VMName'..."
    Stop-VM -Name $VMName -Force
    
    # Retrieve the VMs system settings data using its name
    $vmSettingsData = Get-CimInstance -Namespace "root\virtualization\v2" -Query "select * from Msvm_VirtualSystemSettingData where ElementName = '$VMName'" -ErrorAction Stop
    
    # Ensure BIOS GUID has { } format
    if (-not ($BiosGuid.StartsWith("{") -and $BiosGuid.EndsWith("}"))) {
        $BiosGuid = "{$BiosGuid}"
    }
    # Set the BIOS GUID
    $vmSettingsData.BIOSGUID = $BiosGuid
    
    # Get the Virtual System Management Service object
    $vmms = Get-CimInstance -Namespace root\virtualization\v2 -Class Msvm_VirtualSystemManagementService -ErrorAction Stop
    
    # Apply the updated system settings using ModifySystemSettings
    $result = $vmms | Invoke-CimMethod -Name "ModifySystemSettings" -Arguments @{
        "SystemSettings" = ($vmSettingsData | ConvertTo-CimEmbeddedString)
    } -ErrorAction Stop
    
    # Check the return value to determine if the operation succeeded
    if ($result.ReturnValue -eq 0) {
        # Success: operation completed synchronously
        Write-Host "BIOS GUID successfully updated for VM: $VMName (synchronous)"
    }
    elseif ($result.ReturnValue -eq 4096) {
    
        # 4096 indicates the method started an asynchronous job
        $jobPath = $result.Job
        Write-Host "BIOS GUID update started asynchronously for VM: $VMName (job path: $jobPath)"
        # Get the job object using its path
        $job = Microsoft.PowerShell.Management\Get-CimInstance -CimInstance $jobPath
    
        # Poll the job state until it's no longer Running (4) or Starting (3)
        while ($job.JobState -eq 3 -or $job.JobState -eq 4) {
            Start-Sleep -Seconds 1
            $job = Microsoft.PowerShell.Management\Get-CimInstance -CimInstance $jobPath
        }
    
        # If job completes successfully
        if ($job.JobState -eq 7) {
            Write-Host "BIOS GUID updated successfully for VM: $VMName (asynchronous job completed)"
        }
        else {
            # Job failed or didn't complete properly
            throw "Async job failed. JobState: $($job.JobState), ErrorDescription: $($job.ErrorDescription)"
        }
    }
    else {
        # Any other return value indicates a failure
        throw "ModifySystemSettings failed with ReturnValue: $($result.ReturnValue)"
    }
    
    Write-Output "BIOS GUID successfully updated for VM: $VMName"
    # Start the VM again
    Write-Output "Starting VM '$VMName'..."
    Start-VM -Name $VMName
    ```

    Note

    This process updates only the BIOS GUID. The BIOS Serial Number isn't updated because VMware and Hyper-V use different formats:

    - VMware BIOS Serial Number: UUID format (8-4-4-4-12) → 503a4411-be04-bd40-98ac-ffa42335cc22
    - Hyper-V BIOS Serial Number: Custom format (4-4-4-4-4-4-2) → 3123-9812-5797-4305-8770-5953-62

    If licensing in your environment depends on a combination of BIOS GUID and BIOS Serial Number, the source, and destination values won't match, even if the BIOS GUID is manually updated.