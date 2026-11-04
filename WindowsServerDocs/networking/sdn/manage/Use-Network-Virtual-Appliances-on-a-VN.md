---
layout: Conceptual
title: Use network virtual appliances on a virtual network | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/manage/use-network-virtual-appliances-on-a-vn
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: In this topic, you learn how to deploy network virtual appliances on tenant virtual networks. You can add network virtual appliances to networks that perform user-defined routing and port mirroring functions.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-11-02T00:00:00.0000000Z
locale: en-us
document_id: 57212c1e-3d93-6567-8130-6cac85e07045
document_version_independent_id: 7297c6c3-bf41-4ef8-40d6-90ed3ea9614a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/manage/Use-Network-Virtual-Appliances-on-a-VN.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/manage/use-network-virtual-appliances-on-a-vn
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/manage/Use-Network-Virtual-Appliances-on-a-VN.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
platformId: fdc7a17f-21d4-8cb2-5abf-875a711b2962
---

# Use network virtual appliances on a virtual network | Microsoft Learn

In this topic, you learn how to deploy network virtual appliances on tenant virtual networks. You can add network virtual appliances to networks that perform user-defined routing and port mirroring functions.

## Types of network virtual appliances

You can use one of the two types of virtual appliances:

1. **User defined routing** - replaces distributed routers on the virtual network with the routing capabilities of the virtual appliance. With user-defined routing, the virtual appliance gets used as a router between the virtual subnets on the virtual network.
2. **Port mirroring** - all network traffic that is entering or leaving the monitored port is duplicated and sent to a virtual appliance for analysis.

## Deploying a network virtual appliance

To deploy a network virtual appliance, you must first create a VM that contains the appliance, and then connect the VM to the appropriate virtual network subnets. For more details, see [Create a Tenant VM and Connect to a Tenant Virtual Network or VLAN](create-a-tenant-vm).

Some appliances require multiple virtual network adapters. Usually, one network adapter dedicated to the appliance management while additional adapters process traffic. If your appliance requires multiple network adapters, you must create each network interface in Network Controller. You must also assign an interface ID on each host for each of the additional adapters that are on different virtual subnets.

Once you've deployed the network virtual appliance, you can use the appliance for defined routing, porting mirroring, or both.

## Example: User-defined routing

For most environments, you only need the system routes already defined by the virtual network's distributed router. However, you might need to create a routing table and add one or more routes in specific cases, such as:

- Force tunneling to the Internet via your on-premises network.
- Use of virtual appliances in your environment.

For these scenarios, you must create a routing table and add user-defined routes to the table. You can have multiple routing tables, and you can associate the same routing table to one or more subnets. You can only associate each subnet to a single routing table. All VMs in a subnet use the routing table associated to the subnet.

Subnets rely on system routes until a routing table gets associated to the subnet. After an association exists, routing is done based on Longest Prefix Match (LPM) among both user-defined routes and system routes. If there is more than one route with the same LPM match, then the user defined route is selected first - before the system route.

**Procedure:**

1. Create the route table properties, which contains all of the user defined routes.

    System routes still apply according to the rules defined above.

    ```PowerShell
     $routetableproperties = new-object Microsoft.Windows.NetworkController.RouteTableProperties
    ```
2. Add a route to the routing table properties.

    Any route destined for 12.0.0.0/8 subnet gets routed to the virtual appliance at 192.168.1.10. The appliance must have a virtual network adapter attached to the virtual network with that IP assigned to a network interface.

    ```PowerShell
     $route = new-object Microsoft.Windows.NetworkController.Route
     $route.ResourceID = "0_0_0_0_0"
     $route.properties = new-object Microsoft.Windows.NetworkController.RouteProperties
     $route.properties.AddressPrefix = "0.0.0.0/0"
     $route.properties.nextHopType = "VirtualAppliance"
     $route.properties.nextHopIpAddress = "192.168.1.10"
     $routetableproperties.routes += $route
    ```

    Tip

    If you want to add more routes, repeat this step for each route you want to define.
3. Add the routing table to Network Controller.

    ```PowerShell
     $routetable = New-NetworkControllerRouteTable -ConnectionUri $uri -ResourceId "Route1" -Properties $routetableproperties
    ```
4. Apply the routing table to the virtual subnet.

    When you apply the route table to the virtual subnet, the first virtual subnet in the Tenant1\_Vnet1 network uses the route table. You can assign the route table to as many of the subnets in the virtual network as you want.

    ```PowerShell
     $vnet = Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "Tenant1_VNet1"
     $vnet.properties.subnets[0].properties.RouteTable = $routetable
     new-networkcontrollervirtualnetwork -connectionuri $uri -properties $vnet.properties -resourceId $vnet.resourceid
    ```

As soon as you apply the routing table to the virtual network, traffic gets forwarded to the virtual appliance. You must configure the routing table in the virtual appliance to forward the traffic, in a manner that is appropriate for your environment.

## Example: Port mirroring

In this example, you configure the traffic for MyVM\_Ethernet1 to mirror Appliance\_Ethernet1. We assume that you've deployed two VMs, one as the appliance and the other as the VM to monitor with mirroring.

The appliance must have a second network interface for management. After you enable mirroring as a destination on Appliciance\_Ethernet1, it no longer receives traffic destined for the IP interface configured there.

**Procedure:**

1. Get the virtual network on which your VMs are located.

    ```PowerShell
    $vnet = Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "Tenant1_VNet1"
    ```
2. Get the Network Controller network interfaces for the mirroring source and destination.

    ```PowerShell
    $dstNic = get-networkcontrollernetworkinterface -ConnectionUri $uri -ResourceId "Appliance_Ethernet1"
    $srcNic = get-networkcontrollernetworkinterface -ConnectionUri $uri -ResourceId "MyVM_Ethernet1"
    ```
3. Create a serviceinsertionproperties object to contain the port mirroring rules and the element which represents the destination interface.

    ```PowerShell
    $portmirror = [Microsoft.Windows.NetworkController.ServiceInsertionProperties]::new()
    $portMirror.Priority = 1
    ```
4. Create a serviceinsertionrules object to contain the rules that must be matched in order for the traffic to be sent to the appliance.

    The rules defined below match all traffic, both inbound and outbound, which represents a traditional mirror. You can adjust these rules if you are interested in mirroring a specific port, or specific source/destinations.

    ```PowerShell
    $portmirror.ServiceInsertionRules = [Microsoft.Windows.NetworkController.ServiceInsertionRule[]]::new(1)
    
    $portmirror.ServiceInsertionRules[0] = [Microsoft.Windows.NetworkController.ServiceInsertionRule]::new()
    $portmirror.ServiceInsertionRules[0].ResourceId = "Rule1"
    $portmirror.ServiceInsertionRules[0].Properties = [Microsoft.Windows.NetworkController.ServiceInsertionRuleProperties]::new()
    
    $portmirror.ServiceInsertionRules[0].Properties.Description = "Port Mirror Rule"
    $portmirror.ServiceInsertionRules[0].Properties.Protocol = "All"
    $portmirror.ServiceInsertionRules[0].Properties.SourcePortRangeStart = "0"
    $portmirror.ServiceInsertionRules[0].Properties.SourcePortRangeEnd = "65535"
    $portmirror.ServiceInsertionRules[0].Properties.DestinationPortRangeStart = "0"
    $portmirror.ServiceInsertionRules[0].Properties.DestinationPortRangeEnd = "65535"
    $portmirror.ServiceInsertionRules[0].Properties.SourceSubnets = "*"
    $portmirror.ServiceInsertionRules[0].Properties.DestinationSubnets = "*"
    ```
5. Create a serviceinsertionelements object to contain the network interface of the mirrored appliance.

    ```PowerShell
    $portmirror.ServiceInsertionElements = [Microsoft.Windows.NetworkController.ServiceInsertionElement[]]::new(1)
    
    $portmirror.ServiceInsertionElements[0] = [Microsoft.Windows.NetworkController.ServiceInsertionElement]::new()
    $portmirror.ServiceInsertionElements[0].ResourceId = "Element1"
    $portmirror.ServiceInsertionElements[0].Properties = [Microsoft.Windows.NetworkController.ServiceInsertionElementProperties]::new()
    
    $portmirror.ServiceInsertionElements[0].Properties.Description = "Port Mirror Element"
    $portmirror.ServiceInsertionElements[0].Properties.NetworkInterface = $dstNic
    $portmirror.ServiceInsertionElements[0].Properties.Order = 1
    ```
6. Add the service insertion object in Network Controller.

    When you issue this command, all traffic to the appliance network interface specified in the previous step stops.

    ```PowerShell
    $portMirror = New-NetworkControllerServiceInsertion -ConnectionUri $uri -Properties $portmirror -ResourceId "MirrorAll"
    ```
7. Update the network interface of the source to be mirrored.

    ```PowerShell
    $srcNic.Properties.IpConfigurations[0].Properties.ServiceInsertion = $portMirror
    $srcNic = New-NetworkControllerNetworkInterface -ConnectionUri $uri  -Properties $srcNic.Properties -ResourceId $srcNic.ResourceId
    ```

After completing these steps, the Appliance\_Ethernet1 interface mirrors the traffic from the MyVM\_Ethernet1 interface.