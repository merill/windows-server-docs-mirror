---
layout: Conceptual
title: Disable Automatic Reconnection in Remote Desktop Service for Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/automatic-reconnection-lock-screen
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn about the Remote Desktop Services Automatic Reconnection feature, lock screen security, and how to disable Automatic Reconnection.
author: robinharwood
ms.author: roharwoo
ms.reviewer: spatnaik
ms.topic: how-to
ms.date: 2024-07-03T00:00:00.0000000Z
locale: en-us
document_id: 363444be-6d96-f0d2-6ea0-899d081b2d8f
document_version_independent_id: 363444be-6d96-f0d2-6ea0-899d081b2d8f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/automatic-reconnection-lock-screen.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/automatic-reconnection-lock-screen
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/automatic-reconnection-lock-screen.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: fc51426c-b85b-2e5f-911b-5a3e910b83e3
---

# Disable Automatic Reconnection in Remote Desktop Service for Windows Server | Microsoft Learn

Learn about Automatic Reconnection in Remote Desktop Service (RDS), lock screen security, and how to disable Automatic Reconnection for RDS session hosts and clients using Server Manager, Group Policy, and Remote Desktop Protocol (RDP) properties.

## Automatic Reconnection

Microsoft Remote Desktop offers a wide range of features designed to enhance your remote working experience, such as Automatic Reconnection. Automatic Reconnection allows the client to seamlessly reconnect to their existing sessions, giving a smooth, uninterrupted user experience when temporary network disruptions occur. To learn more about the automatic reconnection behavior, see the [Automatic Reconnection](/en-us/openspecs/windows_protocols/ms-rdpbcgr/e729948a-3f4e-4568-9aef-d355e30b5389) open specification. Automation Reconnection is available to Remote Desktop when connecting to a local PC or Remote Desktop Services (RDS).

Important

Automatic Reconnection is enabled by default, and therefore, requires explicit action from the administrators to disable it.

## Lock Screen Security

When a policy or the user locks the remote session and the network connection is lost or disrupted, RDS retains the session state and connection information. If the automatic reconnection of locked sessions raises concerns for your specific use case, we recommend implementing extra security measures. Because RDS retains the session state and connection information, the client reconnects without needing to reauthenticate. The lock screen of the Remote Desktop session isn't designed to function as a security boundary. Security measures can include disabling Automatic Reconnection on either the RDS session host or the client. This article describes how to disabled Automatic Reconnection.

## Prerequisites

Before you can configure Automatic Reconnection for Remote Desktop, you need to complete the following prerequisites:

- A Windows client or Windows Server machine to connect from and to.
- An account that is a member of RDS session host administrators group, or equivalent.
- If your machine is a domain member, you also need a domain account that is a member of the [Group Policy Creator Owners](../../identity/ad-ds/manage/understand-security-groups#group-policy-creator-owners) group, or equivalent.

If you're using RDS, you also need:

- A Windows Server with the RDS installed and configured. To learn more about deploying RDS, see [Deploy your Remote Desktop environment](rds-deploy-infrastructure).
- A Remote Desktop Session Collection. To learn more about creating a Remote Desktop Session Collection, see [Create a Remote Desktop Services collection for desktops and apps to run](rds-create-collection).

## Methods to disable Automatic Reconnection

To disable Automatic Reconnection, you can configure your server, client, or both.

Tip

- If you disable Automatic Reconnection from your server, clients will be unable to perform Automatic Reconnection regardless of the client configuration.
- Changes to the Automatic Reconnection setting only apply to new sessions. Existing sessions will continue to use the Automatic Reconnection setting from the time of connection.

### Client RDP Properties

You can configure the following Remote Desktop Protocol (RDP) property to disable Automatic Reconnection using the Remote Desktop Connection app or by editing the `.rdp` file. More information can be found here: [Supported RDP properties with Remote Desktop Services](clients/rdp-files#supported-rdp-properties-with-remote-desktop-services). To disabled Automatic Reconnection, select the relevant method and follow the steps.

# [RDP file](#tab/rdpfile)
Here's how to disable Automatic Reconnection by editing the `.rdp` file.

1. Locate your `.rdp` file, right-click the file, expand the **Open with** menu, then select **Choose another app**.
2. Select **Notepad**, then select **Just once**
3. Scroll to the last line of the file, then enter the following text.

    ```RDP
    autoreconnection enabled:i:0
    ```

# [Remote Desktop Connection app](#tab/mstsc)
Here's how to disable Automatic Reconnection using the Remote Desktop Connection app (`mstsc.exe`).

1. Open the **Remote Desktop Connection** app and enter your connection information.
2. Go to **Show Options**, then select the **Experience** tab.
3. Clear the **Reconnect if the connection is dropped** checkbox.

---

### Remote Desktop Services server configuration

To disable Automatic Reconnection for your RDS session host, select the relevant method and follow the steps.

Tip

If you have an RDS deployment and want to configure Automatic Reconnection using the Session Collection properties, Group Policy must be in the **Not Configured** state for each session host. The Group Policy setting applied to each session host takes priority over the Automatic Reconnection setting for the Remote Desktop Session Collection.

# [Group Policy](#tab/gpo)
Here's how to disable Automatic Reconnection for RDS session hosts using Group Policy.

1. Open the **Group Policy Management Console**, create or edit a policy applied to your server.
2. In the console tree, select **Computer Configuration &gt; Administrative Templates &gt; Windows Components &gt; Remote Desktop Service &gt; Remote Desktop Session Host &gt; Connections**.
3. For the setting, right-click **Automatic reconnection** and select **Edit**.
4. Select **Disable**, from the radio buttons.
5. Select **OK** to complete the configuration.

# [Server Manager](#tab/servermanager)
Here's how to disable Automatic Reconnect using Server Manager from the Windows desktop.

1. From the Windows desktop, open the **Start** menu, enter the *Server Manager* and select the matching service entry.
2. From Server Manager, in the panel on left, select **Remote Desktop Services**, then select your collection.
3. In the *Properties* section, select **TASKS**, then select **Edit Properties** from the drop-down menu.
4. Select the Session Collection, select **Session**.
5. From the *Configure Session Properties* page, uncheck the **Enable automatic reconnection** box, then select **OK**.

# [PowerShell](#tab/powershell)
Here's how to disable Automatic reconnection using the [Set-RDSessionCollectionConfiguration](/en-us/powershell/module/remotedesktop/Set-RDSessionCollectionConfiguration) PowerShell command.

To disable Automatic Reconnection for the Remote Desktop Session Collection named `Desktops`, run the following command on a computer with the Remote Desktop Services server role installed:

```powershell
Set-RDSessionCollectionConfiguration -CollectionName "Desktops" -AutomaticReconnectionEnabled $false
```

---