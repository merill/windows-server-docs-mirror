---
layout: Conceptual
title: Step 2 Plan the DirectAccess Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/add-to-existing-vpn/step-2-plan-da-davpn
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to plan the settings for the Enable DirectAccesss Wizard.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 48201950-8772-e7be-a89d-c1c3c83aa900
document_version_independent_id: 0cb39d5a-bbac-1719-8f9e-c3211e89414a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/add-to-existing-vpn/step-2-plan-da-davpn.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/add-to-existing-vpn/step-2-plan-da-davpn
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/add-to-existing-vpn/step-2-plan-da-davpn.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
platformId: df7cddd3-dca7-81d7-f058-03e5a975fec2
---

# Step 2 Plan the DirectAccess Deployment | Microsoft Learn

After planning the Remote Access infrastructure, the next step in enabling DirectAccess is to plan the settings for the Enable DirectAccesss Wizard.

| Task | Description |
| --- | --- |
| Planning for client deployment | Plan how to allow client computers to connect using DirectAccess. Decide which managed computers will be configured as DirectAccess clients. |
| Planning for Remote Access server deployment | Plan how to deploy the Remote Access server. |

## Planning for client deployment

There are two decisions to make when planning your client deployment:

- Will DirectAccess be available to mobile computers only, or to any computer?

    When you configure DirectAccess clients in the Enable DirectAccess wizard, you can choose to allow only mobile computers in the specified security groups to connect using DirectAccess. If you restrict access to mobile computers, Remote Access automatically configures a WMI filter to ensure that the DirectAccess client GPO is applied only to mobile computers in the specified security groups. The Remote Access administrator requires permissions to create or modify group policy WMI filters to enable this setting.
- What security groups will contain the DirectAccess client computers?

    DirectAccess settings are contained in the DirectAccess client GPO. The GPO is applied to computers that are part of the security groups that you specify in the Enable DirectAccess wizard. You can specify security groups contained in any supported domain. Before you configure Remote Access, the security groups should be created. You can add computers to the security group after completing the Remote Access deployment, but note that if you add client computers that reside in a different domain to the security group, the client GPO will not be applied to these clients. For example, if you created SG1 in domain A for DirectAccess clients, and later add clients from domain B to this group, the client GPO will not be applied to clients in domain B. To avoid this issue, create a new client security group for each domain that contains client computers. Alternatively, if you do not want to create a new security group, run the Add-DAClient cmdlet with the name of the new GPO for the new domain.

## Planning for Remote Access server deployment

There are a number of decisions to make when planning to deploy your Remote Access server:

- **Network topology**-There are two topologies available when deploying a Remote Access server:

    - **Two adapters**-With two network adapters, Remote Access can be configured with one network adapter connected directly to the Internet, and the other is connected to the internal network. Or alternatively the server is installed behind an edge device such as a firewall or a router. In this configuration one network adapter is connected to the perimeter network, the other is connected to the internal network.
    - **Single network adapter**-In this configuration the Remote Access server is installed behind an edge device such as a firewall or a router. The network adapter is connected to the internal network.
- **Network adapters**-The Enable DirectAccess wizard automatically detects the network adapters configured on the Remote Access server, based on the interfaces used by VPN. You must make sure that the correct adapters are selected.
- **ConnectTo address**-Client computers use the ConnectTo address in order to connect to the Remote Access server. The address that you choose must match the subject name of the IP-HTTPS certificate that you deploy for the IP-HTTPS connection and must be available in the public DNS. See Planning website certificates for IP-HTTPS.
- **IP-HTTPS certificate**-If SSTP VPN is configured, the Enable DirectAccess wizard picks up the certificate used by SSTP for IP-HTTPS. If SSTP VPN is not configured, the wizard will try to see if a certificate for IP-HTTPS has been configured. If not, it will automatically provision self-signed certificates for IP-HTTPS.The wizard automatically enables Kerberos authentication. The wizard will also enable NAT64 and DNS64 for protocol translation in the IPv4-only environment.
- **IPv6 prefixes**-If the wizard detects that IPv6 has been deployed on the network adapters, it automatically creates IPv6 prefixes for the internal network, an IPv6 prefix to assign to DirectAccess client computers, and an IPv6 prefix to assign to VPN client computers. If the automatically generated prefixes are not correct for your native IPv6 or ISATAP infrastructure, you must manually change them. See 1.1 Planning network and server topology and settings.
- **Windows 7 clients**-By default, Windows 7 client computers cannot connect to a Windows Server 2012 Remote Access deployment. If you have Windows 7 client computers in your organization that require remote access to internal resources, you can allow them to connect. Any client computers that you want to allow to access internal resources must be a member of a security group that you specify in the Enable DirectAccess wizard.

    Note

    Allowing Windows 7 client computers to connect using DirectAccess requires you to use computer certificate authentication.
- **Authentication**-The Enable DirectAccess wizard uses Active Directory to authenticate the user credentials. To deploy two-factor authentication, see [Deploy Remote Access with OTP authentication](../../ras/otp/deploy-ra-otp).