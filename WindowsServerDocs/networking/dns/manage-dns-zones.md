---
layout: Conceptual
title: Manage DNS zones using DNS server in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/dns/manage-dns-zones
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to create DNS zones and manage them with DNS server in Windows Server using PowerShell and the DNS Manager console.
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2025-01-02T00:00:00.0000000Z
ms.custom: template-how-to, team=cloud_advocates
ms.contributors: orthomas
locale: en-us
document_id: bbc421e8-79d1-5dd5-5421-aae0c45e468b
document_version_independent_id: bbc421e8-79d1-5dd5-5421-aae0c45e468b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/dns/manage-dns-zones.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/dns/manage-dns-zones
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/dns/manage-dns-zones.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 20d5edb4-94d6-7d40-30b4-17f8c48b0eb3
---

# Manage DNS zones using DNS server in Windows Server | Microsoft Learn

Create primary, secondary, stub, and reverse DNS zones using the DNS server role in Windows Server. This article also shows you how to configure zone transfer settings and perform zone delegation.

## Prerequisites

Before you can manage DNS zone in Windows Server, you need to complete the following prerequisites:

- A Windows Server with the DNS Server role installed and configured. See [Quickstart: Installing and configure DNS Server](quickstart-install-configure-dns-server) to found out how to get started.
- Determine the type of zone you want to create, see [DNS zones](zone-types) to learn more.
- An account that is a member of the Administrators group, or equivalent.
- You need the fully qualified domain name (FQDN) of the zone you want to create.
- If you want to create a secondary or stub zone, you need the IP address of the DNS server(s) hosting the primary zone.

You can remotely manage a Windows Server DNS server using all of the methods outlined in this article.

### Create a primary zone

#### Create an Active Directory integrated primary zone

To create an Active Directory integrated primary zone, select the relevant method and follow the steps.

# [PowerShell](#tab/powershell)
Here's how to create an Active Directory Integrated DNS zone using the [Add-DnsServerPrimaryZone](/en-us/powershell/module/dnsserver/add-dnsserverprimaryzone) PowerShell command.

Create a new primary zone for `north.contoso.com` and set the replication scope, run the following command:

```powershell
Add-DnsServerPrimaryZone -Name "north.contoso.com" -ReplicationScope "Forest" -PassThru
```

# [GUI](#tab/gui)
Here's how to create a forward look up zone using DNS Manager.

1. From the Windows desktop, open the **Start** menu, select **Windows Administrative Tools &gt; DNS**.
2. In the console tree, connect to the DNS server you wish to manage, expand the DNS server, right-click, then select **New Zone**.
3. On the New Zone Wizard page, select **Next**.
4. On the Zone Type page, select **Primary zone** and ensure **Store the zone in Active Directory** is checked. This option is available when the DNS server is also an AD DS domain controller.
5. On the Active Directory Zone Replication Scope page, choose one of the following options:

    - All DNS servers running on AD DS domain controllers in the forest.
    - All DNS servers running on AD DS domain in the domain.
    - All domain controllers in this domain (for Windows 2000 compatibility).
    - All domain controllers enrolled in a specific directory partition.
6. On the Forward or Reverse Lookup Zone page, select **Forward lookup zone**.
7. On the zone name page, specify the name of the DNS zone. For example, `north.contoso.com`
8. On the Dynamic Update page, choose one of the following options:

    - Allow only secure dynamic updates (recommended for Active Directory).
    - Allow both nonsecure and secure dynamic updates.
    - Do not allow dynamic updates.
9. Select **Finish** to complete the New Zone Wizard.

---

#### Create a file based primary zone

To create a file based primary zone, select the relevant method and follow the steps.

# [PowerShell](#tab/powershell)
Here's how to create a file based DNS zone using the [Add-DnsServerPrimaryZone](/en-us/powershell/module/dnsserver/add-dnsserverprimaryzone) PowerShell command.

To add the file based DNS zone `east.contoso.com` using the file `east.contoso.com.dns`, run the following command on a computer with the DNS server role installed:

```powershell
Add-DnsServerPrimaryZone -Name "east.contoso.com" -ZoneFile "east.contoso.com.dns"
```

# [GUI](#tab/gui)
Here's how to create a file base forward lookup zone using DNS Manager.

1. From the Windows desktop, open the **Start** menu, select **Windows Administrative Tools &gt; DNS**.
2. In the console tree, expand a DNS server then right-click, then select **New Zone**.
3. On the New Zone Wizard page, select **Next**.
4. On the Zone Type page, select **Primary zone** and ensure **Store the zone in Active Directory***isn't* checked. This option is only available of the DNS server is also an AD DS domain controller.
5. On the Forward or Reverse Lookup Zone page, select **Forward lookup zone**.
6. On the zone name page, specify the name of the DNS zone. For example, `east.contoso.com`.
7. On the Zone File page, you're provided with the option to specify a new file name, with the default being the zone name with the `.dns` extension. For example, `east.contoso.com.dns`. You can also use an existing zone file that has been copied to the `%SystemRoot%\system32\dns` folder on the DNS server.
8. On the Dynamic Update page, choose one of the following options:

    - Allow both nonsecure and secure dynamic updates.
    - Do not allow dynamic updates.
9. Select **Finish** to complete the New Zone Wizard.

---

### Create a secondary zone

To create a secondary zone, select the relevant method and follow the steps.

# [PowerShell](#tab/powershell)
Here's how to create a secondary DNS zone using the [Add-DnsServerSecondaryZone](/en-us/powershell/module/dnsserver/add-dnsserversecondaryzone) PowerShell command.

Add the secondary zone western.contoso.com using the zone file name `south.contoso.dns` and using the primary zone server at IP address `172.23.90.124` use the following command:

```powershell
Add-DnsServerSecondaryZone -Name "south.contoso.com" -ZoneFile "south.contoso.com.dns" -MasterServers 172.23.90.124
```

# [GUI](#tab/gui)
Here's how to create a secondary look up zone using DNS Manager.

1. From the Windows desktop, open the **Start** menu, select **Windows Administrative Tools &gt; DNS**.
2. In the console tree, expand a DNS server then right-click, then select **New Zone**.
3. On the New Zone Wizard page, select **Next**.
4. On the Zone Type page, select **Secondary zone**.
5. On the Zone Name page, specify the name of the secondary zone. The name of the zone must match the name of the primary zone to replicate from. For example, `south.contoso.com`.
6. On the Master DNS Servers page, specify the IP addresses of one or more DNS servers that host copies of the primary zone. You need to ensure that the primary zone allows transfers to the DNS server hosting the secondary zone. For example, `172.23.90.124`.
7. Select **Finish** on the Completing the New Zone Wizard.

---

### Create a stub zone

To create a stub zone, select the relevant method and follow the steps.

# [PowerShell](#tab/powershell)
Here's how to create a secondary DNS zone using the [Add-DnsServerStubZone](/en-us/powershell/module/dnsserver/add-dnsserverstubzone) PowerShell command.

To add a stub zone for the `west.contoso.com` zone using the authoritative DNS server `172.23.90.124`, run the following command:

```powershell
Add-DnsServerStubZone -Name "west.contoso.com" -MasterServers "172.23.90.124" -PassThru -ZoneFile "west.contoso.com.dns"
```

# [GUI](#tab/gui)
Here's how to create a stub zone up zone using DNS Manager.

1. From the Windows desktop, open the **Start** menu, select **Windows Administrative Tools &gt; DNS**.
2. In the console tree, expand a DNS server then right-click, then select **New Zone**.
3. On the New Zone Wizard page, select **Next**.
4. On the Zone Type page, select **Stub zone**. If the DNS server is also an AD DS domain controller, you can store the zone information in Active Directory.
5. If you have chosen to store the zone data in AD DS, choose one of the following options:

    - All DNS servers running on AD DS domain controllers in the forest.
    - All DNS servers running on AD DS domain in the domain.
    - All domain controllers in this domain (for Windows 2000 compatibility).
    - All domain controllers enrolled in a specific directory partition.
6. Specify the zone name. For example, `west.contoso.com`
7. On the Master DNS Servers page, provide the IP address of a DNS server that is authoritative for the target zone. For example, `172.23.90.124`.
8. Select **Finish** on the Completing the New Zone Wizard.

---

### Create a reverse lookup zone

To create a reverse lookup zone, select the relevant method and follow the steps.

# [PowerShell](#tab/powershell)
Here's how to create an Active Directory Integrated reverse DNS zone using the [Add-DnsServerPrimaryZone](/en-us/powershell/module/dnsserver/add-dnsserverprimaryzone) PowerShell command.

To add the reverse lookup zone for the `10.1.0.0/24` IPv4 address range and set the replication scope, run the following command.

```powershell
Add-DnsServerPrimaryZone -NetworkID "10.1.0.0/24" -ReplicationScope "Forest"
```

# [GUI](#tab/gui)
Here's how to create a reverse look up zone using DNS Manager.

1. From the Windows desktop, open the **Start** menu, select **Windows Administrative Tools &gt; DNS**.
2. In the console tree, expand a DNS server then right-click, then select **New Zone**.
3. On the New Zone Wizard page, select **Next**.
4. On the Zone Type page, select **Primary zone** and ensure Store the zone in Active Directory is selected. This option is available if the DNS server is also an AD DS domain controller.
5. On the Active Directory Zone Replication Scope page, choose one of the following options:

    - All DNS servers running on AD DS domain controllers in the forest.
    - All DNS servers running on AD DS domain in the domain.
    - All domain controllers in this domain (for Windows 2000 compatibility).
    - All domain controllers enrolled in a specific directory partition.
6. On the Forward or Reverse Lookup Zone page, select **Reverse lookup zone**.
7. On the Reverse Lookup Zone Name page, choose either of the following options:

    - IPv4 Reverse Lookup Zone.
    - IPv6 Reverse Lookup Zone.
8. On the Network ID page, enter the network ID in the normal (not the reversed) order. For example, for the IPv4 network `192.168.220.0/24` enter the network ID as `192.168.220`. The `in-addr.arpa` zone name is automatically appended.
9. On the Dynamic Update page, choose one of the following options:

    - Allow only secure dynamic updates (recommended for Active Directory).
    - Allow both nonsecure and secure dynamic updates.
    - Do not allow dynamic updates.
10. Select **Finish** to complete the New Zone Wizard.

---

## Configure zone transfer settings

To configure the zone transfer settings for a primary DNS zone, select the relevant method and follow the steps.

# [PowerShell](#tab/powershell)
Here's how to set the zone transfer settings for an existing DNS zone using the [Set-DnsServerPrimaryZone](/en-us/powershell/module/dnsserver/add-dnsserverprimaryzone) PowerShell command.

To configure zone transfers to only be allowed to servers in the name servers (NS) records for `west.contoso.com` DNS zone, run the following command.

```powershell
Set-DnsServerPrimaryZone -name "west.contoso.com" -SecureSecondaries "TransferToZoneNameServer" -PassThru
```

# [GUI](#tab/gui)
Using DNS Manager you can control whether a zone can be transferred to other servers and which servers can receive the zone transfer.

1. From the Windows desktop, open the **Start** menu, select **Windows Administrative Tools &gt; DNS**.
2. In the console tree, expand a DNS server and a DNS zone, right-click, then select **Properties**.
3. On the Zone Transfers tab, select one of the following options:

    - To disable zone transfers, clear the **Allow zone transfers** check box.
    - To allow zone transfers, check the **Allow zone transfers** check box.
4. If you allowed zone transfers, select one of the following options:

    - To allow zone transfers to any server, select **To any server**.
    - To allow zone transfers only to the DNS servers that are listed on the Name Servers tab, select **Only to servers listed on the Name Servers tab**.
    - To allow zone transfers only to specific DNS servers, select **Only to the following servers**, and then add the IP address of one or more DNS servers.

---

## Perform zone delegation

To perform zone delegation for a subdomain, select the relevant method and follow the steps.

# [PowerShell](#tab/powershell)
Here's how to delegate the `south.west.contoso.com` subdomain using the [Add-DnsServerZoneDelegation](/en-us/powershell/module/dnsserver/add-dnsserverzonedelegation) PowerShell command.

To delegate the `south` subdomain to the name server `west-ns01.contoso.com` using an IP address of `172.23.90.136`, run the following command.

```powershell
Add-DnsServerZoneDelegation -Name "west.contoso.com" -ChildZoneName "south" -NameServer "west-ns01.contoso.com" -IPAddress 172.23.90.136 -PassThru -Verbose
```

# [GUI](#tab/gui)
Here's how to create a zone delegation using DNS Manager.

1. From the Windows desktop, open the **Start** menu, select **Windows Administrative Tools &gt; DNS**.
2. In the console tree, expand a DNS server, right-click the DNS zone to delegate, then select **New Delegation**.
3. On the Delegated Domain Name page, enter the delegated domain name. For example, to delegate the subdomain `south.west.contoso.com`, enter `south`. The fully qualified domain name (FQDN) name is automatically be appended.
4. Select **Add** to specify the names and IP addresses of the DNS server to host the delegated zone.

    1. Enter either:

        - The FQDN of the DNS server that is authoritative for the delegated zone, then select **Resolve**. Add other DNS servers if necessary, when validated select **OK**.

            Or
        - Manually enter the IP address of the DNS server that is authoritative for the delegated zone. Add other DNS servers if necessary, when validated select **OK**.
5. Select **Finish** to complete the New Delegation Wizard.

---