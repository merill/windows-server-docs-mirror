---
layout: Conceptual
title: Get started with OpenSSH Server for Windows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Learn how to install and connect to remote machines using the OpenSSH Client and Server for Windows.
ms.date: 2025-09-04T00:00:00.0000000Z
ms.topic: quickstart
ms.author: roharwoo
author: robinharwood
ms.custom: se-defect-target
ai-usage: ai-assisted
zone_pivot_groups: openssh-windows-version
locale: en-us
document_id: 18a5a4e5-2604-23c2-1374-68a6974170bc
document_version_independent_id: f93809cc-eb5e-6b9b-ed58-c8811a8ee21f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/OpenSSH/OpenSSH_Install_FirstUse.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/openssh/openssh_install_firstuse
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/OpenSSH/OpenSSH_Install_FirstUse.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
2PlusCloud: []
platformId: 59c49c05-304e-0a54-8ac2-3798f16f4d15
---

# Get started with OpenSSH Server for Windows | Microsoft Learn

OpenSSH is a connectivity tool for remote sign-in that uses the SSH protocol. It encrypts all traffic between client and server to eliminate eavesdropping, connection hijacking, and other attacks.

An OpenSSH-compatible client can be used to connect to Windows Server and Windows client devices.

This article uses the in-box OpenSSH Feature on Demand in Windows and Windows Server. Microsoft supports and services this version through Windows Update, so it's the recommended option for most users.

Microsoft also maintains [PowerShell/openssh-portable](https://github.com/PowerShell/openssh-portable), a fork of the upstream, open-source OpenSSH project. Its releases might differ from the version in Windows.

## Prerequisites

Before you start, your computer must meet the following requirements:

- A device running at least Windows Server 2019 or Windows 10 (build 1809).
- PowerShell 5.1 or later.
- An account that is a member of the built-in Administrators group.

### Prerequisites check

To validate your environment, open an elevated PowerShell session and do the following:

- Enter *winver.exe* and press enter to see the version details for your Windows device.
- Run `$PSVersionTable.PSVersion`. Verify your major version is at least 5, and your minor version at least 1. Learn more about [installing PowerShell on Windows](/en-us/powershell/scripting/install/installing-powershell-on-windows).
- To check when you're an administrator, run the following command. The output shows `True` when you're a member of the built-in Administrators group.

    ```powershell
    (New-Object Security.Principal.WindowsPrincipal([Security.Principal.WindowsIdentity]::GetCurrent())).IsInRole([Security.Principal.WindowsBuiltInRole]::Administrator)
    ```

::: zone pivot="windows-server-2025"

## Enable OpenSSH Server

Beginning with Windows Server 2025, OpenSSH is now installed by default. You can also enable or disable the `sshd` service in Server Manager.

# [GUI](#tab/gui)
To enable SSHD using Server Manager:

1. In **Server Manager**, on the navigation pane to the left, select **Local Server**.
2. In the **Properties** window, locate **Remote SSH Access**.
3. Select **Enabled** to enable the OpenSSH service.

Note

If you need to allow or restrict specific users or groups from using OpenSSH for remote access, add them to the **OpenSSH Users** user group.

# [PowerShell](#tab/powershell)
To enable SSHD using PowerShell:

1. Open PowerShell as an administrator and run the following cmdlet to start the SSHD service:

    ```powershell
    # Start the sshd service
    Start-Service sshd
    ```
2. You can also run the following optional but recommended cmdlet to automatically start SSHD to make sure it stays enabled:

    ```powershell
    Set-Service -Name sshd -StartupType 'Automatic'
    ```
3. Finally, run the following command to verify that the SSHD setup process automatically configured the firewall rule:

    ```powershell
    if (!(Get-NetFirewallRule -Name "OpenSSH-Server-In-TCP" -ErrorAction SilentlyContinue)) {
        Write-Output "Firewall Rule 'OpenSSH-Server-In-TCP' does not exist, creating it..."
        New-NetFirewallRule -Name 'OpenSSH-Server-In-TCP' -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
    } else {
        Write-Output "Firewall rule 'OpenSSH-Server-In-TCP' has been created and exists."
    }
    ```

---

::: zone-end

::: zone pivot="windows-11"

## Install OpenSSH Server & Client

# [GUI](#tab/gui)
To install the OpenSSH components on Windows Server devices:

1. Select **Start**, type *Optional Features* in the search box, then select **Optional Features**.
2. Scan the list to see if the OpenSSH is already installed. If not, at the top of the page, select **Views features**, then:

    - Search for and select **OpenSSH Client**, then select **Add**
    - Search for and select **OpenSSH Server**, then select **Add**
3. Open the **Services** desktop app. (Select **Start**, type *services.msc* in the search box, and then select the **Services** app or press ENTER.)
4. In the details pane, double-click **OpenSSH SSH Server**.
5. On the **General** tab, from the **Startup type** drop-down menu, select **Automatic** and then select **Ok**.
6. To start the service, select **Start**.

Note

Installing OpenSSH Server creates and enables a firewall rule named `OpenSSH-Server-In-TCP`. This rule allows inbound SSH traffic on port 22. If this rule isn't enabled and this port isn't open, connections are refused or reset.

# [PowerShell](#tab/powershell)
To install OpenSSH using PowerShell:

1. Run PowerShell as an Administrator.
2. Run the following cmdlet to make sure that OpenSSH is available:

    ```powershell
    Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
    ```

    The command should return the following output if neither are already installed:

    ```powershell
    Name  : OpenSSH.Client~~~~0.0.1.0
    State : NotPresent
    
    Name  : OpenSSH.Server~~~~0.0.1.0
    State : NotPresent
    ```
3. After that, run the following cmdlets to install the server or client components as needed:

    ```powershell
    # Install the OpenSSH Client
    Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
    
    # Install the OpenSSH Server
    Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
    ```

    Both commands should return the following output:

    ```powershell
    Path          :
    Online        : True
    RestartNeeded : False
    ```
4. To start and configure OpenSSH Server for initial use, open an elevated PowerShell prompt (right-click, then select **Run as an administrator**), then run the following commands to start the `sshd service`:

    ```powershell
    # Start the sshd service
    Start-Service sshd
    
    # OPTIONAL but recommended:
    Set-Service -Name sshd -StartupType 'Automatic'
    
    # Confirm the Firewall rule is configured. It should be created automatically by setup. Run the following to verify
    if (!(Get-NetFirewallRule -Name "OpenSSH-Server-In-TCP" -ErrorAction SilentlyContinue)) {
        Write-Output "Firewall Rule 'OpenSSH-Server-In-TCP' does not exist, creating it..."
        New-NetFirewallRule -Name 'OpenSSH-Server-In-TCP' -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
    } else {
        Write-Output "Firewall rule 'OpenSSH-Server-In-TCP' has been created and exists."
    }
    ```

---

::: zone-end

::: zone pivot="windows-server-2022"

## Install OpenSSH Server & Client

# [GUI](#tab/gui)
To install the OpenSSH components on Windows Server devices:

1. Select **Start**, type *Optional Feature* in the search box, then select **Add an optional feature**.
2. Scan the list to see if the OpenSSH is already installed. If not, at the top of the page, select **Add a feature**, then:

    - Search for **OpenSSH Client**, then select **Install**
    - Search for **OpenSSH Server**, then select **Install**
3. Open the **Services** desktop app. (Select **Start**, type *services.msc* in the search box, and then select the **Services** app or press ENTER.)
4. In the details pane, double-click **OpenSSH SSH Server**.
5. On the **General** tab, from the **Startup type** drop-down menu, select **Automatic** and then select **Ok**.
6. To start the service, select **Start**.

Note

Installing OpenSSH Server creates and enables a firewall rule named `OpenSSH-Server-In-TCP`. This rule allows inbound SSH traffic on port 22. If this rule isn't enabled and this port isn't open, connections are refused or reset.

# [PowerShell](#tab/powershell)
To install OpenSSH using PowerShell:

1. Run PowerShell as an Administrator.
2. Run the following cmdlet to make sure that OpenSSH is available:

    ```powershell
    Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
    ```

    The command should return the following output if neither are already installed:

    ```powershell
    Name  : OpenSSH.Client~~~~0.0.1.0
    State : NotPresent
    
    Name  : OpenSSH.Server~~~~0.0.1.0
    State : NotPresent
    ```
3. After that, run the following cmdlets to install the server or client components as needed:

    ```powershell
    # Install the OpenSSH Client
    Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
    
    # Install the OpenSSH Server
    Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
    ```

    Both commands should return the following output:

    ```powershell
    Path          :
    Online        : True
    RestartNeeded : False
    ```
4. To start and configure OpenSSH Server for initial use, open an elevated PowerShell prompt (right-click, then select **Run as an administrator**), then run the following commands to start the `sshd service`:

    ```powershell
    # Start the sshd service
    Start-Service sshd
    
    # OPTIONAL but recommended:
    Set-Service -Name sshd -StartupType 'Automatic'
    
    # Confirm the Firewall rule is configured. It should be created automatically by setup. Run the following to verify
    if (!(Get-NetFirewallRule -Name "OpenSSH-Server-In-TCP" -ErrorAction SilentlyContinue)) {
        Write-Output "Firewall Rule 'OpenSSH-Server-In-TCP' does not exist, creating it..."
        New-NetFirewallRule -Name 'OpenSSH-Server-In-TCP' -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
    } else {
        Write-Output "Firewall rule 'OpenSSH-Server-In-TCP' has been created and exists."
    }
    ```

---

::: zone-end

::: zone pivot="windows-server-2019,windows-10"

## Install OpenSSH Server & Client

# [GUI](#tab/gui)
To install the OpenSSH components on Windows Server devices:

1. Select **Start**, type *Optional Features* in the search box, then select **Optional Features** (also referred to as **Manage optional features**).
2. Scan the list to see if the OpenSSH is already installed. If not, at the top of the page, select **Add a feature**, then:

    - Search for **OpenSSH Client**, then select **Install**
    - Search for **OpenSSH Server**, then select **Install**
3. Open the **Services** desktop app. (Select **Start**, type *services.msc* in the search box, and then select the **Services** app or press ENTER.)
4. In the details pane, double-click **OpenSSH SSH Server**.
5. On the **General** tab, from the **Startup type** drop-down menu, select **Automatic** and then select **Ok**.
6. To start the service, select **Start**.

Note

Installing OpenSSH Server creates and enables a firewall rule named `OpenSSH-Server-In-TCP`. This rule allows inbound SSH traffic on port 22. If this rule isn't enabled and this port isn't open, connections are refused or reset.

# [PowerShell](#tab/powershell)
To install OpenSSH using PowerShell:

1. Run PowerShell as an Administrator.
2. Run the following cmdlet to make sure that OpenSSH is available:

    ```powershell
    Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
    ```

    The command should return the following output if neither are already installed:

    ```powershell
    Name  : OpenSSH.Client~~~~0.0.1.0
    State : NotPresent
    
    Name  : OpenSSH.Server~~~~0.0.1.0
    State : NotPresent
    ```
3. After that, run the following cmdlets to install the server or client components as needed:

    ```powershell
    # Install the OpenSSH Client
    Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
    
    # Install the OpenSSH Server
    Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
    ```

    Both commands should return the following output:

    ```powershell
    Path          :
    Online        : True
    RestartNeeded : False
    ```
4. To start and configure OpenSSH Server for initial use, open an elevated PowerShell prompt (right-click, then select **Run as an administrator**), then run the following commands to start the `sshd service`:

    ```powershell
    # Start the sshd service
    Start-Service sshd
    
    # OPTIONAL but recommended:
    Set-Service -Name sshd -StartupType 'Automatic'
    
    # Confirm the Firewall rule is configured. It should be created automatically by setup. Run the following to verify
    if (!(Get-NetFirewallRule -Name "OpenSSH-Server-In-TCP" -ErrorAction SilentlyContinue)) {
        Write-Output "Firewall Rule 'OpenSSH-Server-In-TCP' does not exist, creating it..."
        New-NetFirewallRule -Name 'OpenSSH-Server-In-TCP' -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
    } else {
        Write-Output "Firewall rule 'OpenSSH-Server-In-TCP' has been created and exists."
    }
    ```

---

::: zone-end

## Connect to OpenSSH Server

Once installed, you can connect to OpenSSH Server from a Windows or Windows Server device with the OpenSSH client installed. From a PowerShell prompt, run the following command.

```powershell
ssh domain\username@servername
```

Once connected, you get a message similar to the following output.

```powershell
The authenticity of host 'servername (10.00.00.001)' can't be established.
ECDSA key fingerprint is SHA256:(<a large string>).
Are you sure you want to continue connecting (yes/no)?
```

Entering *yes* adds that server to the list of known SSH hosts on your Windows client.

At this point, the service prompts you for your password. As a security precaution, the characters of your password aren't displayed as you enter them.

Once connected, you should see the following Windows command shell prompt:

```powershell
domain\username@SERVERNAME C:\Users\username>
```

::: zone pivot="windows-server-2025"

## Disable OpenSSH Server

You can disable the `sshd` service in Server Manager.

# [GUI](#tab/gui)
To disable SSHD using Server Manager:

1. In **Server Manager**, on the navigation pane to the left, select **Local Server**.
2. In the **Properties** window, locate **Remote SSH Access**.
3. Select **Disabled** to disable the OpenSSH service.

Note

If you need to allow or restrict specific users or groups from using OpenSSH for remote access, add them to the **OpenSSH Users** user group.

# [PowerShell](#tab/powershell)
To disable SSHD using PowerShell:

1. Open PowerShell as an administrator and run the following cmdlet to start the SSHD service:

    ```powershell
    # Stop the sshd service
    Stop-Service sshd
    ```
2. You can also run the following optional but recommended cmdlet to automatically start SSHD to make sure it stays enabled:

    ```powershell
    Set-Service -Name sshd -StartupType 'Disabled'
    ```
3. Finally, run the following command to disable the default SSHD firewall rule:

    ```powershell
    if ((Get-NetFirewallRule -Name "OpenSSH-Server-In-TCP" -ErrorAction SilentlyContinue)) {
        Write-Output "Firewall rule 'OpenSSH-Server-In-TCP' is being disabled."
        Disable-NetFirewallRule -Name 'OpenSSH-Server-In-TCP'
    } else {
        Write-Output "Firewall Rule 'OpenSSH-Server-In-TCP' does not exist, disable failed..."
    }
    ```

---

::: zone-end

::: zone pivot="windows-11"

## Uninstall OpenSSH Server & Client

# [GUI](#tab/gui)
To uninstall OpenSSH using Windows Settings:

1. Select **Start**, type *Optional Features* in the search box, then select **Optional feature**.
2. Scan the list to see if the OpenSSH is installed:

    - Search for and select **OpenSSH Client**, then select **Remove**
    - Search for and select **OpenSSH Server**, then select **Remove**

# [PowerShell](#tab/powershell)
To uninstall the OpenSSH components using PowerShell, follow these steps.

1. Open PowerShell as an administrator.
2. To remove OpenSSH, use the following commands:

    ```powershell
    # Uninstall the OpenSSH Client
    Remove-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
    
    # Uninstall the OpenSSH Server
    Remove-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
    ```
3. Finally, run the following command to remove the firewall rule:

    ```powershell
    if ((Get-NetFirewallRule -Name "OpenSSH-Server-In-TCP" -ErrorAction SilentlyContinue)) {
        Write-Output "Firewall rule 'OpenSSH-Server-In-TCP' is being removed."
        Remove-NetFirewallRule -Name 'OpenSSH-Server-In-TCP'
    } else {
        Write-Output "Firewall Rule 'OpenSSH-Server-In-TCP' does not exist, removal failed..."
    }
    ```

---

::: zone-end

::: zone pivot="windows-server-2022,windows-server-2019,windows-10"

## Uninstall OpenSSH Server & Client

# [GUI](#tab/gui)
To uninstall OpenSSH using Windows Settings:

1. Select **Start**, type *Optional Features* in the search box, then select **Optional features** (also referred to as **Manage optional features** or **See optional feature history**).
2. In the list, select **OpenSSH Client** or **OpenSSH Server**.
3. Select **Uninstall**.

# [PowerShell](#tab/powershell)
To uninstall the OpenSSH components using PowerShell, follow these steps.

1. Open PowerShell as an administrator.
2. To remove OpenSSH, use the following commands:

    ```powershell
    # Uninstall the OpenSSH Client
    Remove-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
    
    # Uninstall the OpenSSH Server
    Remove-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
    ```
3. Finally, run the following command to remove the firewall rule:

    ```powershell
    if ((Get-NetFirewallRule -Name "OpenSSH-Server-In-TCP" -ErrorAction SilentlyContinue)) {
        Write-Output "Firewall rule 'OpenSSH-Server-In-TCP' is being removed."
        Remove-NetFirewallRule -Name 'OpenSSH-Server-In-TCP'
    } else {
        Write-Output "Firewall Rule 'OpenSSH-Server-In-TCP' does not exist, removal failed..."
    }
    ```

---

::: zone-end

If the service was in use when you uninstalled it, you should restart Windows.