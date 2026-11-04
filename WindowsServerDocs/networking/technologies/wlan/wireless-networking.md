---
layout: Conceptual
title: Wireless LAN overview in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/wlan/wireless-networking
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: The WLAN service allows for wireless configuration, discovery, and connectivity using a wireless adapter in Windows devices.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2024-10-25T00:00:00.0000000Z
locale: en-us
document_id: b9554999-7339-a25c-4f13-925cf6855a68
document_version_independent_id: b9554999-7339-a25c-4f13-925cf6855a68
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/wlan/wireless-networking.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/wlan/wireless-networking
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/wlan/wireless-networking.md
2PlusCloud:
- Power
- Azure
- M365
__autotagging_hash:
- ED2EAF6FD4D5F2EC331B01CD0E2F3A9596A415C5E7300EB633F6FEC0260A78FD
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: fc4fee55-fb27-7ac5-224f-41df2de8459d
---

# Wireless LAN overview in Windows Server | Microsoft Learn

The Wireless LAN (WLAN) service is a feature in Windows Server that allows you to configure, discover, and connect to wireless networks. Once enabled, the WLAN AutoConfig service dynamically scans and selects which wireless network your device can automatically connect to using a wireless network adapter. The AutoConfig service automatically connects to a more preferred wireless network when one becomes available.

WLAN also offers various security measures to safeguard data transmission over wireless networks using authentication and encryption protocols. To learn more, see [Extensible Authentication Protocol (EAP) for network access](../extensible-authentication-protocol/network-access).

## Prerequisites

- A Windows Server 2012 operating system or later.
- Drivers for supported wireless adapters.

### Install WLAN for Windows Server

The WLAN feature isn't installed in Windows Server by default. To install the WLAN and related service, follow these steps:

1. Open **Server Manager**, select **Add Roles and Features**, select **Next**, then select **Next** again.
2. In the **Select server roles** page, select **Next**, select **Wireless LAN Service**, then select **Next**.
3. In the **Confirm installations selections** page, select **Install**, then select **Close**.
4. Restart your device for these changes to apply.

Alternatively, the WLAN feature can also be installed in PowerShell by running:

```powershell
Install-WindowsFeature -Name Wireless-Networking
```

Note

In Windows Server 2025, the WLAN feature is installed by default and you're required to enable this service to utilize wireless capabilities.

### Enable WLAN service

After your device is restarted, the **wlansvc** service needs to be enabled in the **Services** app by following these steps:

1. Select **Start** &gt; type **services.msc** &gt; select **Services**.
2. In the right pane, scroll to the bottom until you see **WLAN AutoConfig**.
3. Right-click on **WLAN AutoConfig** and select **Start**.

Alternatively, the WLAN service can be started using the Command Prompt or PowerShell by running:

```cmd
net start wlansvc
```

```powershell
Start-Service -Name wlansvc
```

### Install WLAN for Windows client

This service is already installed and enabled by default in Windows client devices.