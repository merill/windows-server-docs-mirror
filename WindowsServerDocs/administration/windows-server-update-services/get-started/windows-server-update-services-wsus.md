---
layout: Conceptual
title: Windows Server Update Services (WSUS) Overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: wsus
ms.update-cycle: 1095-days
description: See an overview of the Windows Server Update Service (WSUS) Server role, including its features, applications, and support for Unified Update Platform (UUP).
ms.topic: overview
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-02T00:00:00.0000000Z
locale: en-us
document_id: 2b79ce4d-52b9-5193-df08-c40fa663da58
document_version_independent_id: a5215c06-f761-3141-4eb4-71ae00b2c8aa
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-server-update-services/get-started/windows-server-update-services-wsus.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-server-update-services/get-started/windows-server-update-services-wsus
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-server-update-services/get-started/windows-server-update-services-wsus.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 259c4855-c1a1-9505-bdd5-8c031c9624ef
---

# Windows Server Update Services (WSUS) Overview | Microsoft Learn

Windows Server Update Services (WSUS) provides a way for IT administrators to deploy the latest Microsoft product updates. You can use WSUS to fully manage the distribution of updates that are released through Microsoft Update to computers on your network. This article provides an overview of this server role and more information about how to deploy and maintain WSUS.

Note

WSUS is deprecated and is no longer adding new features. However, it continues to be supported for production deployments, and receives security and quality updates as per the product lifecycle. For more info, see [Features removed or no longer developed in Windows Server](../../../get-started/removed-deprecated-features-windows-server).

## WSUS Server role description

A WSUS server provides features that you can use to manage and distribute updates through a management console. A WSUS server can also be the update source for other WSUS servers within the organization. The WSUS server that acts as an update source is called an upstream server. In a WSUS implementation, at least one WSUS server on your network must be able to connect to Microsoft Update to get available update information. As an administrator, you can determine, based on network security and configuration, how many other WSUS servers connect directly to Microsoft Update.

WSUS includes the following features:

- Windows PowerShell cmdlets to manage the most important administrative tasks in WSUS.
- Secure hash algorithm 256-bit (SHA-256) capability for extra security.
- Client and server separation: versions of the Windows Update Agent (WUA) can be deployed independently of WSUS.

## Practical applications

Update management is the process of controlling the deployment and maintenance of interim software releases into production environments. It helps you maintain operational efficiency, overcome security vulnerabilities, and maintain the stability of your production environment. Maintaining a known level of trust within your organization's operating systems and application software helps you avoid security vulnerabilities that, if exploited, can lead to a loss of revenue and intellectual property. Minimizing this threat requires you to properly configure systems, use the latest software, and install the recommended software updates.

The core scenarios where WSUS adds value to your business are:

- Centralized update management
- Update management automation

### Use Windows PowerShell to manage WSUS

For system administrators to automate their operations, they need coverage through command-line automation. The main goal is to facilitate WSUS administration by providing a way for system administrators to automate their day-to-day operations. Bringing core WSUS operations to Windows PowerShell helps administrators increase productivity, reduce the learning curve for new tools, and increase consistency across similar operations. The Windows PowerShell cmdlets for WSUS operations add flexibility and agility for the system administrator.

## Unified Update Platform

Beginning March 28, 2023, WSUS supports Unified Update Platform (UUP) updates for Windows 11 version 21H2 clients. For more information, see [Plan your WSUS deployment](../plan/plan-your-wsus-deployment).

Important

This change requires either an update installation or the manual addition of Multipurpose Internet Mail Extensions (MIME) types to Internet Information Services (IIS) on WSUS servers. Clients using Windows 11 version 22H2 might fail to install updates from WSUS if the server isn't updated. For more information, see [UUP considerations](../plan/plan-your-wsus-deployment#uup-considerations).