---
layout: Conceptual
title: Deploy a Single DirectAccess Server Using the Getting Started Wizard | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/single-server-wizard/deploy-a-single-directaccess-server-using-the-getting-started-wizard
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn about the DirectAccess scenario that uses a single DirectAccess server, and allows you to deploy DirectAccess in a few easy steps.
ms.topic: install-set-up-deploy
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 7b4069eb-a776-7580-bc8f-aa6bd79474e4
document_version_independent_id: 1628cbdb-df01-e70c-3b00-ac9cabe95b2f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/single-server-wizard/Deploy-a-Single-DirectAccess-Server-Using-the-Getting-Started-Wizard.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/single-server-wizard/deploy-a-single-directaccess-server-using-the-getting-started-wizard
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/single-server-wizard/Deploy-a-Single-DirectAccess-Server-Using-the-Getting-Started-Wizard.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ecc03daf-45fb-990b-2208-88acc03b4d60
---

# Deploy a Single DirectAccess Server Using the Getting Started Wizard | Microsoft Learn

Important

Microsoft highly recommends that you use Always On VPN instead of DirectAccess for new deployments. For more information, see [Always on VPN](../../overview-always-on-vpn).

This topic provides an introduction to the DirectAccess scenario that uses a single DirectAccess server, and allows you to deploy DirectAccess in a few easy steps.

## Before you begin deploying, see the list of unsupported configurations, known issues, and prerequisites

You can use the following topics to review prerequisites and other information before you deploy DirectAccess.

- [DirectAccess Unsupported Configurations](../directaccess-unsupported-configurations)
- [Prerequisites for Deploying DirectAccess](../prerequisites-for-deploying-directaccess)

## Scenario description

In this scenario, a Windows Server computer is configured as a DirectAccess server with default settings. The configuration only requires a few easy wizard steps, without any need to configure infrastructure settings such as a certification authority (CA) or Active Directory security groups.

Note

If you want to configure an advanced deployment with custom settings, see [Deploy a Single DirectAccess Server with Advanced Settings](../single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings)

## In this scenario

To set up a basic DirectAccess server, several planning and deployment steps are required.

### Prerequisites

Before you begin deploying this scenario, review this list for important requirements:

- Windows firewall must be enabled on all profiles
- This scenario is only supported when your client computers are running Windows 10, Windows 8.1 or Windows 8.
- ISATAP in the corporate network isn't supported. If you're using ISATAP, you should remove it and use native IPv6.
- A Public Key Infrastructure isn't required.
- Not supported for deploying two factor authentication. Domain credentials are required for authentication.
- Automatically deploys DirectAccess to all mobile computers in the current domain.
- Traffic to Internet doesn't go over the DirectAccess tunnel. Force tunnel configuration isn't supported.
- DirectAccess server is the Network Location Server.
- Network Access Protection (NAP) isn't supported.
- Changing policies outside of the DirectAccess management console or PowerShell cmdlets isn't supported.
- To deploy multisite, now or in the future, first [Deploy a Single DirectAccess Server with Advanced Settings](../single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings).

### Planning steps

Planning is divided into two phases:

1. Planning for the DirectAccess infrastructure. This phase describes the planning that's required to set up the network infrastructure before beginning the DirectAccess deployment. Planning includes the design of the network and server topology, and the DirectAccess network location server.
2. Planning for the DirectAccess deployment. This phase describes the planning steps required to prepare for the DirectAccess deployment. It includes planning for DirectAccess client computers, server and client authentication requirements, VPN settings, infrastructure servers, and management and application servers.

For detailed planning steps, see [Plan an Advanced DirectAccess Deployment](../single-server-advanced/plan-an-advanced-directaccess-deployment).

### Deployment steps

Deployment is divided into three phases:

1. Configuring the DirectAccess infrastructure. This phase includes configuring the following components:

- Network and routing
- Firewall settings (if required)
- Certificates
- DNS servers
- Active Directory and GPO settings
- DirectAccess network location server

1. Configuring DirectAccess server settings. This phase includes steps for configuring DirectAccess client computers, the DirectAccess server, infrastructure servers, management and application servers.
2. Verifying the deployment. This phase includes steps to verify that the deployment is working as required.

For detailed deployment steps, see [Install and Configure Basic DirectAccess](install-and-configure-basic-directaccess).

## Practical applications

Deploying a single Remote Access server provides the following benefits:

- Ease-of-access. You can configure managed client computers running Windows 10, Windows 8.1, Windows 8, or Windows 7, as DirectAccess clients. These clients can access internal network resources via DirectAccess anytime they're located on the Internet without needing to log in to a VPN connection. Client computers that aren't running one of these operating systems can connect to the internal network by using traditional VPN connections.
- Ease-of-management. DirectAccess client computers located on the Internet can be remotely managed by Remote Access administrators over DirectAccess, even when the client computers aren't located in the internal corporate network. Client computers that don't meet corporate requirements can be remediated automatically by management servers. Both DirectAccess and VPN are managed in the same console and with the same set of wizards. Additionally, one or more Remote Access servers can be managed from a single Remote Access Management console

## Roles and features included in this scenario

The following table lists the roles and features required for the scenario:

| Role/feature | How it supports this scenario |
| --- | --- |
| Remote Access role | The role is installed and uninstalled using the Server Manager console or Windows PowerShell. This role encompasses both DirectAccess, Routing, and Remote Access Services. The Remote Access role consists of two components:<br>1. DirectAccess and Routing and Remote Access Services (RRAS) VPN. DirectAccess and VPN are managed together in the Remote Access Management console.2. RRAS Routing. RRAS routing features are managed in the legacy Routing and Remote Access console.<br><br>The Remote Access Server Role is dependent on the following server roles/features:<br><br>- Internet Information Services (IIS) Web Server - This feature is required to configure the network location server on the Remote Access server, and the default web probe.- Windows Internal Database. Used for local accounting on the Remote Access server. |
| Remote Access Management Tools feature | This feature is installed as follows:<br>- It's installed by default on a Remote Access server when the Remote Access role is installed, and supports the Remote Management console user interface and Windows PowerShell cmdlets.- It can be optionally installed on a server not running the Remote Access server role. In this case, it's used for remote management of a Remote Access computer running DirectAccess and VPN.<br><br>The Remote Access Management Tools feature consists of the following components:<br><br>- Remote Access GUI- Remote Access module for Windows PowerShell<br><br>Dependencies include:<br><br>- Group Policy Management Console- RAS Connection Manager Administration Kit (CMAK)- Windows PowerShell 3.0- Graphical Management Tools and Infrastructure |

## Hardware requirements

Hardware requirements for this scenario include the following:

- Server requirements:

    - A computer that meets the hardware requirements for Windows Server 2016, Windows Server 2012 R2 , or Windows Server 2012 .
    - The server must have at least one network adapter installed, enabled, and connected to the internal network. When two adapters are used, there should be one adapter connected to the internal corporate network, and one connected to the external network (Internet, or private network).
    - At least one domain controller. The Remote Access server and DirectAccess clients must be domain members.
- Client requirements:

    - A client computer must be running Windows 10, Windows 8.1 or Windows 8.

        Important

        If some or all of your client computers are running Windows 7, you must use the Advanced Setup Wizard. The Getting Started Setup Wizard described in this document does'nt support client computers that are running Windows 7. See [Deploy a Single DirectAccess Server with Advanced Settings](../single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings) for instructions on how to use Windows 7 clients with DirectAccess.

        Note

        Only the following operating systems can be used as DirectAccess clients: Windows 10 Enterprise, Windows 8.1 Enterprise, Windows Server 2016, Windows Server 2012 R2 , Windows Server 2012 , Windows 8 Enterprise, Windows Server 2008 R2, Windows 7 Enterprise, and Windows 7 Ultimate.
- Infrastructure and management server requirements:

    - If VPN is enabled and a static IP address pool isn't configured, you must deploy a DHCP server to allocate IP addresses automatically to VPN clients.
- A DNS server running Windows Server 2016, Windows Server 2012 R2 , Windows Server 2012 , Windows Server 2008 SP2, or Windows Server 2008 R2 is required.

## Software requirements

Below are the requirements for this scenario:

- Server requirements:

    - The Remote Access server must be a domain member. The server can be deployed at the edge of the internal network, or behind an edge firewall or other device.
    - If the Remote Access server is located behind an edge firewall or NAT device, the device must be configured to allow traffic to and from the Remote Access server.
    - The person deploying remote access on the server requires local administrator permissions on the server, and domain user permissions. In addition, the administrator requires permissions for the GPOs used in DirectAccess deployment. To take advantage of the features that restricts DirectAccess deployment to mobile computers only, permissions to create a WMI filter on the domain controller are required.
- Remote Access client requirements:

    - DirectAccess clients must be domain members. Domains containing clients can belong to the same forest as the Remote Access server, or have a two-way trust with the Remote Access server forest.
    - An Active Directory security group is required to contain the computers that will be configured as DirectAccess clients. If a security group isn't specified when configuring DirectAccess client settings, by default the client GPO is applied on all laptop computers in the Domain Computers security group. Only the following operating systems can be used as DirectAccess clients: Windows Server 2016, Windows Server 2012 R2 , Windows Server 2012 , Windows Server 2008 R2, Windows 8 Enterprise, Windows 7 Enterprise, and Windows 7 Ultimate.

## See also

The following table provides links to additional resources.

| Content type | References |
| --- | --- |
| **Remote Access on TechNet** | [Remote Access TechCenter](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn756544%28v=ws.11%29) |
| **Tools and settings** | [Remote Access PowerShell cmdlets](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn756544%28v=ws.11%29) |
| **Community resources** | [DirectAccess Wiki entries](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn636118%28v=ws.11%29) |
| **Related technologies** | [How IPv6 works](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc781672%28v=ws.10%29) |