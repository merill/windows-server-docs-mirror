---
layout: Conceptual
title: Name Resolution Requirements for Federation Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/name-resolution-requirements-for-federation-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Name Resolution Requirements for Federation Servers'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 47f650ef-9c5c-2440-56aa-6e57b5dd8f7a
document_version_independent_id: 81d1a835-7a94-2f36-936b-f3e9b11c6b40
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Name-Resolution-Requirements-for-Federation-Servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/name-resolution-requirements-for-federation-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Name-Resolution-Requirements-for-Federation-Servers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 0aba45bf-8925-e172-b812-700696ec0354
---

# Name Resolution Requirements for Federation Servers | Microsoft Learn

When client computers on the corporate network attempt to access an application or Web service that is protected by Active Directory Federation Services (AD FS), they must first authenticate to a federation server. One way to authenticate is to have the corporate network clients access a local federation server through Windows Integrated Authentication.

## Configure corporate DNS

So that successful name resolution through Windows Integrated Authentication on local federation servers can occur, Domain Name System (DNS) in the corporate network of the account partner must be configured for a new host (A) resource record that will resolve the fully qualified domain name (FQDN) host name of the federation server to the IP address of the federation server cluster.

In the following illustration, you can see how this task is accomplished for a given scenario. In this scenario, Microsoft Network Load Balancing (NLB) provides a single cluster FQDN name and a single cluster IP address for an existing federation server farm.

![name requirements](media/adfs2_deploy_single_fs.gif)

For information about how to configure a cluster IP address or cluster FQDN using NLB, see [Specifying the Cluster Parameters](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc781505%28v=ws.10%29).

For information about how to configure corporate DNS for a federation server, see [Add a Host (A) Resource Record to Corporate DNS for a Federation Server](../deployment/add-a-host--a--resource-record-to-corporate-dns-for-a-federation-server).

For information about how to configure federation server proxies in the perimeter network, see [Name Resolution Requirements for Federation Server Proxies](name-resolution-requirements-for-federation-server-proxies).