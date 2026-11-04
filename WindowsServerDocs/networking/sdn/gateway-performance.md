---
layout: Conceptual
title: SDN gateway performance | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/gateway-performance
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: Learn more about SDN gateway performance
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2023-09-18T00:00:00.0000000Z
locale: en-us
document_id: 4e665502-aa55-3f4c-b521-694190b7178b
document_version_independent_id: 697b2a28-55a6-8397-ea71-11e8a270f9c1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/gateway-performance.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/gateway-performance
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/gateway-performance.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b9ca1709-c1b3-3e77-dc98-fb46beef1610
---

# SDN gateway performance | Microsoft Learn

In Windows Server 2016, one of the customer concerns was the inability of SDN gateway to meet the throughput requirements of modern networks. The network throughput of IPsec and GRE tunnels had limitations with the single connection throughput for IPsec connectivity being about 300 Mbps and for GRE connectivity being about 2.5 Gbps.

Starting with Windows Server 2019, we have significantly improved SDN gateway performance, with the numbers soaring to 1.8 Gbps and 15 Gbps for IPsec and GRE connections, respectively. All this, with significant reductions in the CPU cycles/per byte, thereby providing ultra-high-performance throughput with much less CPU utilization.

## Enable high performance with gateways

For **GRE connections**, once you deploy/upgrade to Windows Server 2019 builds on the gateway VMs, you should automatically see the improved performance. No manual steps are involved.

For **IPsec connections**, by default, when you create the connection for your virtual networks, you get the Windows Server 2016 data path and performance numbers. To enable the Windows Server 2019 data path, do the following:

1. On an SDN gateway VM, go to **Services** console (services.msc).
2. Find the service named **Azure Gateway Service**, and set the startup type to **Automatic**.
3. Restart the gateway VM. The active connections on this gateway failover to a redundant gateway VM.
4. Repeat the previous steps for rest of the gateway VMs.

The following requirements must be met for high performance IPsec connections to work:

- Network Address Translation-Traversal (NAT-T) should be enabled on your on-premises gateway. When enabling high performance IPsec connections, SDN gateway configures a NAT rule, hence you also need to enable NAT-T on your on-premises gateway.
- The on-premises gateway should allow User Datagram Protocol (UDP) packets on ports 500 and 4500 and protocol 50 and 51.

Tip

For the best performance results, ensure that the cipherTransformationConstant and authenticationTransformConstant in quickMode settings of the IPsec connection uses the **GCMAES256** cipher suite.

For maximum performance, the gateway host hardware must support AES-NI and PCLMULQDQ CPU instruction sets. These are available on any Westmere (32nm) and later Intel CPU except on models where AES-NI has been disabled. You can look at your hardware vendor documentation to see if the CPU supports AES-NI and PCLMULQDQ CPU instruction sets.

Below is a REST sample of IPsec connection with optimal security algorithms:

```PowerShell
# NOTE: The virtual gateway must be created before creating the IPsec connection. More details here.
# Create a new object for Tenant Network IPsec Connection
$nwConnectionProperties = New-Object Microsoft.Windows.NetworkController.NetworkConnectionProperties

# Update the common object properties
$nwConnectionProperties.ConnectionType = "IPSec"
$nwConnectionProperties.OutboundKiloBitsPerSecond = 2000000
$nwConnectionProperties.InboundKiloBitsPerSecond = 2000000

# Update specific properties depending on the Connection Type
$nwConnectionProperties.IpSecConfiguration = New-Object Microsoft.Windows.NetworkController.IpSecConfiguration
$nwConnectionProperties.IpSecConfiguration.AuthenticationMethod = "PSK"
$nwConnectionProperties.IpSecConfiguration.SharedSecret = "111_aaa"

$nwConnectionProperties.IpSecConfiguration.QuickMode = New-Object Microsoft.Windows.NetworkController.QuickMode
$nwConnectionProperties.IpSecConfiguration.QuickMode.PerfectForwardSecrecy = "PFS2048"
$nwConnectionProperties.IpSecConfiguration.QuickMode.AuthenticationTransformationConstant = "GCMAES256"
$nwConnectionProperties.IpSecConfiguration.QuickMode.CipherTransformationConstant = "GCMAES256"
$nwConnectionProperties.IpSecConfiguration.QuickMode.SALifeTimeSeconds = 3600
$nwConnectionProperties.IpSecConfiguration.QuickMode.IdleDisconnectSeconds = 500
$nwConnectionProperties.IpSecConfiguration.QuickMode.SALifeTimeKiloBytes = 2000

$nwConnectionProperties.IpSecConfiguration.MainMode = New-Object Microsoft.Windows.NetworkController.MainMode
$nwConnectionProperties.IpSecConfiguration.MainMode.DiffieHellmanGroup = "Group2"
$nwConnectionProperties.IpSecConfiguration.MainMode.IntegrityAlgorithm = "SHA256"
$nwConnectionProperties.IpSecConfiguration.MainMode.EncryptionAlgorithm = "AES256"
$nwConnectionProperties.IpSecConfiguration.MainMode.SALifeTimeSeconds = 28800
$nwConnectionProperties.IpSecConfiguration.MainMode.SALifeTimeKiloBytes = 2000

# L3 specific configuration (leave blank for IPSec)
$nwConnectionProperties.IPAddresses = @()
$nwConnectionProperties.PeerIPAddresses = @()

# Update the IPv4 Routes that are reachable over the site-to-site VPN Tunnel
$nwConnectionProperties.Routes = @()
$ipv4Route = New-Object Microsoft.Windows.NetworkController.RouteInfo
$ipv4Route.DestinationPrefix = "<<On premise subnet that must be reachable over the VPN tunnel. Ex: 10.0.0.0/24>>"
$ipv4Route.metric = 10
$nwConnectionProperties.Routes += $ipv4Route

# Tunnel Destination (Remote Endpoint) Address
$nwConnectionProperties.DestinationIPAddress = "<<Public IP address of the On-Premise VPN gateway. Ex: 192.168.3.4>>"

# Add the new Network Connection for the tenant. Note that the virtual gateway must be created before creating the IPsec connection. $uri is the REST URI of your deployment and must be in the form of “https://<REST URI>”
New-NetworkControllerVirtualGatewayNetworkConnection -ConnectionUri $uri -VirtualGatewayId $virtualGW.ResourceId -ResourceId "Contoso_IPSecGW" -Properties $nwConnectionProperties -Force
```

## Testing Results

We have done extensive performance testing for the SDN gateways in our test labs. In the tests, we have compared gateway network performance with Windows Server 2019 in SDN scenarios and non-SDN scenarios. You can find the results and test setup details captured in the blog article [here](https://techcommunity.microsoft.com/t5/networking-blog/top-10-networking-features-in-windows-server-2019-6-high/ba-p/339766).