---
layout: Conceptual
title: Enable Hotpatch for Azure Edition virtual machines | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/enable-hotpatch-azure-edition
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: 'Learn how to enable Hotpatch for Windows Server Datacenter: Azure Edition when built using ISO installation media.'
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2024-11-15T00:00:00.0000000Z
locale: en-us
document_id: c8228819-98c5-dfc3-ecaf-a89ea4e4e093
document_version_independent_id: c8228819-98c5-dfc3-ecaf-a89ea4e4e093
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/enable-hotpatch-azure-edition.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/enable-hotpatch-azure-edition
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/enable-hotpatch-azure-edition.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/289b8734-3abd-4162-bc19-e661c3f4c940
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3dfe9005-13cb-4d91-be75-60fd92cba00d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a94795e-9024-410d-b38e-b67941440893
- https://authoring-docs-microsoft.poolparty.biz/devrel/de3e9d45-756e-43ff-93c2-451fc0181705
platformId: bd528530-6a86-b02d-1cc4-e1e5d283daa5
---

# Enable Hotpatch for Azure Edition virtual machines | Microsoft Learn

Hotpatch for Windows Server 2022 Datacenter: Azure Edition virtual machines (VMs) hosted on Azure Local allows you to install security updates on an ISO-deployed machine on Azure Local without requiring a reboot after installation. You can use Hotpatch with both Desktop Experience and Server Core. This article will teach you how to configure Hotpatch after installing or upgrading the operating system using an ISO.

Note

If you're using the Azure marketplace, don't follow the steps in this article. Instead, use the following images from Azure Marketplace that are ready for Hotpatching:

- Windows Server 2022 Datacenter: Azure Edition Hotpatch - Gen2
- Windows Server 2022 Datacenter: Azure Edition Core - Gen2

When using Hotpatch for your ISO deployed machine on Azure Local, there are a few important differences with the Hotpatch experience compared with using Hotpatch as part of Azure Automanage for Azure VMs.

The differences include:

- Hotpatch configuration isn't available via Azure Update Manager.
- Hotpatch can't be disabled.
- Automatic Patching orchestration isn't available.
- Orchestration must be performed manually (for example, using Windows Update via SConfig).

## Prerequisites

To enable Hotpatch, you must have the following prerequisites ready before you start:

- Windows Server 2022 Datacenter: Azure Edition hosted on a supported platform, such as Azure or Azure Local with Azure benefits enabled.
    - Azure Local must be version 21H2 or later.
- Review the [How hotpatch works](/en-us/azure/automanage/automanage-hotpatch#how-hotpatch-works) section of the Hotpatch for new virtual machines article.
- Outbound network access or an outbound port rule allowing HTTPS (TCP/443) traffic to the following endpoints:
    - `go.microsoft.com`
    - `software-static.download.prss.microsoft.com`

## Prepare your computer

Before you can enable Hotpatch for your VM, you must prepare your computer using the following steps:

1. Sign-in to your machine. If you're on Server core, from the SConfig menu, enter option **15**, then press Enter to open a PowerShell session. If you're on the desktop experience, remote desktop into your VM and launch PowerShell.
2. Enable virtualization-based security by running the following PowerShell command to configure the correct registry settings:

    ```powershell
    $registryPath = "HKLM:\SYSTEM\CurrentControlSet\Control\DeviceGuard"
    $parameters = $parameters = @{
        Path = $registryPath
        Name = "EnableVirtualizationBasedSecurity"
        Value = "0x1"
        Force = $True
        PropertyType = "DWORD" 
    }
    New-ItemProperty @parameters
    ```
3. Restart your computer.
4. Configure the Hotpatch table size in the registry by running the following PowerShell command:

    ```powershell
    $registryPath = "HKLM:\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management"
    $parameters = $parameters = @{
        Path = $registryPath
        Name = "HotPatchTableSize"
        Value = "0x1000"
        Force = $True
        PropertyType = "DWORD"
    }
    New-ItemProperty @parameters
    ```
5. Configure the Windows Update endpoint for Hotpatch in the registry by running the following PowerShell command:

    ```powershell
    $registryPath = "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Update\TargetingInfo\DynamicInstalled\Hotpatch.amd64"
    $nameParameters = $parameters = @{
        Path = $registryPath
        Name = "Name"
        Value = "Hotpatch Enrollment Package"
        Force = $True
    }
    $versionParameters = $parameters = @{
        Path = $registryPath
        Name = "Version"
        Value = "10.0.20348.1129"
        Force = $True
    }
    New-Item $registryPath -Force
    New-ItemProperty @nameParameters
    New-ItemProperty @versionParameters
    ```

Now you've prepared your computer, you can install the Hotpatch servicing package.

## Install Hotpatch servicing package

Note

The Hotpatch Prerequisite KB is currently not published in the Microsoft Update catalog.

To be able to receive Hotpatch updates, you'll need to download and install the Hotpatch servicing package. In your PowerShell session, complete the following steps:

1. Download the (KB5003508) Microsoft Update Standalone Package from the Microsoft Update Catalog and copy it to your computer using the following PowerShell command:

    ```powershell
    $parameters = @{
         Source = "https://go.microsoft.com/fwlink/?linkid=2211714"
         Destination = ".\KB5003508.msu"
    }
    Start-BitsTransfer @parameters
    ```
2. To install the Standalone Package, run the following command:

    ```powershell
    wusa.exe .\KB5003508.msu
    ```
3. Follow the prompts. Once it's completed, select Finish.
4. To verify the installation, run the following command:

    ```powershell
    Get-HotFix | Where-Object {$_.HotFixID -eq "KB5003508"}
    ```

Note

When using Server Core, updates are set to be manually installed by default. You can change this setting using the SConfig utility.