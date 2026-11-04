---
layout: Conceptual
title: Remote Access | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/remote-access
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: This topic provides an overview of the Remote Access services in Windows Server.
ms.topic: overview
ms.author: roharwoo
author: robinharwood
ms.date: 2022-09-28T00:00:00.0000000Z
locale: en-us
document_id: a9d8e4f9-6717-41fb-cca8-64e936965cf0
document_version_independent_id: a208cb51-3070-9be2-f8e3-1b61ffaf8ade
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/Remote-Access.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/remote-access
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/Remote-Access.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: cae7fa99-2da2-b644-a4a3-f29ded37d5e6
---

# Remote Access | Microsoft Learn

When you install the Remote Access Server Role with the *Add Roles and Features Wizard* or Windows PowerShell, you can choose to install one or more of the following three role services:

- Direct Access and VPN (RAS) service
- Routing service
- Web Application Proxy service

Anyone of these services can be installed either individually or on the same server.

Important

Don't attempt to deploy Remote Access on a virtual machine (VM) in Microsoft Azure. Using Remote Access in Microsoft Azure is not supported. You can't use Remote Access in an Azure VM to deploy VPN, DirectAccess, or any other Remote Access feature in Windows Server. For more information, see [Microsoft server software support for Microsoft Azure virtual machines](https://support.microsoft.com/help/2721672/microsoft-server-software-support-for-microsoft-azure-virtual-machines).

## DirectAccess and VPN service

### VPN (RAS)

The VPN service uses the connectivity of the internet and a combination of tunneling and data encryption technologies to connect to remote clients and offices.

With VPN and Routing service, you can also choose to deploy Always On VPN. Always On VPN enables Windows 10 clients to securely access shared resources, intranet Web sites, and the applications on an internal network without having to manually connect. For more information, see [Always On VPN](vpn/vpn-map-da)

### DirectAccess

DirectAccess allows connectivity for remote users to organization network resources without the need for traditional VPN connections. With DirectAccess connections, remote client computers are always connected to your organization. There's no need for remote users to start and stop connections, as is required with VPN connections. In addition, your IT administrators can manage DirectAccess client computers whenever they're' running and Internet connected.

Important

For Windows 10 or later, it is recommended to connect using Always On VPN. DirectAccess should be used only for clients earlier than Windows 10.

## Routing service

The Routing service allows you to route network traffic between subnets on your Local Area Network. Routing provides support for the following technologies:

- [Network Address Translation (NAT) routers](/en-us/previous-versions/windows/it-pro/windows-2000-server/cc957896%28v=technet.10%29)
- [LAN routers running Border Gateway Protocol (BGP)](bgp/border-gateway-protocol-bgp)
- [Routing Information Protocol (RIP)](/en-us/previous-versions/windows/it-pro/windows-2000-server/cc957940%28v=technet.10%29)
- [Multicast-capable routers using Internet Group Management Protocol (IGMP)](/en-us/previous-versions/windows/it-pro/windows-2000-server/cc957920%28v=technet.10%29)
- [Demand-dial routing](/en-us/previous-versions/windows/it-pro/windows-2000-server/cc957968%28v=technet.10%29)
- [Unicast IP Routing](/en-us/previous-versions/windows/it-pro/windows-2000-server/cc957899%28v=technet.10%29)

As a full-featured router, you can deploy RAS on either a physical computer or as a virtual machine (VM) on a computer that's running Hyper-V.

To install Remote Access as a LAN router, either use the *Add Roles and Features Wizard* in Server Manager and select the **Remote Access** server role and the **Routing** role service; or type the following command from an elevated Windows PowerShell prompt, and then press ENTER.

```
Install-RemoteAccess -VpnType RoutingOnly
```

## Web Application Proxy service

Web Application Proxy service provides reverse proxy functionality for web applications inside your corporate network to allow users on any device to access them from outside the corporate network. Web Application Proxy pre-authenticates access to web applications using Active Directory Federation Services (AD FS), and also functions as an AD FS proxy.

To install Remote Access as a Web Application Proxy, either use the Add Roles and Features Wizard in Server Manager and select the **Remote Access** server role and the **Web Application Proxy** role service; or type the following command at a Windows PowerShell prompt, and then press ENTER.

```
Install-RemoteAccess -VpnType SstpProxy
```

For more information, see [Web Application Proxy](web-application-proxy/web-app-proxy-windows-server).

For more information about other networking technologies, see [Networking in Windows Server](../../networking/).