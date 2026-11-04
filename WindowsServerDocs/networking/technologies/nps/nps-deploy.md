---
layout: Conceptual
title: Deploy Network Policy Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-deploy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides links to Network Policy Server deployment content for Windows Server 2016, and includes links to additional guidance about NPS.
ms.topic: install-set-up-deploy
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: c01ca229-c5ea-6d23-d3e0-e3664ea9baff
document_version_independent_id: c3999c8e-b365-7f4f-b595-79b8d3e44be2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-deploy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-deploy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-deploy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 94783d96-c9b3-4d0f-184a-7329a88fd624
---

# Deploy Network Policy Server | Microsoft Learn

You can use this topic for information about deploying Network Policy Server.

Note

For additional Network Policy Server documentation, you can use the following library sections.

- [Getting Started with Network Policy Server](nps-getstart-top)
- [Plan Network Policy Server](nps-plan-top)
- [Manage Network Policy Server](nps-manage-top)

The Windows Server 2016 Core Network Guide includes a section on planning and installing Network Policy Server (NPS), and the technologies presented in the guide serve as prerequisites for deploying NPS in an Active Directory domain. For more information, see the section "Deploy NPS1" in the Windows Server 2016 [Core Network Guide](../../core-network-guide/core-network-guide#BKMK_deployNPS1).

## Deploy NPS Certificates for VPN and 802.1X Access

If you want to deploy authentication methods like Extensible Authentication Protocol (EAP) and Protected EAP that require the use of server certificates on your NPS, you can deploy NPS certificates with the guide [Deploy Server Certificates for 802.1X Wired and Wireless Deployments](../../core-network-guide/cncg/server-certs/deploy-server-certificates-for-802.1x-wired-and-wireless-deployments).

## Deploy NPS for 802.1X Wireless Access

To deploy NPS for wireless access, you can use the guide [Deploy Password-Based 802.1X Authenticated Wireless Access](../../core-network-guide/cncg/wireless/a-deploy-8021x-wireless-access).

## Deploy NPS for Windows 10 VPN Access

You can use NPS to process connection requests for Always On Virtual Private Network (VPN) connections for remote employees that are using computers and devices running Windows 10.

For more information, see the [Remote Access Always On VPN Deployment Tutorial for Windows Server 2016 and Windows 10](../../../remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy-deployment).