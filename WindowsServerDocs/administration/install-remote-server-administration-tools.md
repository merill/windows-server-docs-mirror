---
layout: Conceptual
title: Install and Manage Remote Server Administration Tools in Windows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/install-remote-server-administration-tools
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Learn about the available Remote Server Administration Tools (RSAT) and how to install, enable, and use RSAT on Windows Server and Windows 10 or 11 clients
ms.topic: install-set-up-deploy
ms.author: roharwoo
author: robinharwood
ms.date: 2025-08-22T00:00:00.0000000Z
zone_pivot_groups: windows-os-version-plus-client
ms.custom:
- ai-gen-docs-bap
- ai-gen-description
- ai-seo-date:08/20/2025
locale: en-us
document_id: fdcb12f6-884e-2537-795d-540421900ab1
document_version_independent_id: 4853adc9-67c5-abf0-6c6c-178e8a4e126d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/install-remote-server-administration-tools.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/install-remote-server-administration-tools
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/install-remote-server-administration-tools.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 09ba7900-1dcd-d5dd-80e5-37d5ffdef3a8
---

# Install and Manage Remote Server Administration Tools in Windows | Microsoft Learn

Remote Server Administration Tools (RSAT) for Windows Server are a collection of utilities that enable IT administrators to remotely manage roles and features on Windows Server systems from a Windows client computer. This article provides an overview of the Remote Server Administration Tools (RSAT) for Windows. The article also shows you how to install and use them to manage Windows Server roles and features from a Windows Server or Windows client computer.

The method to install the RSATs varies depending on your platform. Make sure to select your platform from the buttons at the start of the article.

## What are Remote Server Administration Tools?

RSAT includes several types of tools to help you manage servers remotely:

- **Server Manager** - A central console for server tasks
- **MMC snap-ins** - Focused tools for specific services
- **PowerShell modules** - Command-line scripts and automation
- **Command-line tools** - Direct server control from the command prompt

These tools streamline remote administration, making it easier to configure, monitor, and troubleshoot Windows Server environments from anywhere.

### Available tools

You can use the following RSATs from either a Windows Server or Windows client machine. The following table shows you which tools are available to each platform.

| RSAT Tool Name | Description | Windows Server | Windows client (Feature on Demand) | Windows client (DISM) |
| --- | --- | --- | --- | --- |
| **Feature Administration Tools** |  |  |  |  |
| BitLocker Drive Encryption Administration Utilities | Manage BitLocker Drive Encryption on remote servers. | ✅ | ✅ | ✅ |
| BITS Server Extensions Tools | Administer Background Intelligent Transfer Service extensions. | ✅ | ❌ | ❌ |
| DataCenterBridging LLDP Tools | Configure Data Center Bridging and LLDP settings. | ✅ | ✅ | ✅ |
| Failover Clustering Tools | Manage and configure failover clusters. | ✅ | ✅ | ✅ |
| IP Address Management (IPAM) Client | Administer IP address infrastructure using IPAM. | ✅ | ✅ | ✅ |
| Network Load Balancing Tools | Configure and manage network load balancing clusters. | ✅ | ✅ | ✅ |
| Shielded VM Tools | Manage Shielded Virtual Machines. | ✅ | ❌ | ❌ |
| SNMP Tools | Administer SNMP services and settings. | ✅ | ❌ | ❌ |
| Storage Migration Service Tools | Manage storage migration services. | ✅ | ✅ | ✅ |
| Storage Replica Module for Windows PowerShell | Configure and manage storage replication. | ✅ | ✅ | ✅ |
| System Insights Module for Windows PowerShell | Access predictive analytics for Windows Server. | ✅ | ✅ | ✅ |
| WINS Server Tools | Manage Windows Internet Name Service (WINS) servers. | ✅ | ❌ | ❌ |
| **Role Administration Tools** |  |  |  |  |
| AD DS and AD LDS Tools | Manage Active Directory Domain Services and Lightweight Directory Services. | ✅ | ✅ | ✅ |
| Hyper-V Management Tools | Manage Hyper-V hosts and virtual machines. | ✅ | ❌ | ✅ |
| Remote Desktop Services Tools | Manage Remote Desktop Session Host, Gateway, and other RDS roles. | ✅ | ✅ | ✅ |
| Windows Server Update Services Tools | Administer WSUS servers and manage updates for Windows systems. | ✅ | ✅ | ✅ |
| Active Directory Certificate Services Tools | Manage AD Certificate Services and related components. | ✅ | ✅ | ✅ |
| Active Directory Rights Management Services Tools | Administer AD Rights Management Services. | ✅ | ❌ | ❌ |
| DHCP Server Tools | Administer and configure DHCP servers and scopes. | ✅ | ✅ | ✅ |
| DNS Server Tools | Manage DNS servers, zones, and records. | ✅ | ✅ | ✅ |
| Fax Server Tools | Manage fax server roles and settings. | ✅ | ❌ | ❌ |
| File Services Tools | Administer shared folders, quotas, and file server resources. | ✅ | ✅^1^ | ✅^1^ |
| Network Controller Management Tools | Manage network controllers in Windows Server. | ✅ | ✅ | ✅ |
| Network Policy and Access Services Tools | Administer network policies and access services. | ✅ | ❌ | ❌ |
| Print and Document Services Tools | Administer print servers and printers. | ✅ | ❌ | ❌ |
| Remote Access Management Tools | Manage remote access roles and VPN services. | ✅ | ✅ | ✅ |
| Volume Activation Tools | Configure and manage volume activation services. | ✅ | ✅ | ✅ |
| Windows Deployment Services Tools | Manage Windows Deployment Services for network-based OS installations. | ✅ | ❌ | ❌ |
| Server Manager | Centralized management console for managing server roles and features. | ✅^2^ | ✅ | ✅ |

1. Tools for managing Services for NFS on local and remote computers can be added as a Windows Optional Feature using DISM.
2. Server Manager is included with Windows Server by default and not listed as a Remote Server Administration Tool.

To learn more about the available Features on Demand RSAT, see the [list of RSAT available via Features on Demand](/en-us/windows-hardware/manufacture/desktop/features-on-demand-non-language-fod#remote-server-administration-tools-rsat).

## Prerequisites

To use Remote Server Administration Tools, you need the following prerequisites:

- A computer running one of the following operating systems:

    - Windows 10 (October 2018 Cumulative Update or later) Pro or Enterprise editions only
    - Windows 11 Pro or Enterprise editions only
    - Any supported version of Windows Server
- Administrative privileges on the computer where RSAT is installed.
- Administrative privileges on the remote Windows Server systems for the service you want to manage.
- Network connectivity to the remote Windows Server systems you want to manage.

## Install Remote Server Administration Tools

::: zone pivot="windows-server-2025,windows-server-2022,windows-server-2019,windows-server-2016"

To install Remote Server Administration Tools on Windows Server, select your preferred method:

# [Server Manager](#tab/server-manager)
To install RSATs using Server Manager, follow these steps:

1. Sign in to the Windows Server computer with an account that has administrative privileges.
2. Open **Server Manager** from the Start menu or taskbar.
3. In Server Manager, select on **Manage** in the top right corner.
4. Select **Add Roles and Features** from the dropdown menu.
5. In the **Add Roles and Features Wizard**, select **Next** until you reach the **Features** section.
6. In the **Select features** section, scroll down to find the **Remote Server Administration Tools** category.
7. Expand the **Remote Server Administration Tools** category to see the available tools.
8. Select the specific tools you want to install by checking the corresponding checkboxes.
9. Select **Next** and then select **Install** to begin the installation process.
10. Wait for the installation to complete, then select **Close**.
11. Once the installation is complete, you can access the tools from the **Tools** menu in Server Manager or selecting **Windows Tools** from the Start menu.

# [Windows PowerShell](#tab/windows-powershell)
To install Remote Server Administration Tools using the Install-WindowsFeature PowerShell cmdlet, follow these steps:

1. Sign in to the Windows Server computer with an account that has administrative privileges.
2. Open **Windows PowerShell** with administrative privileges (Run as Administrator).
3. To review the tools available for installation, run the following command and take note of the specific tools you want to install:

    ```powershell
    Get-WindowsFeature -Name RSAT*
    ```
4. Install the desired RSAT tools by running the following command, replacing `<FeatureName>` with the specific feature names you want to install. You can specify multiple features by separating them with commas.

    ```powershell
    Install-WindowsFeature -Name <FeatureName> -IncludeAllSubFeature
    ```

    For example, to install the Active Directory Domain Services tools, you would run:

    ```powershell
    Install-WindowsFeature -Name RSAT-AD-Tools -IncludeAllSubFeature
    ```
5. After the installation is complete, you can access the tools from the **Tools** menu in Server Manager or selecting **Windows Tools** from the Start menu.

---

::: zone-end

::: zone pivot="windows-client-11"

### Install RSAT as Feature on Demand

Some RSAT tools are available as **Features on Demand**, review the Available tools to see which tools are available as Features on Demand.

To install Remote Server Administration Tools on Windows client, select your preferred method:

# [Desktop experience](#tab/desktop-experience)
To install RSAT using the desktop experience:

1. Sign in to the Windows client computer with an account that has administrative privileges.
2. Select **Start**, type *Optional Features* in the search box, then select **Add an optional feature**.
3. Scan the list to see if the tool you need is already installed. If not, at the top of the page, select **Views features**, then:

    - Search for and select the tool you want to install, select **Next**, then **Install**
4. Review the installation progress. Once the installation is complete, you can access the tools from the **Tools** menu in Server Manager or selecting **Windows Tools** from the Start menu.

# [PowerShell](#tab/powershell)
To install Remote Server Administration Tools using PowerShell, follow these steps:

1. Run PowerShell as an Administrator.
2. Run the following cmdlet to make sure that OpenSSH is available:

    ```powershell
    Get-WindowsCapability -Online | Where-Object Name -like 'RSAT*'
    ```

    The command should return the following output if neither are already installed:

    ```powershell
    Name  : Rsat.ActiveDirectory.DS-LDS.Tools~~~~0.0.1.0
    State : NotPresent
    ```
3. After that, run the following cmdlets to the tool you need, replacing `<FeatureName>` with the specific feature names you want to install. You can specify multiple features by separating them with commas:

    ```powershell
    # Install the Active Directory Domain Services tools
    Add-WindowsCapability -Online -Name Rsat.ActiveDirectory.DS-LDS.Tools~~~~0.0.1.0
    ```

    Both commands should return the following output:

    ```powershell
    Path          :
    Online        : True
    RestartNeeded : False
    ```

---

### Install RSAT as a Windows Feature

To install RSAT using the Windows Features dialog, select your preferred method:

# [Desktop experience](#tab/desktop-experience)
To install RSAT using the desktop experience:

1. Select **Start**, type *Windows Features* in the search box, then select **Turn Windows features on or off**.
2. In the **Windows Features** dialog box, search for tool you want to install, such as **Hyper-V Management Tools**, and check the box next to it. You might need to expand the category to see the specific tool.
3. Select **OK** to install the selected RSAT tools.
4. Once the installation is complete, you can access the tools from the **Tools** menu in Server Manager or selecting **Windows Tools** from the Start menu.

# [PowerShell](#tab/powershell)
To install RSAT Windows Features using PowerShell, follow these steps:

1. Run PowerShell as an Administrator.
2. Run the following cmdlet to make sure that RSAT is available. If you prefer, you can replace `*Tools*` with the specific feature name you want to install:

    ```powershell
    Get-WindowsOptionalFeature -Online -FeatureName *tools* | FT FeatureName,DisplayName,Description,State
    ```

    The command should return the following output if neither are already installed:

    ```powershell
    FeatureName                  DisplayName                                 Description
    -----------                  -----------                                 -----------
    IIS-WebServerManagementTools Web Management Tools                        Install Web management console and tools
    IIS-ManagementScriptingTools IIS Management Scripts and Tools            Manage a local Web server with IIS configur...
    Microsoft-Hyper-V-Tools-All  Hyper-V Management Tools                    Includes GUI and command-line tools for man...
    ```
3. Install the desired RSAT tools by running the following command, replacing `<FeatureName>` with the specific feature names you want to install. Using the `-All` switch enables the parent and all of its default dependencies if required by the feature.

    ```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName <FeatureName> -All
    ```
4. After the installation is complete, you can access the tools from the **Tools** menu in Server Manager or selecting **Windows Tools** from the Start menu.

---

::: zone-end

::: zone pivot="windows-client-10"

### Install RSAT as Feature on Demand

Some RSAT tools are available as Features on Demand, review the Available tools to see which tools are available as Features on Demand.

To install Remote Server Administration Tools on Windows client, select your preferred method:

# [Desktop experience](#tab/desktop-experience)
To install RSAT using the desktop experience:

1. Sign in to the Windows client computer with an account that has administrative privileges.
2. Select **Start**, type *Optional Features* in the search box, then select **Optional Features** (also referred to as **Manage optional features**).
3. Scan the list to see if the tool you need is already installed. If not, at the top of the page, select **Add a feature**, then:

    - Search for the tool you want to install, then select **Install**
4. Review the installation progress. Once the installation is complete, you can access the tools from the **Tools** menu in Server Manager or selecting **Windows Tools** from the Start menu.

# [PowerShell](#tab/powershell)
To install Remote Server Administration Tools using PowerShell, follow these steps:

1. Run PowerShell as an Administrator.
2. Run the following cmdlet to make sure that RSAT is available:

    ```powershell
    Get-WindowsCapability -Online | Where-Object Name -like 'RSAT*'
    ```

    The command should return the following output if neither are already installed:

    ```powershell
    Name  : Rsat.ActiveDirectory.DS-LDS.Tools~~~~0.0.1.0
    State : NotPresent
    ```
3. After that, run the following cmdlets to the tool you need, replacing `<FeatureName>` with the specific feature names you want to install. You can specify multiple features by separating them with commas:

    ```powershell
    # Install the Active Directory Domain Services tools
    Add-WindowsCapability -Online -Name Rsat.ActiveDirectory.DS-LDS.Tools~~~~0.0.1.0
    ```

    Both commands should return the following output:

    ```powershell
    Path          :
    Online        : True
    RestartNeeded : False
    ```

---

### Install RSAT as a Windows Feature

To install RSAT using the Windows Features dialog, select your preferred method:

# [Desktop experience](#tab/desktop-experience)
To install RSAT using the desktop experience:

1. Select **Start**, type *Windows Features* in the search box, then select **Turn Windows features on or off**.
2. In the **Windows Features** dialog box, search for tool you want to install, such as **Hyper-V Management Tools**, and check the box next to it. You might need to expand the category to see the specific tool.
3. Select **OK** to install the selected RSAT tools.
4. Once the installation is complete, you can access the tools from the **Tools** menu in Server Manager or selecting **Windows Tools** from the Start menu.

# [PowerShell](#tab/powershell)
To install RSAT Windows Features using PowerShell, follow these steps:

1. Run PowerShell as an Administrator.
2. Run the following cmdlet to make sure that RSAT is available. If you prefer, you can replace `*Tools*` with the specific feature name you want to install:

    ```powershell
    Get-WindowsOptionalFeature -Online -FeatureName *tools* | FT FeatureName,DisplayName,Description,State
    ```

    The command should return the following output if neither are already installed:

    ```powershell
    FeatureName                  DisplayName                                 Description
    -----------                  -----------                                 -----------
    IIS-WebServerManagementTools Web Management Tools                        Install Web management console and tools
    IIS-ManagementScriptingTools IIS Management Scripts and Tools            Manage a local Web server with IIS configur...
    Microsoft-Hyper-V-Tools-All  Hyper-V Management Tools                    Includes GUI and command-line tools for man...
    ```
3. Install the desired RSAT tools by running the following command, replacing `<FeatureName>` with the specific feature names you want to install. Using the `-All` switch enables the parent and all of its default dependencies if required by the feature.

    ```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName <FeatureName> -All
    ```
4. After the installation is complete, you can access the tools from the **Tools** menu in Server Manager or selecting **Windows Tools** from the Start menu.

---

::: zone-end

## Manage local and remote servers with Server Manager

Server Manager can be used along with the other tools included in Remote Server Administration Tools to manage both local and remote servers from a single experience. You can use Server Manager to install, configure, and manage roles and features on multiple remote servers from a single console.

::: zone pivot="windows-server-2025,windows-server-2022,windows-server-2019,windows-server-2016"

Server Manager is included with Windows Server by default and doesn't need to be installed separately. In the following steps, you'll use Server Manager to add an example Remote Server Administration Tool and launch the associated management tool.

1. For new installations of Windows Server, Server Manager opens automatically by default. If Server Manager doesn't open automatically, open the Start menu, then select **Server Manager**.

    ![Screenshot showing Server Manager Dashboard with configuration options and status tiles for installed roles.](media/install-remote-server-administration-tools/server-manager.png)
2. In Server Manager, select on **Manage** in the top right corner.
3. Select **Add Roles and Features** from the dropdown menu.
4. In the **Add Roles and Features Wizard**, select **Next** until you reach the **Features** section.
5. Expand the **Remote Server Administration Tools** category, then expand the **Role Administration Tools** category.
6. Select the checkbox next to **DNS Server Tools**, then select **Next**.
7. Select **Install** to begin the installation process.
8. Select **Close** once the installation is complete.
9. To manage a DNS server, select **Tools** in the top right corner of Server Manager, then select **DNS** from the dropdown menu.
10. You can now use the DNS Manager console to manage the DNS server or right-click the server name in the left pane to connect to a different DNS server.

To learn more about using Server Manager to manage remote servers, see [Server Manager](server-manager/server-manager).

::: zone-end

::: zone pivot="windows-client-11,windows-client-10"

Server Manager is included with Remote Server Administration Tools and can be installed as a Feature on Demand. In the following steps, you'll install Server Manager and use to add an example role to a remote server and launch the associated management tool.

1. Install the *RSAT: Server Manager* feature on demand by following the steps in the Install RSAT as Feature on Demand section.
2. Install any other RSAT tools you want to use, such as the *RSAT: DNS Server Tools*.
3. Once installed, open the Start menu, type *Server Manager*, then select **Server Manager** from the search results.
4. In Server Manager, select on **Tools** in the top right corner.
5. Select the tool you want to use, such as **DNS** from the dropdown menu.
6. When prompted, enter the name or IP address of the remote server you want to manage, then select **OK**.

    ![A screenshot showing Server Manager with the DNS Manager window open.](media/install-remote-server-administration-tools/server-manager-dns-tools.png)

To learn more about using Server Manager to manage remote servers, see [Server Manager](server-manager/server-manager).

::: zone-end