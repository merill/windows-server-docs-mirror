---
layout: Conceptual
title: Deploying Federation Server Proxies in AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/deploying-federation-server-proxies
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Deploying Legacy AD FS Federation Server Proxies'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: bdf3fabd-fd81-91e1-adaa-c62c5a6855a5
document_version_independent_id: 7e5ec885-881e-cbd3-4eb6-4937baa5ba18
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Deploying-Federation-Server-Proxies.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/deploying-federation-server-proxies
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Deploying-Federation-Server-Proxies.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d33a21c3-d5f1-76a7-a0de-02c7b880d4f6
---

# Deploying Federation Server Proxies in AD FS | Microsoft Learn

To deploy federation server proxies in Active Directory Federation Services (AD FS), complete each of the tasks in [Checklist: Setting Up a Federation Server Proxy](checklist--setting-up-a-federation-server-proxy).

Note

When you use this checklist, we recommend that you first read the references to federation server proxy planning guidance in the [AD FS Design Guide in Windows Server 2012](../design/ad-fs-design-guide-in-windows-server-2012) before you begin the procedures for configuring the servers. Following the checklist provides a better understanding of the design and deployment process for federation server proxies.

## About federation server proxies

Federation server proxies are computers that run Windows Server® 2012 and AD FS software that have been configured manually to act in the proxy role. You can use federation server proxies in your organization to provide intermediary services between an Internet client and a federation server that is behind a firewall on your corporate network.

Note

Although the federation server and the federation server proxy roles cannot be installed on the same computer, a federation server can perform federation server proxy functions. For more information, see [When to Create a Federation Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807101%28v=ws.11%29).

The act of installing the AD FS software on a Windows Server® 2012 computer and configuring it to serve in the proxy role makes that computer a federation server proxy.