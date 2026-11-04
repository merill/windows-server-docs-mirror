---
layout: Conceptual
title: Install and Configure DNS Server on Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/dns/quickstart-install-configure-dns-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to install and configure a DNS server on Windows Server using PowerShell or Server Manager. Manage DNS zones and queries effectively.
author: robinharwood
ms.author: roharwoo
ms.topic: quickstart
ms.date: 2025-06-11T00:00:00.0000000Z
ms.custom: template-quickstart, team=cloud_advocates
ms.contributors: orthomas
locale: en-us
document_id: e30dce2f-cf7f-44ae-3503-fce3e97e5be7
document_version_independent_id: e30dce2f-cf7f-44ae-3503-fce3e97e5be7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/dns/quickstart-install-configure-dns-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/dns/quickstart-install-configure-dns-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/dns/quickstart-install-configure-dns-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 175f595b-c012-05a6-cad5-1a3c0edd704c
---

# Install and Configure DNS Server on Windows Server | Microsoft Learn

Domain Name System (DNS) is essential for translating domain names into IP addresses, enabling network connectivity and resource access. This quickstart guides you through installing and configuring the DNS Server role on Windows Server. Learn how to set up DNS zones, manage queries, and configure server options using PowerShell or Server Manager. You can also find information on how to forward DNS queries to DNS root hint name servers, or optionally to an upstream name server.

## Prerequisites

Before you can install and configure your DNS server, your computer must meet the following prerequisites:

- A computer running a supported version of Windows Server.
- A static IP.
- An account that is a member of the Administrators group, or equivalent.

## Install DNS Server

Installing a Domain Name System (DNS) server involves adding the DNS Server role to an existing Windows Server server.

Tip

When you install Active Directory Domain Services (AD DS) with the Active Directory Domain Services Installation Wizard, the wizard gives you the option to automatically install and configure a DNS server. The resulting DNS zone is integrated with the AD DS domain namespace. To learn more, see [Understanding Active Directory Domain Services Integration](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc726034%28v=ws.11%29).

To install the DNS Server role as a standalone server, perform the following steps:

# [PowerShell](#tab/powershell)
Here's how to install the DNS Server role using the [Install-WindowsFeature](/en-us/powershell/module/servermanager/install-windowsfeature) command.

1. Run PowerShell on your computer in an elevated session.
2. To install the DNS role, run the following command. The installation doesn't require a reboot.

    ```powershell
    Install-WindowsFeature -Name DNS
    ```

# [GUI](#tab/gui)
Here's how to install the DNS Server role using Server Manager from the Windows desktop.

1. From the Windows desktop, open the **Start** menu, then select the **Server Manager** tile.
2. On the menu, go to **Manage**, and then select **Add Roles and Features**.
3. On the **Before you begin** page, select **Next** to begin.
4. On the **Select installation type** page, select the **Role-based or feature-based installation** option, and select **Next**.
5. On the **Select destination server** page, leave the default options. Select **Next**.
6. On the **Select server roles** page, select the **DNS Server** checkbox, and then select on the **Next** button.

    1. You're prompted to add features that are required for DNS Server, if you're happy with the defaults, select **Add Features**.
7. On the **Select features** page, you can leave the default selections, and then select on the **Next** button.
8. On the **DNS Server** page, review the role description and things to note, select **Next** to continue.
9. On the **Confirm installation selections** page, review the selected roles and features, and then select on the **Install** button to begin the installation process.
10. Once the installation is complete, select **Close**. The installation doesn't require a reboot.

---

## Configure DNS Server

Now you can continue to configure the server.

### Configure interfaces

By default, a DNS server listens for requests on all IP address interfaces. You can configure DNS server to listen on a specify interface using the GUI or by using PowerShell.

# [PowerShell](#tab/powershell)
Here's how to configure the interface used to listen for DNS requests using the [Set-DNSServerSetting](/en-us/powershell/module/dnsserver/set-dnsserversetting) command.

1. Run PowerShell on your computer in an elevated session.
2. Find your computers existing IP address by running the [Get-NetIPAddress](/en-us/powershell/module/nettcpip/get-netipaddress) cmdlet. Make a note of the IP address that you want to use for your DNS server.

    ```powershell
    Get-NetIPAddress | fl IPAddress,InterfaceAlias
    ```
3. Store the current DNS server setting in a temporary variable, set the **ListeningIpAddress** property, and apply the new settings by running the following commands. Replace the placeholder `<ip_address>` with the IP you made a note of earlier.

    ```powershell
    $DnsServerSettings = Get-DnsServerSetting -ALL
    $DnsServerSettings.ListeningIpAddress = @("<ip_address>")
    Set-DNSServerSetting $DnsServerSettings
    ```

# [GUI](#tab/gui)
Here's how to configure the interface used to listen for DNS requests using the DNS Manager console.

1. From the Windows desktop, open the **Start** menu. Select **Windows Administrative Tools &gt; DNS**.
2. Select and hold (or right-click) your server, and then select **Properties**.
3. To limit the DNS server to use a specific IP address, select **Only the following IP address**, select the IP address you wish to use, and then select **OK**.

---

### Configure root hints

Root hints servers are used to help resolving DNS address information when the DNS server is unable to resolve the query locally from a hosted zone or the DNS server cache. Root hints name servers are populated by default in new installations.

You can edit the list of root name servers if required by navigating to the **Root Hints** tab of the DNS server properties dialog box or by using PowerShell.

Removing all root hints servers isn't supported. Instead, configure your DNS server to not use root hint name server by selecting the **Disable recursion** server option in the DNS Manager console **Advanced** tab. Disabling recursion also disables any configured forwarders. Alternatively, clear **Use root hints if no forwarders are available** in the **Forwarders** tab.

# [PowerShell](#tab/powershell)
Here's how to update a DNS root hint name server using the [Set-DnsServerRootHint](/en-us/powershell/module/dnsserver/set-dnsserverroothint) command.

1. Run PowerShell on your computer in an elevated session.
2. Find your computer's existing IP address by running the [Get-DnsServerRootHint](/en-us/powershell/module/dnsserver/get-dnsserverroothint) cmdlet. Make a note of the name server that you want to update.

    ```powershell
    Get-DnsServerRootHint
    ```
3. Store the current DNS server setting in a variable by running the following commands. Replace the placeholder `<root_hint_name_server>` with the root hint name server you noted earlier.

    ```powershell
    $RootHintServer = (Get-DnsServerRootHint | Where-Object {$_.NameServer.RecordData.NameServer -match "<root_hint_name_server>"} )
    ```
4. Set the **Ipv4address** property in the temporary variable by running the following commands. Replace the placeholder `<ip_address>` with the updated IP address.

    ```powershell
    $RootHintServer.IPAddress[0].RecordData.Ipv4address = "<ip_address>"
    ```
5. Apply the updated record by running the following commands.

    ```powershell
    Set-DnsServerRootHint $RootHintServer
    ```
6. To check the updated root hints, run the following command. Notice that the name server has a trailing dot (.).

    ```powershell
    Get-DnsServerRootHint
    ```

# [GUI](#tab/gui)
Here's how to root hints using the DNS Manager console.

1. From the Windows desktop, open the **Start** menu. Select **Windows Administrative Tools &gt; DNS**.
2. Select and hold (or right-click) your server, and then select **Properties**.
3. Select the **Root Hints** tab, select the item to edit, and then select **Edit**.
4. Enter the fully qualified domain name, then select **Resolve**. Verify the IP address. If necessary, edit the IP address.
5. Select **OK**.
6. Review the updated root hint server in the list. When you're ready, select **OK**. Notice that the name server has a trailing dot (.).

---

### Configure forwarders

You can optionally configure a forwarder to resolve DNS address information rather than forwarding traffic to the DNS root servers. You can add forwarders using the GUI or by using the `Set-DNSServerForwarder` PowerShell cmdlet.

Note

DNS root hints aren't used unless your forwarders fail to respond.

# [PowerShell](#tab/powershell)
Here's how to install the DNS server role using the [Install-WindowsFeature](/en-us/powershell/module/servermanager/install-windowsfeature) command.

1. Run PowerShell on your computer in an elevated session.
2. To configure DNS forwarders, replace the placeholders `<ip_forwarder_1>` and `<ip_forwarder_2>` with the IP address of the DNS server to be used as your forwarders. Then, run the following commands.

    ```powershell
    $Forwarders = "<ip_forwarder_1>","<ip_forwarder_2>"
    Set-DnsServerForwarder -IPAddress $Forwarders
    ```

# [GUI](#tab/gui)
Here's how to configure DNS forwarders using the DNS Manager console.

1. From the Windows desktop, open the **Start** menu. Select **Windows Administrative Tools &gt; DNS**.
2. Select and hold (or right-click) your server, and then select **Properties**.
3. Select the **Forwarders** tab, then select **Edit**.
4. Enter the IP address of the DNS server for forwarding requests to. Repeat this step as many times as you need.
5. Select **OK**.
6. Review the DNS server in the list, select **OK** or **Apply** to complete your configuration.

---

## Remove the DNS Server role

To remove the DNS Server role, perform the following steps.

# [PowerShell](#tab/powershell)
Here's how to uninstall the DNS Server role using the [Uninstall-WindowsFeature](/en-us/powershell/module/servermanager/uninstall-windowsfeature) command.

1. In an elevated PowerShell prompt, run the following command:

    ```powershell
    Uninstall-WindowsFeature -Name DNS
    ```

# [GUI](#tab/gui)
Here's how to uninstall the DNS server role using Server Manager from the Windows desktop.

1. From the Windows desktop, open the **Start** menu, then select the **Server Manager** tile.
2. On the menu, go to **Manage**, and then select **Remove Roles and Features**.
3. On the **Before you begin** page, Select **Next** to begin.
4. On the **Select destination server** page, select the server that you want to remove the DNS server role service from, then select **Next**.
5. From the list, clear the **DNS Server**checkbox.
    1. You're prompted to remove features that require DNS Server, select **Remove Features**, then **Next** to continue.
6. On the **Remove features** page, you can leave the default selections, and then select the **Next** button.
7. On the **Confirm removal selections** page, review the selected roles and features, and then select **Remove**.
8. Once the role and feature is removed, select **Close**.
9. Restart your computer completing the uninstall.

---

Important

When removing the DNS server role service from a Windows Server computer, be aware of the following points:

- For a DNS server that hosts AD DS-integrated zones, these zones are saved or deleted according to their storage type. The zone data isn't deleted unless the DNS server that you uninstall is the last DNS server hosting that zone.
- For a DNS server that hosts standard DNS zones, the zone files remain in the *%systemroot%\System32\Dns* directory, but they aren't reloaded if the DNS server is reinstalled. If you create a new zone with the same name as an old zone, the old zone file is replaced with the new zone file.