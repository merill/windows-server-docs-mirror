---
layout: Conceptual
title: Remote Desktop IP virtualization in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/internet-protocol-virtualization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: How to use IP address virtualization for Winsock applications using Remote Desktop in Windows Server 2019 and later.
author: robinharwood
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: how-to
ms.author: roharwoo
locale: en-us
document_id: e7f65ad4-fd85-9447-b022-ed18f6324fb8
document_version_independent_id: e7f65ad4-fd85-9447-b022-ed18f6324fb8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/internet-protocol-virtualization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/internet-protocol-virtualization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/internet-protocol-virtualization.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 49aa7023-1e9c-73fe-6c5a-6c98c545cbbe
---

# Remote Desktop IP virtualization in Windows Server | Microsoft Learn

As of Windows Server 2008 R2, Remote Desktop session hosts support per-session and per-program Remote Desktop IP Virtualization for Winsock applications. Remote Desktop assigns individual IP addresses to user sessions to avoid application compatibility issues that can happen when all Remote Desktop users in the same location share the same IP address. This article gives instructions for how to virtualize IP addresses for your organization's Remote Desktop users.

Note

This article's instructions for virtualizing IPs only apply to on-premises environments.

## Prerequisites

In order to use IP Virtualization, your system must meet the following requirements:

- Your deployment must run Windows Server 2019 or later.
- You must assign the RD Session Host server role to the machine you use to make the changes.

## How to configure IP Virtualization

You can configure IP Virtualization using the Microsoft Management Console (MMC), Group Policy, or running a command in a PowerShell window.

# [Microsoft Management Console](#tab/mmc)
1. Open the RD Session Host Configuration MMC on the machine you the RD Session Host server role.
2. Go to **Edit settings**.
3. Select **IP Virtualization** and go to **Properties**.
4. Select the **Enable IP virtualization** check box.
5. In the **Select the network adapter to be used for IP Virtualization** field, select the network adapter you want to use for IP Virtualization from the drop-down menu.

    Note

    IP virtualization currently only supports single-network adapter scenarios. If your server has multiple enabled network adapters, you can only use the adapter you specify in the settings for IP virtualization.
6. When you're finished, select **Apply**.
7. Optionally, to configure IP virtualization for specific programs:

    - Return to **Edit settings**, then select **Add program**.
    - Enter or navigate to the file path of the program you want to use.
    - Select **Open**.
    - Repeat for all programs you want to use.
    - When you're finished, select **Apply**.

# [Group Policy](#tab/group-policy)
1. Open the **Group policy editor (gpedit.msc)** on the machine you want to make changes to.
2. Go to **Computer configuration** &gt; **Administrative Templates** &gt; **Windows Components** &gt; **Remote Desktop Services** &gt; **Remote Desktop Session Host** &gt; **Application Compatibility**.
3. Right-click **Select the network adapter to be used for Remote Desktop IP Virtualization**, then select **Edit**.
4. Select **Enabled**.

    Note

    IP virtualization currently only supports single-network adapter scenarios. If your server has multiple enabled network adapters, you can only use the adapter you specify in the settings for IP virtualization.
5. To apply this policy to a specific IP address and network mask, go to the **Define IP address** field and enter the IP address and network mask based on the format `<IP address/<network mask>`.
6. When you're finished, select **Apply**.
7. Next, right-click **Turn on Remote Desktop IP Virtualization**, then select **Edit**.
8. Select **Enabled**.
9. Optionally, if you want to configure virtualization for per-program mode:

    - Select **Per Program**
    - Enter the name or full file path of each program you want to add.
10. When you're finished, select **Apply**.

Optionally, you can also configure the **Do not use Remote Desktop Session Host server IP address when virtual IP address is not available** policy to prevent your deployment from using the IP address of the Remote Desktop Session Host server when virtualized IP addresses aren't available.

To enable this policy:

1. Right-click **Do not use Remote Desktop Session Host server IP address when virtual IP address is not available**, then select **Edit**.
2. Select **Enabled**.
3. Select **Apply**.

# [PowerShell](#tab/powershell)
1. Open an elevated PowerShell window.
2. Run the following cmdlet to rename the registry key:

    ```powershell
    Rename-Item HKLM:\SYSTEM\CurrentControlSet\Services\WinSock2\Parameters\AppId_Catalog\2C69D9F1 Backup_2C69D9F1
    ```

    Note

    We recommend you rename the registry key instead of deleting it, as this lets you revert your settings more easily. To revert your settings, change the name and values back to the following default settings:

    - Name: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WinSock2\Parameters\AppId_Catalog\2C69D9F1\`
    - *AppFullPath*: C:\Windows\System32\svchost.exe\
    - *PermittedLspCategories*: 0x40000000
3. Restart your machine for the changes to take effect.
4. Run the following command to enable the **Turn on Remote Desktop IP Virtualization** group policy.

    ```powershell
    Set-GPRegistryValue -Name "Remote Desktop IP Virtualization" -Key "HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Terminal Services" -ValueName "IPFilterBitmaps" -Type DWORD -Value 1
    ```
5. Restart your machine for the changes to take effect.

---