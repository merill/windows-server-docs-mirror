---
layout: Conceptual
title: Change Remote Desktop listening port on Windows and Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/remotepc/change-listening-port
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn to change the Remote Desktop listening port on Windows and Windows Server for enhanced security or configuration.
ms.topic: how-to
ai-usage: ai-assisted
author: robinharwood
ms.author: roharwoo
ms.date: 2025-06-30T00:00:00.0000000Z
locale: en-us
document_id: 13054e70-b770-f803-4596-6d0ab3fe865c
document_version_independent_id: 3e474a79-1129-fdf6-bbd4-a12e0e7ebe27
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/remotepc/change-listening-port.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/remotepc/change-listening-port
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/remotepc/change-listening-port.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 4bee03eb-1cdf-79a3-1e7c-04cb4b3df18a
---

# Change Remote Desktop listening port on Windows and Windows Server | Microsoft Learn

Remote Desktop allows remote connections to computers running Windows or Windows Server over the Remote Desktop Protocol (RDP), listening on port 3389 by default. For security or configuration purposes, you might want to change this listening port. This article provides step-by-step instructions to modify the listening port using either PowerShell or the Registry Editor.

## Prerequisites

Before you begin, make sure you have the following items:

- Administrator access, or equivalent, to the computer you want to connect to.
- A computer with Remote Desktop enabled. For more information, see [Enable Remote Desktop](remote-desktop-allow-access).
- A client to test the changes from, such as Remote Desktop Connect (`mstsc.exe`) or [Windows App](/en-us/windows-app/get-started-connect-devices-desktops-apps).

## Configure the Remote Desktop listening port

The listening port for Remote Desktop is specified in the registry. To change the registry value, here's how to change it using PowerShell or the Registry Editor. Select the relevant tab for the method you prefer.

# [PowerShell](#tab/powershell)
To change the listening port using PowerShell, follow these steps:

1. Open PowerShell as an administrator.
2. Check the current port by running the following PowerShell command:

    ```powershell
    Get-ItemProperty -Path 'HKLM:\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name 'PortNumber'
    ```

    The output is similar to the following example:

    ```powershell
    PortNumber   : 3389
    PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp
    PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations
    PSChildName  : RDP-Tcp
    PSDrive      : HKLM
    PSProvider   : Microsoft.PowerShell.Core\Registry
    ```
3. Change the port by running the following PowerShell command. Be sure to replace `<Port Number>` with the new port number.

    ```powershell
    $portValue = '<Port Number>'
    
    Set-ItemProperty -Path 'HKLM:\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name 'PortNumber' -Value $portValue
    ```

# [Registry Editor](#tab/regedit)
To change the listening port using the Registry Editor, follow these steps:

1. Select the **Start** button, type **Registry Editor**, open **Registry Editor** from the best match list.
2. Using the navigation pane, expand the key `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp`\*\*`
3. In the main pane, select `PortNumber`
4. From the menu bar, select **Edit &gt; Modify**, then select **Decimal**.
5. Type the new port number, and then select **OK**.
6. Close the Registry Editor, and restart your computer.

---

## Add the new port to the Windows Firewall

If you use the Windows Firewall, you need to add a new inbound rule to allow traffic on the new port. For more information about the different methods you can use to configure the Windows Firewall, see [Windows Firewall tools](/en-us/windows/security/operating-system-security/network-security/windows-firewall/tools).

Important

If you use any other firewall make sure you or your administrator permit connections to the new port number.

To create new Windows Firewall rules to allow the new port by running the following PowerShell command as an administrator. Be sure to replace `<Port Number>` with the new port number.

```powershell
$portValue = '<Port Number>'

New-NetFirewallRule -DisplayName 'RDPPORTLatest-TCP-In' -Profile Public -Direction Inbound -Action Allow -Protocol TCP -LocalPort $portValue
New-NetFirewallRule -DisplayName 'RDPPORTLatest-UDP-In' -Profile Public -Direction Inbound -Action Allow -Protocol UDP -LocalPort $portValue
```

## Test the new Remote Desktop listening port

The next time you connect to this computer by using the Remote Desktop Connection or other client, enter the hostname along with the new port. For example, if you changed the port to use 3390 on computer `pc1.contoso.com`, the address is `pc1.contoso.com:3390`.