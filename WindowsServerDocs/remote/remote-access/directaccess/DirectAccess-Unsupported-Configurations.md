---
layout: Conceptual
title: DirectAccess Unsupported Configurations | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/directaccess-unsupported-configurations
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: This topic provides a list of unsupported DirectAccess configurations in Windows Server 2016.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: ac2ab7c4-c2e8-1faf-790b-35d9f9bdde15
document_version_independent_id: 563c1610-29a5-8c67-c8c7-2dc65395ea21
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/DirectAccess-Unsupported-Configurations.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/directaccess-unsupported-configurations
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/DirectAccess-Unsupported-Configurations.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7fdf6e9c-a84d-0c16-aa24-103a80fd8c10
---

# DirectAccess Unsupported Configurations | Microsoft Learn

Review the following list of unsupported DirectAccess configurations before you start your deployment to avoid having to start your deployment again.

## File Replication Service (FRS) distribution of Group Policy objects (SYSVOL replications)

Do not deploy DirectAccess in environments where your domain controllers are running the File Replication Service (FRS) for distribution of Group Policy objects (SYSVOL replications). Deployment of DirectAccess is not supported when you use FRS.

You are using FRS if you have domain controllers that are running Windows Server 2003 or Windows Server 2003 R2. In addition, you might be using FRS if you previously used Windows 2000 Server or Windows Server 2003 domain controllers and you never migrated SYSVOL replication from FRS to Distributed File System Replication (DFS-R).

If you deploy DirectAccess with FRS SYSVOL replication, you risk the unintentional deletion of DirectAccess Group Policy objects that contain the DirectAccess server and client configuration information. If these objects are deleted, your DirectAccess deployment will suffer an outage, and client computers that use DirectAccess will not be able to connect to your network.

If you are planning to deploy DirectAccess, you must use domain controllers that are running operating systems later than Windows Server 2003 R2, and you must use DFS-R.

For information on migrating from FRS to DFS-R, see the [SYSVOL Replication Migration Guide: FRS to DFS Replication](../../../storage/dfs-replication/migrate-sysvol-to-dfsr).

## Network Access Protection for DirectAccess clients

Network Access Protection (NAP) is used to determine whether remote client computers meet IT policies before they are granted access to the corporate network. NAP was deprecated in Windows Server 2012 R2 and is not included in Windows Server 2016. For this reason, starting a new deployment of DirectAccess with NAP is not recommended. A different method of end point control for the security of DirectAccess clients is recommended.

## Multisite support for Windows 7 clients

When DirectAccess is configured in a multisite deployment, Windows 10®, Windows® 8.1, and Windows® 8 clients have the capability of connecting to the nearest site. Windows 7® client computers do not have the same capability. Site selection for Windows 7 clients is set to a particular site at the time of policy configuration, and these clients will always connect to that designated site, regardless of their location.

## User-based access control

DirectAccess policies are computer based, not user based. Specifying DirectAccess user policies to control access to the corporate network is not supported.

## Customizing DirectAccess policy

DirectAccess can be configured by using the DirectAccess Setup Wizard, the Remote Access Management console, or the Remote Access Windows PowerShell cmdlets. Using any means other than the DirectAccess Setup Wizard to configure DirectAccess, such as modifying DirectAccess Group Policy Objects directly or manually modifying the default policy settings on the server or client, is not supported. These modifications may result in an unusable configuration.

## KerbProxy authentication

When you configure a DirectAccess server with the Getting Started Wizard, the DirectAccess server is automatically configured to use KerbProxy authentication for computer and user authentication. Because of this, you should only use the Getting Started Wizard for single-site deployments where only Windows 10®, Windows 8.1, or Windows 8 clients are deployed.

In addition, the following features should not be used with KerbProxy authentication:

- Load balancing by using either an external load balancer or Windows Load Balancer
- Two-factor authentication where smart cards or a one-time password (OTP) are required

The following deployment plans are not supported if you enable KerbProxy authentication:

- Multisite.
- DirectAccess support for Windows 7 clients.
- Force tunneling. To ensure that KerbProxy authentication is not enabled when you use force tunneling, configure the following items while running the wizard:

    - Enable force tunneling
    - Enable DirectAccess for Windows 7 clients

Note

For the previous deployments, you should use the Advanced Configuration Wizard, which uses a two-tunnel configuration with a certificate-based computer and user authentication. For more information, see [Deploy a Single DirectAccess Server with Advanced Settings](single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings).

## Using ISATAP

ISATAP is a transition technology that provides IPv6 connectivity in IPv4-only corporate networks. It is limited to small- and medium-sized organizations with a single DirectAccess server deployment, and it allows remote management of DirectAccess clients. If ISATAP is deployedin a multisite, load balancing, or multidomain environment, you must remove it or move it to a native IPv6 deployment before you configure DirectAccess.

## IPHTTPS and one-time password (OTP) endpoint configuration

When you use IPHTTPS, the IPHTTPS connection must terminate on the DirectAccess server, not on any other device, such as a load balancer. Similarly, the out-of-band Secure Sockets Layer (SSL) connection that is created during one-time password (OTP) authentication must terminate on the DirectAccess server. All devices between the endpoints of these connections must be configured in pass-through mode.

## Force Tunnel with OTP authentication

Do not deploy a DirectAccess server with two-factor authentication with OTP and Force Tunneling, or OTP authentication will fail. An out-of-band Secure Sockets Layer (SSL) connection is required between the DirectAccess server and the DirectAccess client. This connection requires an exemption to send the traffic outside of the DirectAccess tunnel. In a Force Tunnel configuration, all traffic must flow through a DirectAccess tunnel, and no exemption is allowed after the tunnel is established. Because of this, it is not supported to have OTP authentication in a Forced Tunnel configuration.

## Deploying DirectAccess with a Read-Only Domain Controller

DirectAccess servers must have access to a read-write domain controller, and do not function correctly with a Read-Only Domain Controller (RODC).

A read-write domain controller is required for many reasons, including the following:

- On the DirectAccess server, a read-write domain controller is required to open the Remote Access Microsoft Management Console (MMC).
- The DirectAccess server must both read and write to the DirectAccess client and DirectAccess server Group Policy Objects (GPOs).
- The DirectAccess server reads and writes to the client GPO specifically from the Primary Domain Controller emulator (PDCe).

Because of these requirements, do not deploy DirectAccess with an RODC.