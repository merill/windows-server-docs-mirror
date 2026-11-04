---
layout: Conceptual
title: Install Remote Desktop Services client access licenses | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-install-cals
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to install Remote Desktop Services client access licenses (CALs), ready to license your session hosts.
ms.topic: how-to
ai-usage: ai-assisted
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-29T00:00:00.0000000Z
locale: en-us
document_id: 5a02d662-56db-4efc-52d4-61689541f632
document_version_independent_id: f8692043-d888-09d3-1bf3-bff51ae20e34
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-install-cals.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-install-cals
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-install-cals.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: 159e9f7d-c9fb-45cd-9322-0fcb5995ebcc
---

# Install Remote Desktop Services client access licenses | Microsoft Learn

Remote Desktop Services (RDS) client access licenses (CALs) are required for users to connect to your Remote Desktop environment and in compliance with licensing requirements. This article provides instructions for installing RDS CALs on your license server. Once the CALs are installed and you configure your RDS deployment to use the license server, licenses are issued to users as appropriate.

## Prerequisites

Before you begin, ensure you meet the following prerequisites:

- A Remote Desktop license server installed and activated. For activation instructions, see [Activate the Remote Desktop Services license server](rds-activate-license-server).
- Internet connectivity on a computer running Remote Desktop Licensing Manager to activate the licenses. The license server itself doesn't require internet connectivity.
- A user account that's an administrator on the Remote Desktop license server to install licenses.
- The license code or agreement number provided when you purchased your Remote Desktop Services CALs.

## Install the client access licenses

1. Open the Remote Desktop Licensing Manager.
2. Right-click the name of the license server, then select **Install licenses**.
3. On the welcome page, select **Next** .
4. Select the program you purchased your RDS CALs from, then select **Next**. If you're a service provider, select **Service Provider License Agreement**.
5. Enter the information for your license program. In most cases, you need to enter the license code or an agreement number, but it can vary depending on the license program you're using.
6. Select **Next**.
7. Select the product version, license type, and number of licenses for your environment, then select **Next**. The license manager contacts the Microsoft Clearinghouse to validate and retrieve your licenses.
8. Select **Finish** to complete the process.