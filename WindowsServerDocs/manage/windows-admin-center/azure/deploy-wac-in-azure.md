---
layout: Conceptual
title: Deploy a Windows Admin Center gateway in Azure | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/azure/deploy-wac-in-azure
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: How to deploy a Windows Admin Center gateway in Azure
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.date: 2021-02-18T00:00:00.0000000Z
locale: en-us
document_id: e98e7f06-59d2-01bf-4fbb-779204194f8e
document_version_independent_id: 5b2c311e-69ee-7e2f-5ca3-696c9f9369f5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/azure/deploy-wac-in-azure.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/azure/deploy-wac-in-azure
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/azure/deploy-wac-in-azure.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: d0412bdd-b547-f337-f836-ed0e19499559
---

# Deploy a Windows Admin Center gateway in Azure | Microsoft Learn

This article describes how to manually deploy Windows Admin Center in an Azure VM for use in managing multiple Azure VMs. To manage a single VM, instead use the Windows Admin Center functionality built into the Azure portal, as described in [Use Windows Admin Center in the Azure portal](manage-vm)).

## Deploy using script

You can download [Deploy-WACAzVM.ps1](https://aka.ms/deploy-wacazvm) which you will run from [Azure Cloud Shell](https://shell.azure.com) to set up a Windows Admin Center gateway in Azure. This script can create the entire environment, including the resource group.

Jump to manual deployment steps

### Prerequisites

- Set up your account in [Azure Cloud Shell](https://shell.azure.com). If this is your first time using Cloud Shell, you will be asked you to associate or create an Azure storage account with Cloud Shell.
- In a **PowerShell** Cloud Shell, navigate to your home directory: `PS Azure:\> cd ~`
- To upload the `Deploy-WACAzVM.ps1` file, drag and drop it from your local machine to anywhere on the Cloud Shell window.

If specifying your own certificate:

- Upload the certificate to [Azure Key Vault](/en-us/azure/key-vault/key-vault-whatis). First, create a key vault in Azure portal, then upload the certificate into the key vault. Alternatively, you can use Azure portal to generate a certificate for you.

### Script parameters

- **ResourceGroupName** - [String] Specifies the name of the resource group where the VM will be created.
- **Name** - [String] Specifies the name of the VM.
- **Credential** - [PSCredential] Specifies the credentials for the VM.
- **MsiPath** - [String] Specifies the local path of the Windows Admin Center MSI when deploying Windows Admin Center on an existing VM. Defaults to the version from https://aka.ms/WACDownload if omitted.
- **VaultName** - [String] Specifies the name of the key vault that contains the certificate.
- **CertName** - [String] Specifies the name of the certificate to be used for MSI installation.
- **GenerateSslCert** - [Switch] True if the MSI should generate a self signed ssl certificate.
- **PortNumber** - [int] Specifies the ssl port number for the Windows Admin Center service. Defaults to 443 if omitted.
- **OpenPorts** - [int[]] Specifies the open ports for the VM.
- **Location** - [String] Specifies the location of the VM.
- **Size** - [String] Specifies the size of the VM. Defaults to "Standard\_DS1\_v2" if omitted.
- **Image** - [String] Specifies the image of the VM. Defaults to "Win2016Datacenter" if omitted.
- **VirtualNetworkName** - [String] Specifies the name of the virtual network for the VM.
- **SubnetName** - [String] Specifies the name of the subnet for the VM.
- **SecurityGroupName** - [String] Specifies the name of the security group for the VM.
- **PublicIpAddressName** - [String] Specifies the name of the public IP address for the VM.
- **InstallWACOnly** - [Switch] Set to True if WAC should be installed on a pre-existing Azure VM.

There are 2 different options for the MSI to deploy and the certificate used for MSI installation. The MSI can either be downloaded from aka.ms/WACDownload or, if deploying to an existing VM, the filepath of an MSI locally on the VM can be given. The certificate can be found in either Azure Key Vault or a self-signed certificate will be generated by the MSI.

### Script Examples

First, define common variables needed for the parameters of the script.

```PowerShell
$ResourceGroupName = "wac-rg1"
$VirtualNetworkName = "wac-vnet"
$SecurityGroupName = "wac-nsg"
$SubnetName = "wac-subnet"
$VaultName = "wac-key-vault"
$CertName = "wac-cert"
$Location = "westus"
$PublicIpAddressName = "wac-public-ip"
$Size = "Standard_D4s_v3"
$Image = "Win2016Datacenter"
$Credential = Get-Credential
```

#### Example 1: Use the script to deploy WAC gateway on a new VM in a new virtual network and resource group. Use the MSI from aka.ms/WACDownload and a self-signed cert from the MSI.

```PowerShell
$scriptParams = @{
    ResourceGroupName = $ResourceGroupName
    Name = "wac-vm1"
    Credential = $Credential
    VirtualNetworkName = $VirtualNetworkName
    SubnetName = $SubnetName
    GenerateSslCert = $true
}
./Deploy-WACAzVM.ps1 @scriptParams
```

#### Example 2: Same as #1, but using a certificate from Azure Key Vault.

```PowerShell
$scriptParams = @{
    ResourceGroupName = $ResourceGroupName
    Name = "wac-vm2"
    Credential = $Credential
    VirtualNetworkName = $VirtualNetworkName
    SubnetName = $SubnetName
    VaultName = $VaultName
    CertName = $CertName
}
./Deploy-WACAzVM.ps1 @scriptParams
```

#### Example 3: Using a local MSI on an existing VM to deploy WAC.

```PowerShell
$MsiPath = "C:\Users\<username>\Downloads\WindowsAdminCenter<version>.msi"
$scriptParams = @{
    ResourceGroupName = $ResourceGroupName
    Name = "wac-vm3"
    Credential = $Credential
    MsiPath = $MsiPath
    InstallWACOnly = $true
    GenerateSslCert = $true
}
./Deploy-WACAzVM.ps1 @scriptParams
```

### Requirements for VM running the Windows Admin Center gateway

Port 443 (HTTPS) must be open. Using the same variables defined for script, you can use the code below in Azure Cloud Shell to update the network security group:

```powershell
$nsg = Get-AzNetworkSecurityGroup -Name $SecurityGroupName -ResourceGroupName $ResourceGroupName
$newNSG = Add-AzNetworkSecurityRuleConfig -NetworkSecurityGroup $nsg -Name ssl-rule -Description "Allow SSL" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 443
Set-AzNetworkSecurityGroup -NetworkSecurityGroup $newNSG
```

### Requirements for managed Azure VM's

Port 5985 (WinRM over HTTP) must be open and have an active listener. You can use the code below in Azure Cloud Shell to update the managed nodes. `$ResourceGroupName` and `$Name` use the same variables as the deployment script, but you will need to use the `$Credential` specific to the VM you are managing.

```powershell
Enable-AzVMPSRemoting -ResourceGroupName $ResourceGroupName -Name $Name
Invoke-AzVMCommand -ResourceGroupName $ResourceGroupName -Name $Name -ScriptBlock {Set-NetFirewallRule -Name WINRM-HTTP-In-TCP-PUBLIC -RemoteAddress Any} -Credential $Credential
Invoke-AzVMCommand -ResourceGroupName $ResourceGroupName -Name $Name -ScriptBlock {winrm create winrm/config/Listener?Address=*+Transport=HTTP} -Credential $Credential
```

## Deploy manually on an existing Azure virtual machine

Before installing Windows Admin Center on your desired gateway VM, install a SSL certificate to use for HTTPS communication, or you can choose to use a self-signed certificate generated by Windows Admin Center. However, you will get a warning when trying to connect from a browser if you choose the latter option. You can bypass this warning in Edge by clicking **Details &gt; Go on to the webpage** or, in Chrome, by selecting **Advanced &gt; Proceed to [webpage]**. We recommend you only use self-signed certificates for test environments.

Note

These instructions are for installing on Windows Server with Desktop Experience, not on a Server Core installation.

1. [Download Windows Admin Center](../overview) to your local computer.
2. Establish a remote desktop connection to the VM, then copy the MSI from your local machine and paste into the VM.
3. Double-click the MSI to begin installation, and follow the instructions in the wizard. Be aware of the following:

    - By default, the installer uses the recommended port 443 (HTTPS). If you want to select a different port, note that you need to open that port in your firewall as well.
    - If you have already installed an SSL certificate on the VM, ensure you select that option and enter the thumbprint.
4. Start the Windows Admin Center service (run C:/Program Files/Windows Admin Center/sme.exe)

[Learn more about deploying Windows Admin Center.](../deploy/install)

### Configure the gateway VM to enable HTTPS port access:

1. Navigate to your VM in the Azure portal and select **Networking**.
2. Select **Add inbound port rule** and select **HTTPS** under **Service**.

Note

If you chose a port other than the default 443, choose **Custom** under Service and enter the port you chose in step 3 under **Port ranges**.

### Accessing a Windows Admin Center gateway installed on an Azure VM

At this point, you should be able to access Windows Admin Center from a modern browser (Edge or Chrome) on your local computer by navigating to the DNS name of your gateway VM.

Note

If you selected a port other than 443, you can access Windows Admin Center by navigating to https://&lt;DNS name of your VM&gt;:&lt;custom port&gt;

When you attempt to access Windows Admin Center, the browser will prompt for credentials to access the virtual machine on which Windows Admin Center is installed. Here you will need to enter credentials that are in the Local users or Local administrators group of the virtual machine.

In order to add other VMs in the VNet, ensure WinRM is running on the target VMs by running the following in PowerShell or the command prompt on the target VM: `winrm quickconfig`

If you haven't domain-joined the Azure VM, the VM behaves like a server in workgroup, so you'll need to make sure you account for [using Windows Admin Center in a workgroup](../support/troubleshooting#using-windows-admin-center-in-a-workgroup).