---
layout: Conceptual
title: Install DHCP relay agent for Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/dhcp/dhcp-deploy-relay-agent
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to install a DHCP relay agent on a computer running the Windows Server operating system.
ms.topic: quickstart
author: robinharwood
ms.author: roharwoo
ms.custom: template-quickstart, team=cloud_advocates
ms.contributors: orthomas
ms.date: 2024-01-12T00:00:00.0000000Z
locale: en-us
document_id: 77ae4cbd-2a20-68e6-8c87-d0e3b6cf052a
document_version_independent_id: 77ae4cbd-2a20-68e6-8c87-d0e3b6cf052a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/dhcp/dhcp-deploy-relay-agent.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/dhcp/dhcp-deploy-relay-agent
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/dhcp/dhcp-deploy-relay-agent.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 694ba552-9196-58d9-532a-e806d2c093b9
---

# Install DHCP relay agent for Windows Server | Microsoft Learn

This article shows you how to install and configure a Dynamic Host Configuration Protocol (DHCP) Relay Agent on a computer running Windows Server. A DHCP relay agent works as an intermediary between DHCP clients and DHCP servers that aren't on the same subnet or local network. The DHCP Relay Agent forwards DHCP broadcast messages from clients to remote server, letting clients obtain IP addresses and other network configuration information from a DHCP server located on a different subnet.

To install the DHCP relay agent on Windows Server, you need to deploy the *Remote Access* server role. The DHCP relay agent is a feature of Remote Access and isn't included in the DHCP server role.

## Prerequisites

Before you can install your DHCP relay agent, you must have the following prerequisites:

- A computer running Windows Server in the remote subnet where you want to install the DHCP relay agent.
- A DHCP server with a DHCP scope configured for the remote subnet.

## Install and configure the server role

Here's how to install and configure LAN routing as part of the Remote Access server role from the Windows desktop.

1. Sign into the computer where you want to install the DHCP relay agent, then open the **Server Manager**.
2. In the Server Manager console, select **Add roles and features**.
3. In the **Add Roles and Features** menu, select **Next** until you reach the **Server Roles** page.
4. Expand the **Remote Access** role by selecting the accompanying checkbox or arrow.
5. In **Role Services**, select **Routing**, then **Add Features** when prompted.
6. Select **Next** until you reach the **Confirm installation selections** page.
7. Select **Install** to begin the installation. After the installation completes, select **Open the Getting Started Wizard**.
8. In the Routing and Remote Access Microsoft Management Console (MMC), right-click the server, then select *Configure and Enable Routing and Remote Access* to open the Routing and Remote Access Server Setup Wizard.
9. In the Welcome to the Routing and Remote Access Server Setup Wizard, select **Next**.
10. In **Configuration**, select *LAN routing*, and then select **Next**.
11. In **Custom Configuration**, select *VPN access*, and then select **Next** to open the Completing the Routing and Remote Access Server Setup Wizard.
12. Select **Finish** to close the wizard, then **Start service** when prompted.

## Configure DHCP Relay Agent

Here's how to install the DHCP Relay Agent role from the Routing and Remote Access MMC.

1. In the left pane, expand the server name, then right-click **General** under **IPv4** or **IPv6**, then select **New Routing Protocol**.
2. In the left pane, then right-click **DHCP Relay Agent** under **IPv4** or **IPv6**, then select **New Interface**.
3. Select the network interface you want to use for the DHCP relay agent. Select **OK**.
4. In the left pane, then right-click **DHCP Relay Agent** under **IPv4** or **IPv6**, then select **Properties**.
5. Enter the IP address of the DHCP server you want to relay DHCP requests to, then select **Add**.
6. Select **OK** to save your settings.

Now the DHCP Relay Agent is installed and configured on your Windows Server.