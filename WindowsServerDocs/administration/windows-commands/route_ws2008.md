---
layout: Conceptual
title: route | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/route_ws2008
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the route command, which modifies and displays entries in the local IP routing table.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-10-05T00:00:00.0000000Z
locale: en-us
document_id: b5298689-e441-3788-b31d-967dbce4f735
document_version_independent_id: 5b078c74-5b82-3b35-5842-8ce6142b2152
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/route_ws2008.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/route_ws2008
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/route_ws2008.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0081ce75-6fb3-447f-97fa-23f8e1ae45ee
---

# route | Microsoft Learn

Displays and modifies the entries in the local IP routing table. If used without parameters, **route** displays help at the command prompt.

Important

This command is available only if the Internet Protocol (TCP/IP) protocol is installed as a component in the properties of a network adapter in Network Connections.

## Syntax

```cmd
route [/f] [/p] [<command> [<destination>] [mask <netmask>] [<gateway>] [metric <metric>]] [if <interface>]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /f | Clears the routing table of all entries that are not host routes (routes with a netmask of 255.255.255.255), the loopback network route (routes with a destination of 127.0.0.0 and a netmask of 255.0.0.0), or a multicast route (routes with a destination of 224.0.0.0 and a netmask of 240.0.0.0). If this is used in conjunction with one of the commands (such as add, change, or delete), the table is cleared prior to running the command. |
| /p | When used with the add command, the specified route is added to the registry and is used to initialize the IP routing table whenever the TCP/IP protocol is started. By default, added routes are not preserved when the TCP/IP protocol is started. When used with the print command, the list of persistent routes is displayed. This parameter is ignored for all other commands. Persistent routes are stored in the registry location **HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\PersistentRoutes**. |
| `<command>` | Specifies the command you want to run. The valid commands include:<br>- **add** - Adds a route.<br>- **change** - Modifies an existing route.<br>- **delete:** - Deletes a route or routes.<br>- **print** - Prints a route or routes. |
| `<destination>` | Specifies the network destination of the route. The destination can be an IP network address (where the host bits of the network address are set to 0), an IP address for a host route, or 0.0.0.0 for the default route. |
| `<mask>` | Specifies the next parameter for the 'netmask' value. |
| `<netmask>` | Specifies the network destination subnet mask. Defaults to 255.255.255.255 if not specified. |
| `<gateway>` | Specifies the forwarding or next hop IP address over which the set of addresses defined by the network destination and subnet mask are reachable. For locally attached subnet routes, the gateway address is the IP address assigned to the interface that is attached to the subnet. For remote routes, available across one or more routers, the gateway address is a directly reachable IP address that is assigned to a neighboring router. |
| metric `<metric>` | Specifies an integer cost metric (ranging from 1 to 9999) for the route, which is used when choosing among multiple routes in the routing table that most closely match the destination address of a packet being forwarded. The route with the lowest metric is chosen. The metric can reflect the number of hops, the speed of the path, path reliability, path throughput, or administrative properties. |
| if `<interface>` | Specifies the interface index for the interface over which the destination is reachable. For a list of interfaces and their corresponding interface indexes, use the display of the route print command. You can use either decimal or hexadecimal values for the interface index. For hexadecimal values, precede the hexadecimal number with 0x. When the if parameter is omitted, the interface is determined from the gateway address. |
| /? | Displays help at the command prompt. |

#### Remarks

- Large values in the **metric** column of the routing table are the result of allowing TCP/IP to automatically determine the metric for routes in the routing table based on the configuration of IP address, subnet mask, and default gateway for each LAN interface. Automatic determination of the interface metric, enabled by default, determines the speed of each interface and adjusts the metrics of routes for each interface so that the fastest interface creates the routes with the lowest metric. To remove the large metrics, disable the automatic determination of the interface metric from the advanced properties of the TCP/IP protocol for each LAN connection.
- Names can be used for *destination* if an appropriate entry exists in the local *Networks* file stored in the `systemroot\System32\Drivers\\` folder. Names can be used for the *gateway* as long as they can be resolved to an IP address through standard host name resolution techniques such as Domain Name System (DNS) queries, use of the local Hosts file stored in the `systemroot\system32\drivers\\` folder, and NetBIOS name resolution.
- if the command is **print** or **delete**, the *gateway* parameter can be omitted and wildcards can be used for the destination and gateway. The *destination* value can be a wildcard value specified by an asterisk `(*)`. If the destination specified contains an asterisk `(*)` or a question mark (?), it's treated as a wildcard, and only matching destination routes are printed or deleted. The asterisk matches any string, and the question mark matches any single character. For example, `10.\*.1, 192.168.\*`, `127.\*`, and `\*224\*` are all valid uses of the asterisk wildcard.
- Using an unsupported combination of a destination and subnet mask (netmask) value displays a "Route: bad gateway address netmask" error message. This error message appears when the destination contains one or more bits set to 1 in bit locations where the corresponding subnet mask bit is set to 0. To test this condition, express the destination and subnet mask using binary notation. The subnet mask in binary notation consists of a series of 1 bits, representing the network address portion of the destination, and a series of 0 bits, representing the host address portion of the destination. Check to determine whether there are bits in the destination that are set to 1 for the portion of the destination that is the host address (as defined by the subnet mask).

## Examples

To display the entire contents of the IP routing table, type:

```cmd
route print
```

To display the routes in the IP routing table that begin with 10, type:

```cmd
route print 10.*
```

To add a default route with the default gateway address of 192.168.12.1, type:

```cmd
route add 0.0.0.0 mask 0.0.0.0 192.168.12.1
```

To add a route to the destination 10.41.0.0 with the subnet mask of 255.255.0.0 and the next hop address of 10.27.0.1, type:

```cmd
route add 10.41.0.0 mask 255.255.0.0 10.27.0.1
```

To add a persistent route to the destination 10.41.0.0 with the subnet mask of 255.255.0.0 and the next hop address of 10.27.0.1, type:

```cmd
route /p add 10.41.0.0 mask 255.255.0.0 10.27.0.1
```

To add a route to the destination 10.41.0.0 with the subnet mask of 255.255.0.0, the next hop address of 10.27.0.1, and the cost metric of 7, type:

```cmd
route add 10.41.0.0 mask 255.255.0.0 10.27.0.1 metric 7
```

To add a route to the destination 10.41.0.0 with the subnet mask of 255.255.0.0, the next hop address of 10.27.0.1, and using the interface index 0x3, type:

```cmd
route add 10.41.0.0 mask 255.255.0.0 10.27.0.1 if 0x3
```

To delete the route to the destination 10.41.0.0 with the subnet mask of 255.255.0.0, type:

```cmd
route delete 10.41.0.0 mask 255.255.0.0
```

To delete all routes in the IP routing table that begin with 10, type:

```cmd
route delete 10.*
```

To change the next hop address of the route with the destination of 10.41.0.0 and the subnet mask of 255.255.0.0 from 10.27.0.1 to 10.27.0.25, type:

```cmd
route change 10.41.0.0 mask 255.255.0.0 10.27.0.25
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)