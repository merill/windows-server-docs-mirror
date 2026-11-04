---
layout: Conceptual
title: Upgrade and migrate roles and features in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/upgrade-migrate-roles-features
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: Upgrade Windows Server with confidence. Learn about supported upgrade paths, and migration tools for a smooth transition.
ms.topic: upgrade-and-migration-article
author: robinharwood
ms.author: roharwoo
ms.date: 2026-04-27T00:00:00.0000000Z
locale: en-us
document_id: f48066ff-c9cd-a1f3-c3f8-fcea3e14f2fe
document_version_independent_id: 8255216f-edca-aeb1-b27a-28373b8bb724
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/upgrade-migrate-roles-features.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/upgrade-migrate-roles-features
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/upgrade-migrate-roles-features.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ad813468-c0fb-809c-1cad-f61cfb75be38
---

# Upgrade and migrate roles and features in Windows Server | Microsoft Learn

Upgrading or migrating roles and features in Windows Server is essential for maintaining security, performance, and supportability. This article provides an overview which roles and features can be upgraded in-place or migrated to a new server. It also provides links to detailed migration guides for each role and feature, as well as information about the Windows Server Migration Tools and Storage Migration Service. Use this information to plan a smooth transition to newer versions of Windows Server, minimize downtime, and ensure continued reliability for your workloads.

You can update roles and features to later versions of Windows Server in two ways:

- **Migration:** Move roles and features to a new server running the newer version of Windows Server.
- **In-place upgrade:** Install the new version of Windows Server over the existing one, keeping roles and features in place.

Some roles and features support both methods, while others might only support migration.

You can migrate many roles and features by using Windows Server Migration Tools. This feature is built into Windows Server and helps you move roles and features to a new server. For file servers and storage, use the [Storage Migration Service](../storage/storage-migration-service/overview).

The migration guides support migrations of specified roles and features from one server to another (not in-place upgrades). Unless the guides say otherwise, you can migrate between physical and virtual computers. You can also migrate between Windows Server installations that use either Server with Desktop Experience or Server Core.

Important

Before you begin migrating roles and features, verify that both source and destination servers are running the most current updates that are available for their operating systems.

Before migrating or upgrading to a new version of Windows Server, review the [support lifecycle policy](https://support.microsoft.com/lifecycle) for that version. Make sure you understand how long it's supported. You can [search for lifecycle information](https://support.microsoft.com/lifecycle) for the specific Windows Server release you plan to use.

## Windows Server Migration Tools

Windows Server Migration Tools enables you to migrate server roles, features, operating system settings, and other data and shares to servers, including later versions of Windows Server. It's a feature of Windows Server and so it's easily installed using the Add Roles and Features wizard, or PowerShell. Learn more about how to [install, use, and remove Windows Server Migration Tools](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj134202%28v=ws.11%29).

Note

Cross-subnet migrations using Windows Server Migration Tools is available with Windows Server 2012 and later releases. Previous versions of Windows Server Migration Tools only support migrations in the same subnet.

## Upgrade and migration matrix

| Server Role | Upgradeable in-place? | Migration Supported? | Can migration be completed without downtime? |
| --- | --- | --- | --- |
| Active Directory Certificate Services | Yes | [Yes](../identity/ad-cs/migrate-certification-authority) | No |
| Active Directory Domain Services | [Not recommended](/en-us/windows-server/identity/ad-ds/deploy/upgrade-domain-controllers). Use clean OS install to get AD performance and feature improvements. | [Yes](/en-us/windows-server/identity/ad-ds/deploy/upgrade-domain-controllers) | Yes |
| Active Directory Federation Services | No | Yes | No (new nodes need to be added to the farm) |
| Active Directory Lightweight Directory Services | Yes | Yes | Yes |
| Active Directory Rights Management Services | Yes | [Yes](../identity/ad-rms/adrms-deploy) | No |
| DHCP Server | Yes | Yes | Yes |
| DNS Server | Yes | Yes | No |
| Failover Clustering | Yes with [Cluster OS Rolling Upgrade](../failover-clustering/cluster-operating-system-rolling-upgrade) or when the server is removed by the cluster for upgrade and then added to a different cluster. | Yes | Yes for Failover Clusters with Hyper-V VMs or Failover Clusters running the Scale-out File Server role. See [Cluster OS Rolling Upgrade](../failover-clustering/cluster-operating-system-rolling-upgrade). |
| File and Storage Services | Yes | Varies by subfeature | No |
| Hyper-V | Yes with [Cluster OS Rolling Upgrade](../failover-clustering/cluster-operating-system-rolling-upgrade) process | Yes | Yes for Failover Clusters with Hyper-V VMs or Failover Clusters running the Scale-out File Server role. See [Cluster OS Rolling Upgrade](../failover-clustering/cluster-operating-system-rolling-upgrade). |
| Print and Fax Services | No | Yes (using `Printbrm.exe`) | No |
| Remote Desktop Services | Yes, for all subroles, but mixed mode farm isn't supported | [Yes](../remote/remote-desktop-services/migrate-rds-role-services) | No |
| Web Server (IIS) | Yes | Yes | No |
| Windows Server Essentials Experience | Yes | Yes | No |
| Windows Server Update Services | Yes | [Yes](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh852339%28v=ws.11%29) | No |
| Work Folders | Yes | Yes | Yes with [Cluster OS Rolling Upgrade](../failover-clustering/cluster-operating-system-rolling-upgrade) process. |

## Migration guides

Below you can find links to migration guides for specific Windows Roles and Features.

### Active Directory

- [Migrate the Certification Authority](../identity/ad-cs/migrate-certification-authority)
- [Migrate Active Directory Federation Services Role Service](/en-us/previous-versions/windows-server/it-pro/windows-server-2012/identity/ad-fs/deployment/migrate-ad-fs-service-role-to-windows-server-r2)
- [Upgrading AD RMS to Windows Server 2016](../identity/ad-rms/adrms-deploy)
- [Upgrade domain controllers to a newer version of Windows Server](/en-us/windows-server/identity/ad-ds/deploy/upgrade-domain-controllers)
- [Active Directory Domain Services and Domain Name System (DNS) Server Migration Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379558%28v=ws.10%29)

### BranchCache

- [BranchCache Migration Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd548365%28v=ws.10%29)

### DHCP

- [Migrate DHCP Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn495425%28v=ws.11%29)
- [Migrate existing DHCP failover deployment](../networking/technologies/dhcp/migrate-existing-dhcp-failover)

### Failover Clustering

- [Upgrade a Windows Server failover cluster with a cluster OS rolling upgrade](../failover-clustering/cluster-operating-system-rolling-upgrade)
- [Upgrading Failover Clusters on the same hardware](../failover-clustering/upgrade-option-same-hardware)
- [Migrate Cluster Roles](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn530779%28v=ws.11%29)
- [Migrate Clustered Services and Applications to Windows Server 2012](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn486790%28v=ws.11%29)

### File and Storage Services

- [Storage Migration Service](../storage/storage-migration-service/overview)
- [Migrate File and Storage Services](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn479292%28v=ws.11%29)
- [Upgrade a Storage Spaces Direct cluster](../storage/storage-spaces/upgrade-storage-spaces-direct)

### Hyper-V

- [Migrate Hyper-V](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn486799%28v=ws.11%29)
- [Upgrade virtual machine version in Hyper-V on Windows or Windows Server](../virtualization/hyper-v/deploy/upgrade-virtual-machine-version-in-hyper-v-on-windows-or-windows-server)

### Network Policy Server

- [Migrate Network Policy Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831652%28v=ws.11%29)
- [Migrate Health Registration Authority](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831513%28v=ws.11%29)

### Print and Document Services

- [Migrate Print and Document Services](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj134150%28v=ws.11%29)

### Remote Desktop Services

- [Migrate Remote Desktop Services](../remote/remote-desktop-services/migrate-rds-role-services)
- [Migrate your Remote Desktop Services Client Access Licenses (RDS CALs)](../remote/remote-desktop-services/migrate-rds-cals)

### Routing and Remote Access

- [Overview of the DirectAccess to Always On VPN migration](../remote/remote-access/da-always-on-vpn-migration/da-always-on-migration-overview)
- [RRAS Migration Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee822825%28v=ws.10%29)

### Web Server (IIS)

- [Web Server (IIS)](https://www.iis.net/downloads/microsoft/web-deploy)

### Windows Server Update Services

- [Migrate Windows Server Update Services to Windows Server 2012 R2](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh852339%28v=ws.11%29)

## Other Windows migration guides

- [Local User and Group Migration Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379531%28v=ws.10%29)
- [IP Configuration Migration Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd379537%28v=ws.10%29)