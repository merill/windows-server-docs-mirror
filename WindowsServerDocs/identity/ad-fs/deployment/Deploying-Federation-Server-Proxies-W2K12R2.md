---
layout: Conceptual
title: Deploying Federation Server Proxies in AD FS for Windows Server 2012 R2 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/deploying-federation-server-proxies-w2k12r2
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Deploying Federation Server Proxies'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: checklist
locale: en-us
document_id: 91f48063-77eb-609f-71f2-9cf06dbed844
document_version_independent_id: 9a0d300f-188f-a5e7-349c-ba9980037641
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Deploying-Federation-Server-Proxies-W2K12R2.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/deploying-federation-server-proxies-w2k12r2
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Deploying-Federation-Server-Proxies-W2K12R2.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6c57776-ab71-4356-880c-c5ff411d7fe1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e2d3fbf8-36df-4730-9ac5-e1c53887f039
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 980e4274-4475-c4a3-87c7-05b531bb10b7
---

# Deploying Federation Server Proxies in AD FS for Windows Server 2012 R2 | Microsoft Learn

In Active Directory Federation Services (AD FS) in Windows Server 2012 R2 , the role of a federation server proxy is handled by a new Remote Access role service called Web Application Proxy. To enable your AD FS for accessibility from outside the corporate network, which was the purpose of deploying a federation server proxy in legacy versions of AD FS, such as AD FS 2.0 and AD FS in Windows Server 2012 , you can deploy one or more web application proxies for AD FS in Windows Server 2012 R2 .

In the context of AD FS, Web Application Proxy functions as an AD FS federation server proxy. In addition to this, Web Application Proxy provides reverse proxy functionality for web applications inside your corporate network to enable users on any device to access them from outside the corporate network. For more information, about the Web Application Proxy role service, see Web Application Proxy Overview.

To plan the deployment of Web Application proxy, you can review the information in the following topics:

- [Plan the Web Application Proxy Infrastructure (WAP)](/en-us/previous-versions/orphan-topics/ws.11/dn383648%28v=ws.11%29)
- [Plan the Web Application Proxy Server](/en-us/previous-versions/orphan-topics/ws.11/dn383647%28v=ws.11%29)

To deploy Web Application proxy, you can follow the procedures in the following topics:

- [Configure the Web Application Proxy Infrastructure](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383644%28v=ws.11%29)
- [Install and Configure the Web Application Proxy Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383662%28v=ws.11%29)