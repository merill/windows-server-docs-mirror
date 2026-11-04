---
layout: Conceptual
title: When to Create a Federation Server Proxy Farm | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/when-to-create-a-federation-server-proxy-farm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: When to Create a Federation Server Proxy Farm'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 5344d206-b351-3f92-a171-f326fbc71621
document_version_independent_id: 27ef7dfb-2408-3393-b6d0-56be0e868145
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/When-to-Create-a-Federation-Server-Proxy-Farm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/when-to-create-a-federation-server-proxy-farm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/When-to-Create-a-Federation-Server-Proxy-Farm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c8a7eec3-3f6f-b345-77dc-430e9c92c927
---

# When to Create a Federation Server Proxy Farm | Microsoft Learn

Consider installing additional federation server proxies when you have a large Active Directory Federation Services (AD FS) deployment and you want to provide fault tolerance, load-balancing, and scalability for your proxy deployment. The act of creating two or more federation server proxies in the same perimeter network and configuring each of them to protect the same AD FS Federation Service creates a federation server proxy farm.

You can create a federation server proxy farm or install additional federation server proxies to an existing farm by using the AD FS Federation Server Proxy Configuration Wizard. For more information, see [When to Create a Federation Server Proxy](when-to-create-a-federation-server-proxy).

Before all the federation server proxies can function together as a farm, you must first cluster them under one IP address and one Domain Name System (DNS) fully qualified domain name (FQDN). You can cluster the servers by deploying Microsoft Network Load Balancing (NLB) inside the perimeter network. The tasks in the following table require NLB to be configured appropriately to cluster the federation server proxies in the farm.

For more information about how to configure an FQDN for a cluster using Microsoft NLB technology, see [Specifying the Cluster Parameters](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc781505%28v=ws.10%29).

## Configuring federation server proxies for a farm

The following table describes the tasks that must be completed so that each federation server proxy can participate in a farm.

| Task | Description |
| --- | --- |
| Point all proxies in the farm to the same AD FS Federation Service name | When you create the federation server proxies, you must type the same Federation Service name in the AD FS Federation Server Proxy Configuration Wizard for all the federation server proxies that will participate in the farm. The federation server proxy uses the URL that makes up this DNS host name to determine which AD FS Federation Service instance it contacts.<br>For more information, see [Configure a Computer for the Federation Server Proxy Role](../deployment/configure-a-computer-for-the-federation-server-proxy-role). |
| Obtain and share certificates | You can obtain a server authentication certificate from a public certification authority (CA)—for example, VeriSign—and then configure the certificate so that all federation server proxies share the same private key portion of the same certificate on the default Web site for each federation server proxy. To share the certificate, you must install the same server authentication certificate on the default Web site for each federation server proxy. For more information, see [Import a Server Authentication Certificate to the Default Web Site](../deployment/import-a-server-authentication-certificate-to-the-default-web-site).<br>For more information, see [Certificate Requirements for Federation Server Proxies](certificate-requirements-for-federation-server-proxies). |

For more information about adding new federation server proxies to create a federation server proxy farm, see [Checklist: Setting Up a Federation Server Proxy](../deployment/checklist--setting-up-a-federation-server-proxy).