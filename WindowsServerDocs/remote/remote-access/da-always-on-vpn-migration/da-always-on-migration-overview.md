---
layout: Conceptual
title: Remote Access Always On VPN migration overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/da-always-on-vpn-migration/da-always-on-migration-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Always On VPN addresses the previous gaps between Windows VPNs and DirectAccess, and how to migrate from DirectAccess to Always On VPN.
ms.topic: upgrade-and-migration-article
ms.author: roharwoo
author: robinharwood
ms.date: 2018-05-29T00:00:00.0000000Z
locale: en-us
document_id: 229c4927-d4cf-3400-2558-94246d22b3c8
document_version_independent_id: 3e0da1c0-7dc3-d902-2ec0-aff3c46b381c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/da-always-on-vpn-migration/da-always-on-migration-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/da-always-on-vpn-migration/da-always-on-migration-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/da-always-on-vpn-migration/da-always-on-migration-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 817b69c4-a03f-bc86-311a-d22f6b03842b
---

# Remote Access Always On VPN migration overview | Microsoft Learn

» [**Next:** Plan the DirectAccess to Always On VPN migration](da-always-on-migration-planning)

In previous versions of the Windows VPN architecture, platform limitations made it difficult to provide the critical functionality needed to replace DirectAccess, such as automatic connections initiated before users sign in. Always On VPN, however, has mitigated most of those limitations or expanded the VPN functionality beyond the capabilities of DirectAccess. Always On VPN addresses the previous gaps between Windows VPNs and DirectAccess.

The DirectAccess–to–Always On VPN migration process consists of four primary components and high-level processes:

1. **Plan the Always On VPN migration.** Planning helps identify target clients for user phase separation as well as infrastructure and functionality.

    1. **Build migration rings.** As in most other system migrations, target client migrations in phases to help identify any issues before they affect the entire organization. The first part of Always On VPN migration is no different.
    2. **[Learn about the feature comparison of Always On VPN and DirectAccess](../vpn/vpn-map-da).** Similar to DirectAccess, Always On VPN has many security, connectivity, authentication, and other options.
    3. **[Learn about the feature enhancements of Always On VPN](../vpn/always-on-vpn/always-on-vpn-enhancements).** Discover new or improved features that Always On VPN offers to improve your configuration.
    4. **[Learn about the Always On VPN technology](../vpn/always-on-vpn/always-on-vpn-technology-overview).** For this deployment, you must install a new Remote Access server that is running Windows Server 2016, as well as modify some of your existing infrastructure for the deployment.
2. **Deploy a side-by-side VPN infrastructure.** After you have determined your migration phases and the features you want to include in your deployment, you deploy the Always On VPN infrastructure side by side with the existing DirectAccess infrastructure.
3. **Deploy certificates and configuration to the clients.** Once the VPN infrastructure is ready, you create and publish the required certificates to the client. When the clients have received the certificates, you deploy the VPN\_Profile.ps1 configuration script. Alternatively, you can use Intune to configure the VPN client. Use Microsoft Endpoint Configuration Manager or Microsoft Intune to monitor for successful VPN configuration deployments.
4. **Remove and decommission.** Properly decommission the environment after you have migrated everyone off DirectAccess.

    1. **Remove the DirectAccess configuration from the client.** Monitor Microsoft Endpoint Configuration Manager or Microsoft Intune for successful VPN configuration deployments. Then, use reporting to determine device-assignment information and discover which device belongs to each user. As users migrate successfully, you remove their devices from the DirectAccess security group so that you can remove DirectAccess from your environment.
    2. **Decommission the DirectAccess server.** When you have successfully removed the configuration settings and DNS records, you are ready to tear down the DirectAccess server. To do so, either remove the role in Server Manager or decommission the server and remove it from AD DS.

## DirectAccess deployment scenario

In this deployment scenario, you use a simple DirectAccess deployment scenario as a starting point for the migration this guide presents. You do not need to match this deployment scenario before migrating to Always On VPN, but for many organizations, this simple setup is an accurate representation of their current DirectAccess deployment. The table below provides a list of basic features for this setup.

Many DirectAccess deployment scenarios and options exist, so your implementation is likely to be different from the one described here. If so, refer to [Feature mapping between DirectAccess and Always On VPN](../vpn/vpn-map-da) to determine the Always On VPN feature set mapping for your current additions, and then add those features to your configuration. Also, you can refer to the [Always On VPN enhancements](../vpn/always-on-vpn/always-on-vpn-enhancements) to add options to your Always On VPN deployment.

Note

For nondomain-joined devices, there are additional considerations, such as certificate enrollment. For details, see [Always On VPN Deployment for Windows Server and Windows 10](../vpn/always-on-vpn/deploy/always-on-vpn-deploy-deployment).

### Deployment scenario feature list

| DirectAccess feature | Typical scenario |
| --- | --- |
| Deployment scenario | Deploy full DirectAccess for client access and remote management |
| Network adapters | 2 |
| User authentication | Active Directory credentials |
| Use computer certificates | Yes |
| Security groups | Yes |
| Single DirectAccess server | Yes |
| Network topology | Network address translation (NAT) behind an edge firewall with two network adapters |
| Access mode | End to edge |
| Tunneling | Split tunnel |
| Authentication | Standard public key infrastructure (PKI) authentication with machine certificate plus Kerberos (not KerbProxy) |
| Protocols | IP over HTTPS (IP-HTTPS) |
| Network location server (NLS) off-box | Yes |

## Always On VPN deployment scenario

In this deployment scenario, you focus on migrating a simple DirectAccess environment to a simple Always On VPN environment, which is the DirectAccess replacement solution. The following table provides the features used in this simple solution. For more detailed information about additional enhancements to the Always On VPN client, see [Always On VPN enhancements](../vpn/always-on-vpn/always-on-vpn-enhancements).

### Always On VPN features used in the simple environment

| VPN feature | Deployment scenario configuration |
| --- | --- |
| Connection type | Native Internet Key Exchange version 2 (IKEv2) |
| Network adapters | 2 |
| User authentication | Active Directory credentials |
| Use computer certificates | Yes |
| Routing | Split Tunneling |
| Name resolution | Domain name information list and Domain Name System (DNS) suffix |
| Triggering | Always on and trusted network detection |
| Authentication | Protected Extensible Authentication Protocol-Transport Layer Security (PEAP-TLS) with Trusted Platform Module–protected user certificates |