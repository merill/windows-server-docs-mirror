---
layout: Conceptual
title: Plan to Enable DirectAccess | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/add-to-existing-vpn/plan-to-enable-directaccess
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn about DirectAccess infrastructure and DirectAccess deployment for Windows Server 2016.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 599115de-1d77-a5c8-5b70-f1f36e2f5ee6
document_version_independent_id: 4283ad22-b702-f5c4-441d-d5a68fbae40b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/add-to-existing-vpn/Plan-to-Enable-DirectAccess.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/add-to-existing-vpn/plan-to-enable-directaccess
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/add-to-existing-vpn/Plan-to-Enable-DirectAccess.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b1acb238-648e-deff-ad36-23c088568e34
---

# Plan to Enable DirectAccess | Microsoft Learn

**Note:** Windows Server 2012 combines DirectAccess and Remote Access Service (RAS) into a single Remote Access role. This section describes the planning steps that are required to deploy a single Remote Access server running Windows Server 2016 with basic features.

The planning phase includes the following steps:

- [Step 1: Plan DirectAccess infrastructure](step-1-plan-da-inf-davpn)

    In this phase, you describe the planning that is required to set up the network infrastructure before you begin the Remote Access deployment. It includes planning for the network and server topology, certificates, Domain Name System (DNS), Active Directory and Group Policy Object (GPO) configuration, and the DirectAccess network location server.
- [Step 2: Plan DirectAccess deployment](step-2-plan-da-davpn)

    In this phase, you describe the planning steps that are required to prepare for the Remote Access deployment. It includes planning for Remote Access client computers, server and client authentication requirements, and infrastructure servers.