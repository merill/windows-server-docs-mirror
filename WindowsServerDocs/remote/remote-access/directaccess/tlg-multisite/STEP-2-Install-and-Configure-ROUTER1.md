---
layout: Conceptual
title: STEP 2 Install and Configure ROUTER1 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-multisite/step-2-install-and-configure-router1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to install and configure ROUTER1.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 8fdc9437-b7fd-78bb-6325-afe2330a114f
document_version_independent_id: 2e8231d2-e76c-2006-7313-d8843f2402a1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/STEP-2-Install-and-Configure-ROUTER1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-multisite/step-2-install-and-configure-router1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/STEP-2-Install-and-Configure-ROUTER1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1e86bfd1-0e17-5171-60d8-2369ba548230
---

# STEP 2 Install and Configure ROUTER1 | Microsoft Learn

In this multisite test lab guide, the router computer provides an IPv4 and IPv6 bridge between the Corpnet and 2-Corpnet subnets, and acts as a router for IP-HTTPS and Teredo traffic.

- Install the operating system on ROUTER1
- Configure TCP/IP properties and rename the computer
- Turn off the firewall
- Configure routing and forwarding

## Install the operating system on ROUTER1

First, install Windows Server 2016, Windows Server 2012 R2 or Windows Server 2012.

### To install the operating system on ROUTER1

1. Start the installation of Windows Server 2016, Windows Server 2012 R2 or Windows Server 2012 (full installation).
2. Follow the instructions to complete the installation, specifying a strong password for the local Administrator account. Log on using the local Administrator account.
3. Connect ROUTER1 to a network that has Internet access and run Windows Update to install the latest updates for Windows Server 2016, Windows Server 2012 R2 or Windows Server 2012 , and then disconnect from the Internet.
4. Connect ROUTER1 to the Corpnet and 2-Corpnet subnets.

## Configure TCP/IP properties and rename the computer

Configure TCP/IP settings on the router and rename the computer to ROUTER1.

### To configure TCP/IP properties and rename the computer

1. In the Server Manager console, click **Local Server**, and then in the **Properties** area, next to **Wired Ethernet Connection**, click the link.
2. In the **Network Connections** window, right-click the network adapter that is connected to Corpnet, click **Rename**, type **Corpnet**, and press ENTER.
3. Right-click **Corpnet**, and then click **Properties**.
4. Click **Internet Protocol Version 4 (TCP/IPv4)**, and then click **Properties**.
5. Click **Use the following IP address**. In **IP address**, type **10.0.0.254**. In **Subnet mask**, type **255.255.255.0**, and then click **OK**.
6. Click **Internet Protocol Version 6 (TCP/IPv6)**, and then click **Properties**.
7. Click **Use the following IPv6 address**. In **IPv6 address**, type **2001:db8:1::fe**. In **Subnet prefix length**, type **64**, and then click **OK**.
8. On the **Corpnet Properties** dialog box click **Close**.
9. In the **Network Connections** window, right-click the network adapter that is connected to 2-Corpnet, click **Rename**, type **2-Corpnet**, and press ENTER.
10. Right-click **2-Corpnet**, and then click **Properties**.
11. Click **Internet Protocol Version 4 (TCP/IPv4)**, and then click **Properties**.
12. Click **Use the following IP address**. In **IP address**, type **10.2.0.254**. In **Subnet mask**, type **255.255.255.0**, and then click **OK**.
13. Click **Internet Protocol Version 6 (TCP/IPv6)**, and then click **Properties**.
14. Click **Use the following IPv6 address**. In **IPv6 address**, type **2001:db8:2::fe**. In **Subnet prefix length**, type **64**, and then click **OK**.
15. On the **2-Corpnet Properties** dialog box click **Close**.
16. Close the **Network Connections** window.
17. In the Server Manager console, in **Local Server**, in the **Properties** area, next to **Computer name**, click the link.
18. On the **System Properties** dialog box, on the **Computer Name** tab, click **Change**.
19. On the **Computer Name/Domain Changes** dialog box, in **Computer name**, type **ROUTER1**, and then click **OK**.
20. When you are prompted that you must restart the computer, click **OK**.
21. On the **System Properties** dialog box, click **Close**.
22. When you are prompted to restart the computer, click **Restart Now**.
23. After the computer has restarted, log on with the local Administrator account.

## Turn off the firewall

This computer is configured only to provide routing between the Corpnet and 2-Corpnet subnets; therefore, the firewall must be turned off.

### To turn off the firewall

1. On the **Start** screen, type**wf.msc**, and then press ENTER.
2. In Windows Firewall with Advanced Security, in the **Actions** pane, click **Properties**.
3. On the **Windows Firewall with Advanced Security** dialog box, on the **Domain Profile** tab, in **Firewall state**, click **Off**.
4. On the **Windows Firewall with Advanced Security** dialog box, on the **Private Profile** tab, in **Firewall state**, click **Off**.
5. On the **Windows Firewall with Advanced Security** dialog box, on the **Public Profile** tab, in **Firewall state**, click **Off**, and then click **OK**.
6. Close Windows Firewall with Advanced Security.

## Configure routing and forwarding

To provide routing and forwarding services between the Corpnet and 2-Corpnet subnets, you must enable forwarding on the network interfaces and configure static routes between the subnets.

### To configure static routes

1. On the **Start** screen, type**cmd.exe**, and then press ENTER.
2. Enable forwarding on both the IPv4 and IPv6 interfaces of both network adapters using the following commands. After entering each command, press ENTER.

    ```
    netsh interface IPv4 set interface Corpnet forwarding=enabled
    netsh interface IPv4 set interface 2-Corpnet forwarding=enabled
    netsh interface IPv6 set interface Corpnet forwarding=enabled
    netsh interface IPv6 set interface 2-Corpnet forwarding=enabled
    ```
3. Enable IP-HTTPS routing between the Corpnet and 2-Corpnet subnets.

    ```
    netsh interface IPv6 add route 2001:db8:1:1000::/59 Corpnet 2001:db8:1::2
    netsh interface IPv6 add route 2001:db8:2:2000::/59 2-Corpnet 2001:db8:2::20
    ```
4. Enable Teredo routing between the Corpnet and 2-Corpnet subnets.

    ```
    netsh interface IPv6 add route 2001:0:836b:2::/64 Corpnet 2001:db8:1::2
    netsh interface IPv6 add route 2001:0:836b:14::/64 2-Corpnet 2001:db8:2::20
    ```
5. Close the Command Prompt window.