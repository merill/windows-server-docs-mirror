---
layout: Conceptual
title: Configure a Multisite Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/multisite/configure/configure-a-multisite-deployment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn about the configuration steps required to deploy a single Windows Server 2016 or Windows Server 2012 Remote Access multisite deployment.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: b350e8dd-bb71-d7f6-7b5e-52c1023aacfb
document_version_independent_id: 24c11eb1-3805-6c09-428b-c1daa3124ed1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/multisite/configure/Configure-a-Multisite-Deployment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/multisite/configure/configure-a-multisite-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/multisite/configure/Configure-a-Multisite-Deployment.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 517041d6-59f0-9985-33a2-7427c3633882
---

# Configure a Multisite Deployment | Microsoft Learn

Windows Server 2016 combines DirectAccess and Remote Access Service (RAS) VPN into a single Remote Access role. This overview provides an introduction to the configuration steps required in order to deploy a single Windows Server 2016 or Windows Server 2012 Remote Access multisite deployment.

- Step 1: [Deploy a Single DirectAccess Server with Advanced Settings](../../../directaccess/single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings). Install and configure a single Remote Access server. The multisite deployment requires you to install a single server before configuring a multisite deployment.
- [Step 2: Configure the multisite infrastructure](step-2-configure-the-multisite-infrastructure). For a multisite deployment you must configure additional Active Directory sites and domain controllers. Additional security groups and Group Policy Objects (GPOs) are also required if you are not using automatically configured GPOs.
- [Step 3: Configure the multisite deployment](step-3-configure-the-multisite-deployment)-Install the Remote Access role on additional Remote Access servers, enable the multisite deployment, and configure the additional servers as entry points for the deployment.
- [Step 4: Verify the multisite deployment](step-4-verify-the-multisite-deployment)