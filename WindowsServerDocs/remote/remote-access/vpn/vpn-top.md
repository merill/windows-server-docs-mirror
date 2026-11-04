---
layout: Conceptual
title: Virtual Private Networking (VPN) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/vpn/vpn-top
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how you can use RAS Gateway as a single-tenant VPN server.
ms.topic: overview
ms.date: 2018-11-05T00:00:00.0000000Z
ms.author: roharwoo
author: robinharwood
locale: en-us
document_id: f9037ffb-5ea7-d4d8-b247-6aad60c8f911
document_version_independent_id: 4311fb11-c58f-964c-a5b5-b9bb940a3dcf
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/vpn/vpn-top.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../networking/toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/vpn/vpn-top
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/vpn/vpn-top.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7a5038b6-32a5-9f89-c3d7-404c546c3d88
---

# Virtual Private Networking (VPN) | Microsoft Learn

## RAS Gateway as a Single Tenant VPN Server

In Windows Server 2016, the Remote Access server role is a logical grouping of the following related network access technologies.

- Remote Access Service (RAS)
- Routing
- Web Application Proxy

These technologies are the role services of the Remote Access server role.

When you install the Remote Access server role with the Add Roles and Features Wizard or Windows PowerShell, you can install one or more of these three role services.

When you install the **DirectAccess and VPN (RAS)** role service, you are deploying the Remote Access Service Gateway (**RAS Gateway**). You can deploy RAS Gateway as a single tenant RAS Gateway virtual private network (VPN) server that provides many advanced features and enhanced functionality.

Note

You can also deploy RAS Gateway as a Multitenant VPN server for use with Software Defined Networking (SDN), or as a DirectAccess server. For more information, see [RAS Gateway](../ras-gateway/ras-gateway), [Software Defined Networking (SDN)](/en-us/azure/azure-local/concepts/software-defined-networking?context=/windows-server/context/windows-server-remote), and [DirectAccess](../directaccess/directaccess).