---
layout: Conceptual
title: Upgrade Windows Server in Place | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/upgrade-in-place
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: Learn how to upgrade Windows Server in place using installation media or Windows Update. Keep settings, server roles, and data intact.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2026-04-14T00:00:00.0000000Z
locale: en-us
document_id: 26a28fb3-5359-dcd1-7361-64deec4f1fd5
document_version_independent_id: fd95c553-bd8d-f060-5bfe-ad5b69ab1216
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/upgrade-in-place.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/upgrade-in-place
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/upgrade-in-place.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 04e6ecbb-3ac9-e692-67bc-1d58e3837271
---

# Upgrade Windows Server in Place | Microsoft Learn

An in-place upgrade moves your server from an older version of Windows Server to a newer version while keeping your settings, server roles, and data intact. For example, you can upgrade from Windows Server 2012 R2 to Windows Server 2025. When you upgrade in place, your environment stays running on a supported version with the latest security and performance features, all without rebuilding.

This article shows you how to upgrade by using Windows Server Setup from installation media or the feature update in Windows Update.

## Prerequisites

- To determine the Windows Server versions and supported upgrade paths, see [Supported in-place upgrade paths by version](install-upgrade-migrate#supported-in-place-upgrade-paths-by-version).
- Administrative rights on the target server.
- A full backup of your server, including the operating system, apps, data, and any VMs. Perform a restore test to confirm the backup is valid and recoverable. You can use Windows Server Backup or a partner backup solution.
- A scheduled maintenance window, as downtime is required during the upgrade.
- Knowledge of:

    - The roles and features that support an in-place upgrade. See [Upgrade and migrate roles and features in Windows Server](upgrade-migrate-roles-features).
    - The Microsoft server applications that are supported on Windows Server. See [Microsoft server applications compatibility for Windows Server](application-compatibility).
    - Any non-Microsoft application vendor support requirements.
- A server that:

    - Meets or exceeds the [hardware requirements for Windows Server](hardware-requirements).
    - Isn't clustered. If you're running a cluster, use the [Cluster-Aware Updating](../failover-clustering/cluster-aware-updating) feature or a [cluster operating system rolling upgrade](../failover-clustering/cluster-operating-system-rolling-upgrade) instead.
- A valid product key and activation method. Keys and methods can vary depending on the distribution channel that you received the Windows Server media from, such as a Commercial Licensing program, a retail channel, or an OEM.
- A location to store files away from your server, such as a USB flash drive or network location.
- If Configuration Manager is installed on a Windows Server 2012 or Windows Server 2012 R2 server, follow the preupgrade and post-upgrade instructions at [Upgrade on-premises infrastructure that supports Configuration Manager](/en-us/mem/configmgr/core/servers/manage/upgrade-on-premises-infrastructure#before-upgrade).

Important

Don't use in-place upgrade for servers that run Active Directory Domain Services (AD DS). Although an in-place upgrade is technically possible, it doesn't deliver the AD performance and feature improvements included in Windows Server 2025 and later. Instead, use a clean OS install to promote new domain controllers and demote the older ones. For more information, see [Upgrade domain controllers to a newer version of Windows Server](../identity/ad-ds/deploy/upgrade-domain-controllers).

Depending on whether you upgrade by using installation media or Windows Update, you need to meet additional prerequisites. Select the tab for your upgrade method:

# [Installation media](#tab/media)
The installation media upgrade method applies to non-Azure servers only. To upgrade Windows Server in an Azure virtual machine (VM), see [In-place upgrade for VMs running Windows Server in Azure](/en-us/azure/virtual-machines/windows-in-place-upgrade) or use the Windows Update method.

- Installation media (ISO image, USB drive, or DVD) for the version of Windows Server that you want to upgrade to.
- You can get installation media for your target version of Windows Server from an original equipment manufacturer (OEM), a retail distribution channel, a Visual Studio subscription, or the Microsoft 365 admin center.

# [Windows Update](#tab/windows-update)
To upgrade to Windows Server 2025 or later by using Windows Update, you need:

- Windows Server 2019 or Windows Server 2022 on all servers you want to upgrade.
- The required cumulative update installed on all servers you want to upgrade. Install the correct update for your operating system and restart the server if required.
    - [2026-03 Cumulative Update for Microsoft server operating system version 21H2 for x64-based Systems (KB5078766)](https://support.microsoft.com/help/5078766) or later for Windows Server 2022
    - [2026-03 Cumulative Update for Microsoft server operating system for x64-based Systems (KB5078752)](https://support.microsoft.com/help/5078752) or later for Windows Server 2019

---

## Collect pre-upgrade diagnostic information

Collect diagnostic information from your server before upgrading in case the upgrade fails. Store the diagnostic files where you can access them if your server goes down.

To collect your information:

1. Open an elevated PowerShell prompt, make a note of your current directory, and run the following commands:

    ```powershell
    Get-ComputerInfo -Property WindowsBuildLabEx,WindowsEditionID | Out-File -FilePath .\computerinfo.txt
    systeminfo.exe | Out-File -FilePath systeminfo.txt
    ipconfig /all | Out-File -FilePath ipconfig.txt
    ```

    The `Get-ComputerInfo` command requires PowerShell 5.1 or later. If your Windows Server version doesn't include PowerShell 5.1, open Registry Editor and find the `BuildLabEx` and `EditionID` values under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion`.
2. Open File Explorer, go to the directory you noted, and copy the files to a USB flash drive or network location off your computer.

Back up your server operating system, apps, and VMs after collecting your system information. Shut down or migrate any VMs currently running on the server. Make sure no VMs are running during the upgrade.

## Perform the in-place upgrade

You can perform the in-place upgrade by using installation media or Windows Update. Select the tab for your upgrade method:

# [Installation media](#tab/media)
Tip

Looking for a way to upgrade without installation media? Use the Windows Update tab to upgrade without needing installation media.

Run Windows Server Setup from your installation media to do the in-place upgrade. This procedure applies to non-Azure, nonclustered servers running Windows Server 2012 R2 or later. During the upgrade, your server restarts several times.

To do the in-place upgrade by using installation media:

1. Mount or insert the installation media. Open File Explorer, go to the root of the installation media, and then open `setup.exe`. For example, if you mounted an ISO image or inserted a DVD as drive D, the file path is `D:\setup.exe`. If **User Account Control** prompts you to allow Setup to make changes, select **Yes**.
2. By default, Setup automatically downloads updates for the installation. If you're okay with the default settings, select **Next** to continue.

    If you don't want Setup to automatically download updates, select **Change how Setup downloads updates**, select the appropriate option for your environment, and then select **Next**.
3. If prompted, enter your product key, and then select **Next**.
4. Select the edition of Windows Server you want to install, and then select **Next**.
5. Review the applicable notices and license terms. If you agree to the terms, select **Accept**.
6. Select **Keep files, settings, and apps** to do an in-place upgrade, and then select **Next**.
7. After Setup finishes analyzing your device, it displays the **Ready to install** screen. To start the in-place upgrade, select **Install**.

The in-place upgrade starts, and the screen displays the progress. After the in-place upgrade finishes, your server restarts.

# [Windows Update](#tab/windows-update)
Use the Windows Server feature update in Windows Update to perform the in-place upgrade without installation media.

### Enable the feature update from Windows Update

Add the following registry value to enable the feature update.

Open an elevated PowerShell prompt and run the following command:

```powershell
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AllowWindowsServerFeatureUpdate"
New-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AllowWindowsServerFeatureUpdate" -Name "AllowWindowsServerFeatureUpdate" -PropertyType DWord -Value 1
```

Alternatively, you can set the value manually in Registry Editor:

1. Open Registry Editor.
2. Go to `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AllowWindowsServerFeatureUpdate`.
3. Create a new `DWORD` value named `AllowWindowsServerFeatureUpdate` and set it to `1`.

    ![Screenshot of Registry Editor showing the AllowWindowsServerFeatureUpdate DWORD value set to 1 under the WindowsUpdate key.](media/upgrade-in-place/registry.png)

### Upgrade by using Windows Update

When you meet all the prerequisites and see the Windows Server feature update in Windows Update, proceed with the in-place upgrade.

1. Open **Settings**, and then select **Windows Update**. Verify that the feature update offer banner is visible.

    ![Screenshot of the Windows Update settings page showing the Windows Server 2025 feature update available with a Download and install link.](media/upgrade-in-place/windows-update-feature-update.png)
2. Select **Download and Install** to begin the feature update process.
3. Review the **Important Information** for pricing, best practices, licenses, and privacy.
4. Select **Accept and install** to proceed with the download and installation of the feature update.
5. Wait for the feature update to download and install. Your server restarts during the installation.

Tip

The feature update is also available for Server Core installations. Use SConfig option **6** to search for and install the feature update. For more information, see [Configure Windows Server Core Windows Update](../administration/server-core/server-core-servicing).

---

## Verify the in-place upgrade

After the server restarts, verify the upgrade succeeded by checking the Windows Server version and testing your applications.

1. Open an elevated PowerShell prompt. Run the following command to verify that the version and edition match what you expected.

    ```powershell
    Get-ComputerInfo -Property WindowsProductName
    ```
2. Ensure all applications are running and client connections are successful.

If your server isn't working as expected after the in-place upgrade, analyze the Setup log files in the `C:\Windows\Panther` directory. Also download the [`SetupDiag`](/en-us/windows/deployment/upgrade/setupdiag) tool to analyze the Setup log files.

If you need technical assistance, contact [Microsoft Support](https://support.microsoft.com/contactus).