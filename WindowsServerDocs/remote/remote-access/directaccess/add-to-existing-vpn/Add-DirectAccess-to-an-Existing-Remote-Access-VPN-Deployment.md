---
layout: Conceptual
title: Add DirectAccess to an Existing Remote Access (VPN) Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/add-to-existing-vpn/add-directaccess-to-an-existing-remote-access-vpn-deployment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to add DirectAccess to an existing remote access (VPN) deployment for Windows Server 2016.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: b49972b9-37f4-ca1c-48c4-9c128120adba
document_version_independent_id: 46a6d5e0-1c02-293e-37a1-be6f986c508d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/add-to-existing-vpn/Add-DirectAccess-to-an-Existing-Remote-Access-VPN-Deployment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/add-to-existing-vpn/add-directaccess-to-an-existing-remote-access-vpn-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/add-to-existing-vpn/Add-DirectAccess-to-an-Existing-Remote-Access-VPN-Deployment.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 084630dc-2f85-ca3d-33e4-88366811363f
---

# Add DirectAccess to an Existing Remote Access (VPN) Deployment | Microsoft Learn

Important

Microsoft highly recommends that you use Always On VPN instead of DirectAccess for new deployments. For more information, see [Always on VPN](../../overview-always-on-vpn).

## Scenario description

In this scenario, a single computer running Windows Server 2016, Windows Server 2012 R2 or Windows Server 2012 is configured as a DirectAccess server with recommended settings after you have already installed and configured VPN. If you want to configure DirectAccess with enterprise features, such as a load-balanced cluster, multisite deployment, or two-factor client authentication, complete the scenario described in this topic to set up a single server, and then set up the enterprise scenario as described in [Deploy Remote Access in an enterprise](../../ras/deploy-remote-access-in-an-enterprise).

## In this scenario

To set up a single Remote Access server, a number of planning and deployment steps are required.

### Planning steps

Planning is divided into two phases:

1. **Plan the Remote Access infrastructure**

    In this phase, you describe the planning that is required to set up the network infrastructure before you begin the Remote Access deployment. It includes planning for the network and server topology, certificates, Domain Name System (DNS), Active Directory and Group Policy Object (GPO) configuration, and the DirectAccess network location server.
2. **Plan the Remote Access deployment**

    In this phase, you describe the planning steps that are required to prepare for the Remote Access deployment. It includes planning for Remote Access client computers, server and client authentication requirements, and infrastructure servers.

### Deployment steps

Deployment is divided into three phases:

1. **Configure the Remote Access infrastructure**

    In this phase, you configure the network and routing, firewall settings (if required), certificates, DNS servers, Active Directory and GPO settings, and the DirectAccess network location server.
2. **Configure Remote Access server settings**

    In this phase, you configure the Remote Access client computers, the Remote Access server, and the infrastructure servers.
3. **Verify the deployment**

    In this phase, you verify that the deployment is working as required.

## Practical applications

Deploying a single Remote Access server provides the following:

- **Ease of access**

    Managed client computers running Windows 8 and Windows 7 can be configured as DirectAccess client computers. These clients can access internal network resources through DirectAccess any time they are located on the Internet, without the need to sign in to a VPN connection. Client computers that are not running one of these operating systems can connect to the internal network through a VPN. DirectAccess and VPN are managed in the same console and with the same set of wizards.
- **Ease of management**

    DirectAccess client computers that have access to the Internet can be remotely managed by remote access administrators by using DirectAccess, even when the client computers are not located on the internal corporate network. Client computers that do not meet corporate requirements can be remediated automatically by management servers.

## Roles and features required for this scenario

The following table lists the roles and features that are required for this scenario:

| Role/feature | How it supports this scenario |
| --- | --- |
| Remote Access role | The role is installed and uninstalled by using the Server Manager console or Windows PowerShell. This role encompasses DirectAccess, which was previously a feature in Windows Server 2008 R2, and Routing and Remote Access Services, which was previously a role service under the Network Policy and Access Services (NPAS) server role. The Remote Access role consists of two components:<br>1. DirectAccess and Routing and Remote Access Services (RRAS) VPN: Managed in the Remote Access Management console.2. RRAS Routing: Managed in the Routing and Remote Access console.<br><br>The Remote Access Server role is dependent on the following server features:<br><br>- Internet Information Services (IIS) Web Server:Required to configure the network location server on the Remote Access server, and the default web probe.- Windows Internal Database: Used for local accounting on the Remote Access server. |
| Remote Access Management Tools feature | This feature is installed as follows:<br>- By default on a Remote Access server when the Remote Access role is installed. Supports the Remote Management console user interface and the Windows PowerShell cmdlets.- Optionally installed on a server not running the Remote Access server role. In this case, it is used for remote management of a Remote Access computer running DirectAccess and VPN.<br><br>The Remote Access Management Tools feature consists of the following:<br><br>- Remote Access GUI- Remote Access module for Windows PowerShell<br><br>Dependencies include:<br><br>- Group Policy Management Console- RAS Connection Manager Administration Kit (CMAK)- Windows PowerShell 3.0- Graphical Management Tools and Infrastructure |

## Hardware requirements

Hardware requirements for this scenario include the following:

**Server requirements**

- A computer that meets the hardware requirements for Windows Server 2012 .
- The server must have at least one network adapter installed, enabled, and joined to the internal network. When two adapters are used, there should be one adapter connected to the internal corporate network, and one connected to the external network (Internet).
- If Teredo is required as an IPv4 to IPv6 transition protocol, the external adapter of the server requires two consecutive public IPv4 addresses. The Enable DirectAccess Wizard does not enable Teredo, even if two consecutive IP addresses are present. If a single IP address is available, only IP-HTTPS can be used as the transition protocol.
- At least one domain controller. The Remote Access server and DirectAccess clients must be domain members.
- The Enable DirectAccess Wizard requires certificates for IP-HTTPS and the network location server. If the SSTP VPN is already using a certificate, it is reused for IP-HTTPS. If the SSTP VPN is not configured, you can configure a certificate for IP-HTTPS or use an automatically created self-signed certificate. For the network location server, you can configure a certificate or use an automatically created self-signed certificate.

**Client requirements**

- A client computer must be running Windows 8 or Windows 7.

    Note

    Only the following operating systems can be used as DirectAccess clients: Windows Server 2012, Windows Server 2008 R2, Windows 8 Enterprise, Windows 7 Enterprise, and Windows 7 Ultimate.

**Infrastructure and management server requirements**

- During the remote management of DirectAccess client computers, clients initiate communication with management servers, such as domain controllers, System Center configuration servers, and Health Registration Authority (HRA) servers for services that include Windows and antivirus updates and Network Access Protection (NAP) client compliance. The required servers should be deployed before you begin the Remote Access deployment.
- If remote access requires client NAP compliance, the Network Policy Server (NPS) and the HRA should be deployed before you begin the Remote Access deployment.
- A DNS server running Windows Server 2012 , Windows Server 2008 R2, or Windows Server 2008 with SP2 is required.

## Software requirements

Software requirements for this scenario include the following:

**Server requirements**

- The Remote Access server must be a domain member. The server can be deployed at the edge of the internal network, or behind an edge firewall or other device.
- If the Remote Access server is located behind an edge firewall or network address translation (NAT) device, the device must be configured to allow traffic to and from the Remote Access server.
- The person who deploys remote access on the server requires local administrator permissions on the server, and domain user permissions. In addition, the administrator requires permissions for the GPOs that are used in DirectAccess deployment. To take advantage of the features that restrict a DirectAccess deployment to mobile computers only, permissions to create a WMI filter on the domain controller are required.

**Remote access client requirements**

- DirectAccess clients must be domain members. Domains that contain clients can belong to the same forest as the Remote Access server, or they can have a two-way trust with the Remote Access server forest or domain.
- An Active Directory security group is required to contain the computers that will be configured as DirectAccess clients. If a security group is not specified when you configure DirectAccess client settings, by default, the client GPO is applied on all laptop computers (that are DirectAccess capable) in the Domain Computers security group. Only the following operating systems can be used as DirectAccess clients: Windows Server 2012 , Windows Server 2008 R2 , Windows 8 Enterprise, Windows 7 Enterprise, and Windows 7 Ultimate.

    Note

    We recommend that you create a security group for each domain that contains computers that will be configured as DirectAccess clients.