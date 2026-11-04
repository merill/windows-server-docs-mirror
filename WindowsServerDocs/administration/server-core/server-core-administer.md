---
layout: Conceptual
title: Administer Server Core installation | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/server-core/server-core-administer
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Learn how to administer a Server Core installation of Windows Server
ms.mktglfcycl: manage
ms.sitesec: library
author: robinharwood
ms.author: roharwoo
ms.date: 2025-02-24T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 9869bbf5-6ae0-2a14-4465-796a47c4e9cc
document_version_independent_id: 969ea4db-324d-7aa4-b8de-1d611e30c7f6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/server-core/server-core-administer.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/server-core/server-core-administer
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/server-core/server-core-administer.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 37735477-cb47-2602-cc16-1ff809d0597b
---

# Administer Server Core installation | Microsoft Learn

As Server Core doesn't have a UI, you need to use Windows PowerShell cmdlets, command line tools, or remote tools to perform basic administration tasks. The following sections outline the PowerShell cmdlets and commands used for basic tasks. You can also use [Windows Admin Center](../../manage/windows-admin-center/overview), a unified management portal currently in public preview, to administer your installation.

## Administrative tasks using PowerShell cmdlets

Use the following information to perform basic administrative tasks with Windows PowerShell cmdlets.

### Set a static IP address

When you install a Server Core server, it has a DHCP address by default. If you need a static IP address, you can set it using the following steps.

- To view your current network configuration, use `Get-NetIPConfiguration`.
- To view the IP addresses you're already using, use `Get-NetIPAddress`.

To set a static IP address, perform the following steps:

1. Run `Get-NetIPInterface`.
2. Note the number in the **IfIndex** column for your IP interface or the **InterfaceDescription** string. If you have more than one network adapter, note the number or string corresponding to the interface you want to set the static IP address for.
3. Run the following cmdlet to set the static IP address:

    ```powershell
    New-NetIPaddress -InterfaceIndex 12 -IPAddress 192.0.2.2 -PrefixLength 24 -DefaultGateway 192.0.2.1
    ```

    where:

    - `InterfaceIndex` is the value of **IfIndex** from step 2. (In this example, 12)
    - `IPAddress` is the static IP address you want to set. (In this example, 191.0.2.2)
    - `PrefixLength` is the prefix length which is another form of subnet mask for the IP address you're setting. (For this example, 24)
    - `DefaultGateway` is the IP address to the default gateway. (For this example, 192.0.2.1)
4. Run the following cmdlet to set the DNS client server address:

    ```powershell
    Set-DNSClientServerAddress –InterfaceIndex 12 -ServerAddresses 192.0.2.4
    ```

    where:

    - `InterfaceIndex` is the value of **IfIndex** from step 2.
    - `ServerAddresses` is the IP address of your DNS server.
5. To add multiple DNS servers, run the following command:

    ```powershell
    Set-DNSClientServerAddress –InterfaceIndex 12 -ServerAddresses 192.0.2.4,192.0.2.5
    ```

    where, in this example, `192.0.2.4` and `192.0.2.5` are both IP addresses of DNS servers.

### Set DHCP IP address

If you need to switch to DHCP, run the following command:

```powershell
Set-DnsClientServerAddress –InterfaceIndex 12 –ResetServerAddresses
```

### Join a domain

Use the following cmdlets to join a computer to a domain.

1. Run `Add-Computer`. You're prompted for both credentials to join the domain and the domain name.
2. If you need to add a domain user account to the local Administrators group, run the following command:

    ```
    net localgroup administrators /add <DomainName>\<UserName> & shutdown /r /t 0
    ```

### Rename the server

Use the following steps to rename the server.

1. Determine the current name of the server with the `hostname` or `ipconfig` command.
2. Run the following command:

    ```powershell
    Rename-Computer -NewName "NewName" -Force | Restart-Computer -Force
    ```

### Activate the server

Run `slmgr.vbs –ipk\productkey`. Then run `slmgr.vbs –ato`. Successful activation doesn't produce a notification upon completion.

Note

You can also activate the server by phone, using a [Key Management Service (KMS) server](../../get-started/server-2016-activation), or remotely. To activate remotely, run the following cmdlet from a remote computer:

```
cscript windows\system32\slmgr.vbs <ServerName> <UserName> <password>:-ato
```

### Configure Windows Firewall

You can configure Windows Firewall locally on the Server Core computer using Windows PowerShell cmdlets and scripts. See [NetSecurity](/en-us/powershell/module/netsecurity/) for the cmdlets you can use to configure Windows Firewall.

### Enable Windows PowerShell remoting

You can enable Windows PowerShell Remoting, in which commands typed in Windows PowerShell on one computer run on another computer. Enable Windows PowerShell Remoting with `Enable-PSRemoting`.

For more information, see [About Remote FAQ](/en-us/powershell/module/microsoft.powershell.core/about/about_remote_faq?view=powershell-5.1&amp;preserve-view=true).

## Administrative tasks from the command line

Use the following reference information to perform administrative tasks from the command line.

### Configuration and installation commands

| Task | Command |
| --- | --- |
| Set the local administrative password | `net user administrator *` |
| Join a computer to a domain | `netdom join %computername% /domain:<domain> /userd:<domain>\<username> /passwordd:<password>` Restart the computer. |
| Confirm that the domain has changed | `set` |
| Remove a computer from a domain | `netdom remove <computername>` |
| Add a user to the local Administrators group | `net localgroup Administrators /add <domain>\<username>` |
| Remove a user from the local Administrators group | `net localgroup Administrators /delete <domain>\<username>` |
| Add a user to the local computer | `net user <domain>\<username> * /add` |
| Add a group to the local computer | `net localgroup <group name> /add` |
| Change the name of a domain-joined computer | `netdom renamecomputer %computername% /NewName:<new computer name> /userd:<domain>\<username> /passwordd:<password>` |
| Confirm the new computer name | `set` |
| Change the name of a computer in a work group | `netdom renamecomputer <currentcomputername> /NewName:<newcomputername>`Restart the computer. |
| Disable paging file management | `wmic computersystem where name="<computername>" set AutomaticManagedPagefile=False` |
| Configure the paging file | `wmic pagefileset where name="<path/filename>" set InitialSize=<initialsize>,MaximumSize=<maxsize>`Where *&lt;path/filename&gt;* is the path to and name of the paging file, *`<initialsize>`* is the starting size of the paging file in bytes, and *maxsize* is the maximum size of the page file in bytes. |
| Change to a static IP address | Record the relevant information or redirect it to a text file: `ipconfig /all >ipconfig.txt`Verify that there's an interface list: `netsh interface ipv4 set address <Name ID from interface list> source=static address=<preferred IP address> gateway=<gateway address>`Run `ipconfig /all` to verify that DHCP enabled is set to **No**. |
| Set a static DNS address. | `netsh interface ipv4 add dnsserver name=<name or ID of the network interface card> address=<IP address of the primary DNS server> index=1``netsh interface ipv4 add dnsserver name=<name of secondary DNS server> address=<IP address of the secondary DNS server> index=2` Repeat as appropriate to add additional servers. Run `ipconfig /all` to verify that the addresses are correct. |
| Change to a DHCP-provided IP address from a static IP address | `netsh interface ipv4 set address name=<IP address of local system> source=DHCP`Run `ipconfig /all` to verify that DCHP enabled is set to **Yes**. |
| Enter a product key | `slmgr.vbs –ipk <product key>` |
| Activate the server locally | `slmgr.vbs -ato` |
| Activate the server remotely | `cscript slmgr.vbs –ipk <product key><server name><username><password>``cscript slmgr.vbs -ato <servername> <username> <password>`Get the GUID of the computer by running `cscript slmgr.vbs -did`, then run `cscript slmgr.vbs -dli <GUID>`Verify that License status is set to **Licensed (activated)**. |

### Networking and firewall commands

| Task | Command |
| --- | --- |
| Configure your server to use a proxy server | `netsh Winhttp set proxy <servername>:<port number>`Server Core installations can't access the Internet through a proxy that requires a password to allow connections. |
| Configure your server to bypass the proxy for Internet addresses | `netsh winhttp set proxy <servername>:<port number> bypass-list="<local>"` |
| Display or modify IPSEC configuration | `netsh ipsec` |
| Display or modify NAP configuration | `netsh nap` |
| Display or modify IP to physical address translation | `arp` |
| Display or configure the local routing table | `route` |
| View or configure DNS server settings | `nslookup` |
| Display protocol statistics and current TCP/IP network connections | `netstat` |
| Display protocol statistics and current TCP/IP connections using NetBIOS over TCP/IP (NBT) | `nbtstat` |
| Display hops for network connections | `pathping` |
| Trace hops for network connections | `tracert` |
| Display the configuration of the multicast router | `mrinfo` |
| Enable remote administration of the firewall | `netsh advfirewall firewall set rule group="Windows Defender Firewall Remote Management" new enable=yes` |

### System updates and error reporting commands

| Task | Command |
| --- | --- |
| Install an update | `wusa \<update\>.msu /quiet` |
| List installed updates | `systeminfo` |
| Remove an update | `expand /f: <update>.msu c:\test`Navigate to c:\test\ and open &lt;update&gt;.xml in a text editor. Replace **Install** with **Remove** and save the file. Then run `pkgmgr /n:<update>.xml` |
| Configure automatic updates | To verify the current setting: `cscript %systemroot%\system32\scregedit.wsf /AU /v`To enable automatic updates: `cscript scregedit.wsf /AU 4`To disable automatic updates: `cscript %systemroot%\system32\scregedit.wsf /AU 1` |
| Enable error reporting | To verify the current setting: `serverWerOptin /query`To automatically send detailed reports: `serverWerOptin /detailed`To automatically send summary reports: `serverWerOptin /summary`To disable error reporting: `serverWerOptin /disable` |
| Participate in the Customer Experience Improvement Program (CEIP) | To verify the current setting: `serverCEIPOptin /query`To enable CEIP: `serverCEIPOptin /enable`To disable CEIP: `serverCEIPOptin /disable` |

### Services, processes, and performance commands

| Task | Command |
| --- | --- |
| List the running services | `sc query` or `net start` |
| Start a service | `sc start <service name>` or `net start <service name>` |
| Stop a service | `sc stop <service name>` or `net stop <service name>` |
| Retrieve a list of running applications and associated processes | `tasklist` |
| Start Task Manager | `taskmgr` |
| Create and manage event trace session and performance logs | To create a counter, trace, configuration data collection, or API: `logman create`To query data collector properties: `logman query`To start or stop data collection: `logman start``logman stop`To delete a collector: `logman delete` To update the properties of a collector: `logman update`To import a data collector set from an XML file or export it to an XML file: `logman import``logman export` |

### Event log commands

| Task | Command |
| --- | --- |
| List event logs | `wevtutil el` |
| Query events in a specified log | `wevtutil qe /f:text <log name>` |
| Export an event log | `wevtutil epl <log name>` |
| Clear an event log | `wevtutil cl <log name>` |

### Hardware driver commands

| Task | Command |
| --- | --- |
| Add a driver for a new hardware device | Copy the driver to a folder at **%homedrive%&lt;driver folder&gt;**. Run `pnputil -i -a %homedrive%\<driver folder>\<driver\<.inf>` |
| Remove a driver for a hardware device | For a list of loaded drivers, run `sc query type= driver`. Then run `sc delete <service_name>` |