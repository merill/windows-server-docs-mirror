---
layout: Conceptual
title: Planning for Federation Server Proxy Capacity | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/planning-for-federation-server-proxy-capacity
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Planning for Federation Server Proxy Capacity'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 72c64587-cb67-664f-f323-6c963ae4269a
document_version_independent_id: 47f5ce79-b5bd-4f98-fb8e-71e504b5abb8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Planning-for-Federation-Server-Proxy-Capacity.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/planning-for-federation-server-proxy-capacity
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Planning-for-Federation-Server-Proxy-Capacity.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7cc84b2c-d066-4438-a329-a1ec1f4c211b
---

# Planning for Federation Server Proxy Capacity | Microsoft Learn

Capacity planning for federation server proxies helps you estimate:

- The appropriate hardware requirements for each federation server proxy.
- The number of federation servers and federation server proxies to place in each organization.

Federation server proxies redirect security tokens from a protected federation server in the corporate network to federated users. The purpose of deploying a federation server proxy is to allow external users to connect to a federation server. It does not actually sign tokens or write to data in the AD FS configuration database. Therefore, the hardware requirements for the federation server proxy are usually lower than the hardware requirements for a federation server.

Because every request to a federation server proxy results in a request to a federation server or federation server farm, capacity planning for federation servers and federation server proxies must be performed in parallel.

Estimating the peak sign-ins per second for the federation server proxy requires an understanding of the usage patterns of the federated users that will be signing in through the federation server proxy. In many deployments, the federated users who sign in using the federation server proxy are located on the Internet. You can estimate the peak sign-ins per second by looking at the usage patterns of these federated users on the existing Web applications that will be protected by AD FS.

Note

For production deployments, we recommend a minimum of two federation server proxies for each federation server farm instance you deploy.

## Estimate the number of federation server proxies required for your organization

Before you can estimate the number of AD FS federation server proxy machines required, you will first need to determine the total number of federation servers that you will deploy in your organization. For more information about how to do this, see [Planning for Federation Server Capacity](planning-for-federation-server-capacity).

Once you have decided on the number of federation servers, multiply this number of servers by the percentage of incoming federated authentication requests that you expect will be made from external users (located outside of the corporate network). The value of this calculation will provide you with the estimated number of federation server proxies that will handle the incoming authentication requests for your external users.

For example, if the number of recommended federation servers is 3, and you expect that the total number of authentication requests that will be made from external users will be approximately 60% of the total number of federated authentication requests, your calculation would equal 1.8 (3 X .60) which you can round up to 2. Therefore, in this case, you would need to deploy two federation server proxy machines to accommodate the load of external user authentication requests for the three federation servers.

In tests performed by the AD FS product team, the overall CPU utilization on each federation server proxy was found to be significantly lower than the CPU utilization that was observed on the federation servers for the same farm. In one test, while one federation server CPU was indicating that it was completely saturated, the CPU for a federation server proxy providing proxy services for that same farm was observed at only 20% utilization. Therefore, our tests revealed that the load on the CPU of a federation server proxy, which uses similar hardware specifications as discussed earlier in this section, could reasonably handle the processing load for approximately three federation servers.

However, for fault tolerance purposes, we recommend a minimum of two federation server proxies for each federation server farm you deploy.