---
layout: FAQ
title: Windows Admin Center frequently asked questions | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/understand/faq
summary: >
  <p>Here are answers to the most commonly asked questions about Windows Admin Center.</p>
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
description: Get answers about Windows Admin Center.
ms.topic: faq
ms.author: roharwoo
author: robinharwood
ms.localizationpriority: medium
ms.date: 2025-08-07T00:00:00.0000000Z
locale: en-us
document_id: 9509faf3-2ec5-daa3-51a4-d050f04debec
document_version_independent_id: b70c774f-8962-0e48-8294-645c03530f40
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/understand/faq.yml
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: faq
toc_rel: ../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/understand/faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/understand/faq.yml
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 46c887b8-2e30-70b7-41f9-98a079f17cc8
---

# Windows Admin Center frequently asked questions | Microsoft Learn

Here are answers to the most commonly asked questions about Windows Admin Center.

## What is Windows Admin Center?

Windows Admin Center is a lightweight, browser-based GUI platform and toolset for IT Admins to manage Windows Server and Windows client. It's the evolution of familiar in-box administrative tools, such as Server Manager and Microsoft Management Console (MMC) into a modernized, simplified, integrated, and secure experience.

## Can I use Windows Admin Center in production environments?

Yes. Windows Admin Center is generally available and ready for broad usage and production deployments. The current platform capabilities and core tools meet Microsoft's standard release criteria and our quality bar for usability, reliability, performance, accessibility, security, and adoption.

Windows Admin Center (non-preview) releases are supported continuously, based on Microsoft's [Modern Lifecycle Policy](https://support.microsoft.com/help/30881/modern-lifecycle-policy). This means that only the latest version of Windows Admin Center is serviced and supported, and users must stay current by upgrading to the latest Windows Admin Center release within 30 days of availability to remain supported. This policy applies to both the Windows Admin Center platform itself, as well as any released (non-preview) Microsoft extensions published in the Windows Admin Center extension feed. Note that some extensions may be updated more frequently than others, between Windows Admin Center releases.

For info about Windows Admin Center Preview releases, see [Windows Insider Preview releases](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver).

## How much does it cost to use Windows Admin Center?

Windows Admin Center has no additional cost beyond Windows. You can use Windows Admin Center (available as a separate download) with valid licenses of Windows Server or Windows client at no additional cost. Windows Admin Center is licensed under a Windows Supplemental End User Lisence Agreement (EULA).

## What versions of Windows Server can I manage with Windows Admin Center?

Windows Admin Center is optimized for Windows Server 2025. Although Windows Admin Center works best with Windows Server 2025, it supports managing several versions that customers already use: Windows Server 2016 and newer are fully supported. There's also limited functionality for managing Windows Server 2012.

## Can you install Windows Admin Center version 2410 when you already have an older build of Windows Admin Center installed?

Yes, you can install Windows Admin Center 2410 alongside a legacy gateway build as long as you don't choose the same ports for both installations.

## Can I change the ports my Windows Admin Center modernized gateway is using after install?

Yes, In the Program Files for Windows Admin Center, we've included a PowerShell module called `Microsoft.WindowsAdminCenter.Configuration.psm1`. This module allows you to modify your WAC configuration after installation and can be found in the **PowerShellModules** folder of your installation (`C:\Program Files\WindowsAdminCenter\PowerShellModules\` by default). To change the ports your Windows Admin Center instance is using, run the following command:

```powershell
Set-WACHttpsPort -Wacport <port> -ServicePortRangeStart <port> -ServicePortRangeEnd <port>
```

## Are there any known issues with Windows Admin Center version 2410?

Yes, there are some known issues with the modernized gateway. For a list of known issues, see our [known issues page](../support/known-issues)

## Can I change configuration settings other than port settings after install?

Yes, you can use the PowerShell module `Microsoft.WindowsAdminCenter.Configuration.psm1` to change your configuration settings. It can be found in the **PowerShellModules** folder of your installation.

## Are all the features from the 2311 release available in the 2410 release?

Yes, all the features from the 2311 release are available in the 2410 release. The 2410 release is a modernized gateway that includes a new user interface and experience, but it retains all the functionality of the previous version. [Read more about the 2311 release of Windows Admin Center.](https://aka.ms/wac2311)

## Is Windows Admin Center a complete replacement for all traditional in-box and RSAT tools?

No. Although Windows Admin Center can manage many common scenarios, it doesn't completely replace all traditional Microsoft Management Console (MMC) tools. For a detailed look at what tools are included with Windows Admin Center, read more about [managing servers](../use/manage-servers) in our documentation. Windows Admin Center has the following key capabilities in its Server Manager solution:

- Displaying resources and resource utilization
- Certificate Management
- Managing Devices
- Event Viewer
- File Explorer
- Firewall Management
- Managing Installed Apps
- Configuring Local Users and Groups
- Network Settings
- Viewing/Ending Processes and Creating Process Dumps
- Registry Editing
- Managing Scheduled tasks
- Managing Windows Services
- Enabling/Disabling Roles and Features
- Managing Hyper-V virtual machines and Virtual Switches
- Managing Storage
- Managing Storage Replica
- Managing Windows Updates
- PowerShell console
- Remote Desktop connection

Windows Admin Center also provides these solutions:

- Computer Management provides a subset of the Server Manager features for managing Windows 10 or 11 client PCs
- Failover Cluster Manager provides support for ongoing management of failover clusters and cluster resources
- Hyper-Converged Cluster Manager provides an all-new experience tailored for Storage Spaces Direct and Hyper-V. It features the Dashboard and emphasizes charts and alerts for monitoring.

Windows Admin Center is complementary to and doesn't replace Remote Server Administration Tools since roles such as Active Directory, DHCP, DNS, IIS don't yet have equivalent management capabilities in Windows Admin Center.

## Can Windows Admin Center be used to manage the free Microsoft Hyper-V Server?

Yes. Windows Admin Center can be used to manage Microsoft Hyper-V Server 2019 and Microsoft Hyper-V Server 2016.

## Can I deploy Windows Admin Center on a Windows computer?

Yes, Windows Admin Center can be installed on Windows 10 (version 1709 or later), and Windows 11. Windows Admin Center can also be installed on a server with Windows Server 2016 or greater in gateway mode, and then accessed via a web browser from a Windows 10 computer. [Learn more about installation options](../plan/installation-options).

## I heard that Windows Admin Center uses PowerShell under the hood, can I see the actual scripts that it uses?

Yes! [View PowerShell scripts used in Windows Admin Center](../use/get-started#view-powershell-scripts-used-in-windows-admin-center).

## Are there any plans for Windows Admin Center to manage Windows Server 2008 R2 or earlier?

Windows Admin Center **no longer supports** functionality to manage Windows Server 2008 R2. Windows Admin Center relies on PowerShell capabilities and platform technologies that don't exist in Windows Server 2008 R2 and earlier, making full support infeasible. If you haven't yet, Microsoft recommends [moving to Azure or upgrading to the latest version of Windows Server](https://www.microsoft.com/cloud-platform/windows-server-2008).

## Are there any plans for Windows Admin Center to manage Linux connections?

We're investigating due to customer demand, but there's currently no locked plan to deliver, and support may consist only of a console connection over SSH.

## Which web browsers does Windows Admin Center support?

The latest versions of Microsoft Edge (Windows 10, version 1709 or later), Google Chrome, and [Microsoft Edge Insider](https://microsoftedgeinsider.com) are tested and supported on Windows 10 and later. [View browser specific known issues](../support/known-issues#browser-specific-issues). Other modern web browsers or other platforms aren't currently part of our test matrix and are therefore not *officially* supported.

## How does Windows Admin Center handle security?

Traffic from the browser to the Windows Admin Center gateway uses HTTPS. Traffic from the gateway to managed servers is standard PowerShell and WMI over WinRM. We support LAPS (Local Administrator Password Solution), resource-based constrained delegation, gateway access control using Active Directory or Microsoft Entra ID, and role-based access control for managing target servers.

## Does Windows Admin Center use CredSSP?

Yes, in a few cases Windows Admin Center requires CredSSP. CredSSP is required to pass your credentials for authentication to machines beyond the specific server you're targeting for management. For example, if you're managing virtual machines on **server B**, but want to store the vhdx files for those virtual machines on a file share hosted by **server C**, Windows Admin Center must use CredSSP to authenticate with **server C** to access the file share.

Windows Admin Center handles the configuration of CredSSP automatically after prompting for consent from you. Before configuring CredSSP, Windows Admin Center checks to make sure that the system has the recent CredSSP [updates](https://support.microsoft.com/help/4093492/credssp-updates-for-cve-2018-0886-march-13-2018).

CredSSP is currently used in the following areas:

- Using disaggregated SMB storage in the virtual machines tool
- Using the Updates tool in either the Failover or Hyper-Converged cluster management solutions, which performs [Cluster-Aware Updating](../../../failover-clustering/cluster-aware-updating)

## Are there any cloud dependencies?

Windows Admin Center doesn't require internet access and doesn't require Microsoft Azure. Windows Admin Center manages Windows Server and Windows instances anywhere: on physical systems, or in virtual machines on any hypervisor, or running in any cloud. Although Windows Admin Center integrates with various Azure services, these features are optional and not a requirement to use Windows Admin Center. Connections to Azure based resources **do** require an active and functional internet/network connection, in order to enforce administrative changes and view statuses.

## Are there any other dependencies or prerequisites?

Windows Admin Center can be installed on Windows 10 Fall Anniversary Update (1709) or newer, or Windows Server 2016 or newer. To manage Windows Server 2008 R2, 2012, or 2012 R2, installation of Windows Management Framework 5.1 is required on those servers. There are no other dependencies. IIS, agents, and SQL Server are all not required.

## What about extensibility and 3rd-party support?

Windows Admin Center has an SDK available so that anyone can write their own extension. As a platform, growing our ecosystem and enabling partner extensibility has been a key priority since the beginning. [Read more about the Windows Admin Center SDK](../extend/extensibility-overview).

## Can I manage Hyper-Converged Infrastructure with Windows Admin Center?

Yes. Windows Admin Center supports the management of hyper-converged clusters running Windows Server 2016 or Windows Server 2019. The hyper-converged cluster manager solution in Windows Admin Center was previously in preview but is now **generally available**, with some new functionality in preview. For more information, [read more about managing hyper-converged infrastructure](../use/manage-hyper-converged).

## Does Windows Admin Center require System Center?

No. Windows Admin Center is complementary to System Center, but System Center isn't required. [Read more about Windows Admin Center and System Center](related-management#system-center).

## Can Windows Admin Center replace System Center Virtual Machine Manager (SCVMM)?

Windows Admin Center and SCVMM are complementary; Windows Admin Center is intended to replace the traditional Microsoft Management Console (MMC) snap-ins and the server admin experience. Windows Admin Center isn't intended to replace the monitoring aspects of SCVMM. [Read more about Windows Admin Center and System Center](related-management#system-center).

## What is Windows Admin Center Preview, which version is right for me?

There are two versions of Windows Admin Center available for download:

### Windows Admin Center

- For IT admins who aren't able to update frequently or who want more validation time for the releases they use in production, this version is for you. Our current generally available (GA) release is Windows Admin Center 1910.
- Windows Admin Center (non-preview) releases are supported continuously, based on Microsoft's [Modern Lifecycle Policy](https://support.microsoft.com/help/30881/modern-lifecycle-policy). This means that only the latest version of Windows Admin Center is serviced and supported, and users must stay current by upgrading to the latest Windows Admin Center release within 30 days of availability to remain supported. This policy applies to both the Windows Admin Center platform itself, as well as any released (non-preview) Microsoft extensions published in the Windows Admin Center extension feed. Note that some extensions may be updated more frequently than others, between Windows Admin Center releases.For info about Windows Admin Center Preview releases, see [Windows Insider Preview releases](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver).
- To get the latest release, [download here](https://aka.ms/WACDownload).

### Windows Admin Center Preview

- For IT admins who want the latest and greatest features on a regular cadence, this version is for you. Our intent is to provide subsequent update releases every month or so. The core platform continues to be production-ready and the license provides production use rights. These builds introduce new tools and capabilities that are clearly marked as PREVIEW and are suitable for evaluation and testing.
- To get the latest Insider Preview release, registered Insiders may download Windows Admin Center Preview directly from the [Windows Server Insider Preview download page](https://microsoft.com/en-us/software-download/windowsinsiderpreviewserver), under the Additional Downloads dropdown. If you haven't registered as an Insider, see [Getting Started with Windows Server](https://insider.windows.com/en-us/for-business-getting-started-server/) on the Windows Insiders for Business portal.

## Why was "Windows Admin Center" chosen as the final name for "Project Honolulu"?

Windows Admin Center is the official product name for "Project Honolulu" and reinforces our vision of an integrated experience for IT admins across a breadth of core administrative and management scenarios. It also highlights our customer-focus on IT admin user needs as central to how we invest and what we deliver.

## Where can I learn more about Windows Admin Center or get more details?

Our [launch page](../overview) is the best starting point and has links to our newly categorized documentation content, download location, how to provide feedback, reference information, and other resources.

## What is the version history of Windows Admin Center?

[View the version history here.](../support/release-history)

## I'm having an issue with Windows Admin Center, where can I get help?

See our [troubleshooting guide](../support/troubleshooting) and our list of [known issues](../support/known-issues).