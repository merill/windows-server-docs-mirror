---
layout: Conceptual
title: Upgrade Remote Desktop Services deployments | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/upgrade-to-rds
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn about which Remote Desktop Services versions can be upgraded and the order to upgrade your Remote Desktop role services.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: upgrade-and-migration-article
author: robinharwood
locale: en-us
document_id: 00a9ca95-807e-ea10-53e6-b6ba905e8cc6
document_version_independent_id: 931b0116-ac24-d404-182a-24253cd2d9fe
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/upgrade-to-rds.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/upgrade-to-rds
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/upgrade-to-rds.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: 6da594fc-72ca-9533-c207-d510f56f8970
---

# Upgrade Remote Desktop Services deployments | Microsoft Learn

In this article, learn about which Remote Desktop Services (RDS) versions can be upgraded and the order to upgrade your Remote Desktop (RD) role services.

## Supported OS upgrades with RDS role installed

You can upgrade to a newer version of Windows Server by two versions at a time. For example, you can upgrade to Windows Server 2025 from Windows Server 2019.

## Flow for deployment upgrades

In order to keep the downtime to a minimum, use the following guide:

1. **RD Connection Broker servers** should be upgraded first. If you have an active/active configuration, remove all but one server from the deployment and perform an in-place upgrade. Perform upgrades on the remaining RD Connection Broker servers offline and then reapply them to the deployment. The deployment isn't available during the RD Connection Broker servers' upgrade.

    Note

    It's mandatory to upgrade all RD Connection Broker servers. Windows Server RD Connection Broker servers in a mixed deployment are not supported. Once the RD Connection Broker server(s) are running a new Windows Server version, the deployment remains functional, even if the rest of the servers in the deployment are still running the previous version.
2. **RD License servers** should be upgraded before you upgrade your RD Session Host servers.

    Note

    RD license servers from an older version of Windows Server work with newer versions, but they can only process client access licenses (CALs) from the older Windows Server version. They can't use the newer Windows Server CALs. For more information about RD license servers, see [RDS CAL version compatibility](rds-client-access-license#rds-cal-version-compatibility).
3. **RD Session Host servers** can be upgraded next. Avoid downtime during upgrade by splitting the servers to be upgraded into steps as detailed. All will be functional after the upgrade. To upgrade, use the steps described in [Upgrading your Remote Desktop Session Host to the latest Windows Server version](upgrade-to-rdsh).
4. **RD Virtualization Host servers** can be upgraded next. To upgrade, use the steps described in [Upgrading your Remote Desktop Virtualization Host to the latest Windows Server version](upgrade-to-rdvh).
5. **RD Web Access servers** can be upgraded anytime.

    Note

    - Upgrading RD Web might reset Internet Information Services (IIS) properties, such as any configuration files. To not lose your changes, make notes or copies of customizations done to the RD Web site in IIS.
    - RD Web Access servers from an older version of Windows Server work with newer versions.
6. **RD Gateway servers** can be upgraded anytime.

    Note

    - Windows Server 2016 and later doesn't include Network Access Protection (NAP) policies—they have to be removed. The easiest way to remove the correct policies is by running the upgrade wizard. If there are any NAP policies you must delete, the upgrade blocks and creates a text file on the desktop that includes the specific policies. To manage NAP policies, open the Network Policy Server tool. After deleting them, select **Refresh** in the Setup tool to continue with the upgrade process.
    - RD Gateway servers from an older version of Windows Server work with newer versions.

## VDI deployment – supported guest OS upgrade

Administrators have the following options to upgrade VM collections:

### Upgrade managed shared VM collections

Administrators need to create VM templates with the desired OS version and use it to patch all the VMs in the pool.

Windows 10 can be patched to Windows 11.

### Upgrade unmanaged shared VM collections

End users can't upgrade their personal desktops. Administrators should perform the upgrade. The exact steps are to be determined.

## Known issues

**Issue:** If the RD deployment has the RD Web Access (RDWA) Role already installed and has been upgraded from a previous windows installation, a new upgrade might fail. For example, if the deployment containing RDWA upgraded from Server 2012 R2 to Server 2019, another upgrade to Server 2022 might encounter a failure.

**Workaround:** Before migrating for the second time, check if the following registry key is present: `HKLM\SOFTWARE\Microsoft\Terminal Server Web Access\IsInstalled`

If it isn't present, open an elevated PowerShell prompt, then run the following commands:

```powershell
$registryPath = "HKLM:SOFTWARE\Microsoft\Terminal Server Web Access\IsInstalled"
New-Item -Path $registryPath
New-ItemProperty -Path $registryPath -Name Version -PropertyType String -Value "6.0"
```