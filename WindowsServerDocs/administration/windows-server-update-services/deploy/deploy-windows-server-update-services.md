---
layout: Conceptual
title: Deploy Windows Server Update Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-server-update-services/deploy/deploy-windows-server-update-services
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: wsus
ms.update-cycle: 1095-days
description: Windows Server Update Service (WSUS) topic - An overview of the deployment process with links to the four steps to accomplish it
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 3a1f8511-29e8-48ff-601c-fe5ccfc1eba3
document_version_independent_id: d05b5d1e-ad9e-87a6-1929-933f9bada2c5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-server-update-services/deploy/deploy-windows-server-update-services.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-server-update-services/deploy/deploy-windows-server-update-services
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-server-update-services/deploy/deploy-windows-server-update-services.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: 007ae93c-0a8b-d6e8-f728-89f9be473304
---

# Deploy Windows Server Update Services | Microsoft Learn

Windows Server Update Services (WSUS) enables information technology administrators to deploy the latest Microsoft product updates. WSUS is a Windows Server server role that can be installed to manage and distribute updates. A WSUS server can be the update source for other WSUS servers within the organization. The WSUS server that acts as an update source is called an upstream server.

In a WSUS implementation, at least one WSUS server in the network must connect to Microsoft Update to get available update information. You can determine, based on network security and configuration, how many other servers connect directly to Microsoft Update.

This guide provides conceptual information for planning and deploying Windows Server Update Service.

- [Plan your WSUS deployment](../plan/plan-your-wsus-deployment)
- [Step 1: Install the WSUS Server Role](1-install-the-wsus-server-role)
- [Step 2: Configure WSUS](2-configure-wsus)
- [Step 3: Approve and Deploy Updates in WSUS](3-approve-and-deploy-updates-in-wsus)
- [Step 4: Configure Group Policy Settings for Automatic Updates](4-configure-group-policy-settings-for-automatic-updates)