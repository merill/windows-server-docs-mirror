---
layout: Conceptual
title: Deploy a Single DirectAccess Server with Advanced Settings | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn about the DirectAccess scenario that uses a single DirectAccess server, and allows you to deploy DirectAccess with advanced settings.
ms.topic: install-set-up-deploy
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 156167ec-27d8-63f6-e93a-8a8b61ae9904
document_version_independent_id: 0e9985bd-cac0-faf4-8b9f-4a5bc103582f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 75749383-f908-7fd6-b829-abe3bda7d461
---

# Deploy a Single DirectAccess Server with Advanced Settings | Microsoft Learn

Important

Microsoft highly recommends that you use Always On VPN instead of DirectAccess for new deployments. For more information, see [Always on VPN](../../overview-always-on-vpn).

This topic provides an introduction to the DirectAccess scenario that uses a single DirectAccess server, and allows you to deploy DirectAccess with advanced settings.

## Before you begin deploying, see the list of unsupported configurations, known issues, and prerequisites

You can use the following topics to review prerequisites and other information before you deploy DirectAccess.

- [DirectAccess Unsupported Configurations](../directaccess-unsupported-configurations)
- [Prerequisites for Deploying DirectAccess](../prerequisites-for-deploying-directaccess)

## Scenario description

In this scenario, a single computer running either Windows Server 2016, Windows Server 2012 R2 or Windows Server 2012, is configured as a DirectAccess server with advanced settings.

Note

If you want to configure a basic deployment with simple settings only, see [Deploy a Single DirectAccess Server Using the Getting Started Wizard](../single-server-wizard/deploy-a-single-directaccess-server-using-the-getting-started-wizard). In the simple scenario, DirectAccess is configured with default settings by using a wizard, without any need to configure infrastructure settings such as a certification authority (CA) or Active Directory security groups.

## In this scenario

To set up a single DirectAccess server with advanced settings, you must complete several planning and deployment steps.

### Prerequisites

Before you begin, you can review the following requirements.

- Windows Firewall must be enabled on all profiles.
- The DirectAccess server is the network location server.
- You want all wireless computers in the domain where you install the DirectAccess server to be DirectAccess-enabled. When you deploy DirectAccess, it is automatically enabled on all mobile computers in the current domain.

Important

Some technologies and configurations are not supported when you deploy DirectAccess.

- Intra-Site Automatic Tunnel Addressing Protocol (ISATAP) in the corporate network is not supported. If you are using ISATAP, you must remove it and use native IPv6.

### Planning steps

Planning is divided into two phases:

1. **Planning for the DirectAccess infrastructure**. This phase describes the planning required to set up the network infrastructure before beginning the DirectAccess deployment. It includes planning the network and server topology, certificate planning, DNS, Active Directory and Group Policy object (GPO) configuration, and the DirectAccess network location server.
2. **Planning for the DirectAccess deployment**. This phase describes the planning steps required to prepare for the DirectAccess deployment. It includes planning for DirectAccess client computers, server and client authentication requirements, VPN settings, infrastructure servers, and management and application servers.

### Deployment steps

Deployment is divided into three phases:

1. **Configuring the DirectAccess infrastructure**. This phase includes configuring network and routing, configuring firewall settings if required, configuring certificates, DNS servers, Active Directory and GPO settings, and the DirectAccess network location server.
2. **Configuring DirectAccess server settings**. This phase includes steps for configuring DirectAccess client computers, the DirectAccess server, infrastructure servers, management and application servers.
3. **Verifying the deployment**. This phase includes steps to verify the DirectAccess deployment.

For detailed deployment steps, see [Install and Configure Advanced DirectAccess](install-and-configure-advanced-directaccess).

## Practical applications

Deploying a single DirectAccess server provides the following:

- **Ease of access**. Managed client computers running Windows 10, Windows 8.1, Windows 8, and Windows 7 can be configured as DirectAccess client computers. These clients can access internal network resources via DirectAccess any time they are located on the Internet without needing to log in to a VPN connection. Client computers not running one of these operating systems can connect to the internal network via VPN.
- **Ease of management**. DirectAccess client computers located on the Internet can be remotely managed by Remote Access administrators over DirectAccess, even when the client computers are not located in the internal corporate network. Client computers that do not meet corporate requirements can be remediated automatically by management servers. Both DirectAccess and VPN are managed in the same console and with the same set of wizards. Additionally, one or more DirectAccess servers can be managed from a single Remote Access Management console

## Roles and features required for this scenario

The following table lists the roles and features that are required for this scenario:

| Role/feature | How it supports this scenario |
| --- | --- |
| Remote Access role | The role is installed and uninstalled using the Server Manager console or Windows PowerShell. This role encompasses both DirectAccess and Routing and Remote Access Services (RRAS). The Remote Access role consists of two components:1. DirectAccess and RRAS VPN. DirectAccess and VPN are managed together in the Remote Access Management console.2. RRAS Routing. RRAS routing features are managed in the legacy Routing and Remote Access console.<br>The Remote Access server role is dependent on the following server roles/features: - Internet Information Services (IIS) Web Server - This feature is required to configure the network location server on the DirectAccess server, and the default web probe. - Windows Internal Database. Used for local accounting on the DirectAccess server. |
| Remote Access Management Tools feature | This feature is installed as follows:<br>- It is installed by default on a DirectAccess server when the Remote Access role is installed, and supports the Remote Management console user interface and Windows PowerShell cmdlets.- It can be optionally installed on a server not running the DirectAccess server role. In this case it is used for remote management of a Remote Access computer running DirectAccess and VPN.<br><br>The Remote Access Management Tools feature consists of the following:<br><br>- Remote Access graphical user interface (GUI)- Remote Access module for Windows PowerShell<br><br>Dependencies include:<br><br>- Group Policy Management Console- RAS Connection Manager Administration Kit (CMAK)- Windows PowerShell 3.0- Graphical Management Tools and Infrastructure |

## Hardware requirements

Hardware requirements for this scenario include the following:

- Server requirements:

    - A computer that meets the hardware requirements for Windows Server 2016, Windows Server 2012 R2 or Windows Server 2012 .
    - The server must have at least one network adapter installed, enabled, and connected to the internal network. When two adapters are used, there should be one adapter connected to the internal corporate network, and one connected to the external network (Internet, or private network).
    - If Teredo is required as an IPv4 to IPv6 transition protocol, the external adapter of the server requires two consecutive public IPv4 addresses. If a single IP address is available, then only IP-HTTPS can be used as the transition protocol.
    - At least one domain controller. The DirectAccess server and DirectAccess clients must be domain members.
    - A certification authority (CA) is required if you do not want to use self-signed certificates for IP-HTTPS or the network location server, or if you want to use client certificates for client IPsec authentication. Alternatively, you can request certificates from a public CA.
    - If the network location server is not located on the DirectAccess server, a separate web server is required to run it.
- Client requirements:

    - A client computer must be running Windows 10, Windows 8, or Windows 7.

        Note

        The following operating systems can be used as DirectAccess clients: Windows 10, Windows Server 2012 R2 , Windows Server 2012 , Windows 8 Enterprise, Windows 7 Enterprise, or Windows 7 Ultimate.
- Infrastructure and management server requirements:

    - During remote management of DirectAccess client computers, clients initiate communications with management servers such as domain controllers, System Center Configuration Servers, and Health Registration Authority (HRA) servers for services that include Windows and antivirus updates and Network Access Protection (NAP) client compliance. The required servers should be deployed before beginning the Remote Access deployment.
    - If Remote Access requires client NAP compliance, NPS and HRS servers should be deployed before beginning remote access deployment
    - If VPN is enabled, a DHCP server is required to allocate IP addresses automatically to VPN clients, if a static address pool is not used.

## Software requirements

There are a number of requirements for this scenario:

- Server requirements:

    - The DirectAccess server must be a domain member. The server can be deployed at the edge of the internal network, or behind an edge firewall or other device.
    - If the DirectAccess server is located behind an edge firewall or NAT device, the device must be configured to allow traffic to and from the DirectAccess server.
    - The person deploying remote access on the server requires local administrator permissions on the server, and domain user permissions. In addition, the administrator requires permissions for the GPOs used in DirectAccess deployment. To take advantage of the features that restricts DirectAccess deployment to mobile computers only, permissions to create a WMI filter on the domain controller are required.
- Remote Access client requirements:

    - DirectAccess clients must be domain members. Domains containing clients can belong to the same forest as the DirectAccess server, or have a two-way trust with the DirectAccess server forest or domain.
    - An Active Directory security group is required to contain the computers that will be configured as DirectAccess clients. If a security group is not specified when configuring DirectAccess client settings, by default the client GPO is applied on all laptop computers in the Domain Computers security group.

        Note

        It is recommended that you create a security group for each domain that contains DirectAccess client computers.

        Important

        If you have enabled Teredo in your DirectAccess deployment, and you want to provide access to Windows 7 clients, ensure that the clients are upgraded to Windows 7 with SP1. Clients using Windows 7 RTM will not be able to connect over Teredo. However, these clients will still be able to connect to the corporate network over IP-HTTPS.

## See also

The following table provides links to additional resources.

| Content type | References |
| --- | --- |
| **Deployment** | [DirectAccess Deployment Paths in Windows Server](../directaccess-deployment-paths-in-windows-server)<br>[Deploy a Single DirectAccess Server Using the Getting Started Wizard](../single-server-wizard/deploy-a-single-directaccess-server-using-the-getting-started-wizard) |
| **Tools and settings** | [Remote Access PowerShell cmdlets](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831379%28v=ws.11%29) |
| **Community resources** | [DirectAccess Survival Guide](/en-us/answers/topics/windows-server-infrastructure.html)<br>[DirectAccess Wiki entries](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn636118%28v=ws.11%29) |
| **Related technologies** | [How IPv6 works](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc781672%28v=ws.10%29) |