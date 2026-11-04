---
layout: Conceptual
title: Federation Server Farm Using WID and Proxies | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/federation-server-farm-using-wid-and-proxies
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Legacy AD FS Federation Server Farm Using WID and Proxies'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
ms.custom: sfi-image-nochange
locale: en-us
document_id: 9b624369-5628-1bbd-1e87-aa5bdcf16142
document_version_independent_id: 0cbf7050-9650-f9d5-e9ed-aa08b6505b1d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Federation-Server-Farm-Using-WID-and-Proxies.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/federation-server-farm-using-wid-and-proxies
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Federation-Server-Farm-Using-WID-and-Proxies.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d89b01de-d8f9-2918-e5f2-cf68fc8f9b1b
---

# Federation Server Farm Using WID and Proxies | Microsoft Learn

This deployment topology for Active Directory Federation Services (AD FS) is identical to the federation server farm with Windows Internal Database (WID) topology, but it adds proxy computers to the perimeter network to support external users. These proxies redirect client authentication requests that come from outside your corporate network to the federation server farm. In previous versions of AD FS, these proxies were called federation server proxies.

Important

In Active Directory Federation Services (AD FS) in Windows Server 2012 R2 , the role of a federation server proxy is handled by a new Remote Access role service called Web Application Proxy. To enable your AD FS for accessibility from outside the corporate network, which was the purpose of deploying a federation server proxy in legacy versions of AD FS, such as AD FS 2.0 and AD FS in Windows Server 2012 , you can deploy one or more web application proxies for AD FS in Windows Server 2012 R2 .

In the context of AD FS, Web Application Proxy functions as an AD FS federation server proxy. In addition to this, Web Application Proxy provides reverse proxy functionality for web applications inside your corporate network to enable users on any device to access them from outside the corporate network. For more information, about the Web Application Proxy role service, see Web Application Proxy Overview.

To plan the deployment of Web Application proxy, you can review the information in the following topics:

- [Plan the Web Application Proxy Infrastructure (WAP)](/en-us/previous-versions/orphan-topics/ws.11/dn383648%28v=ws.11%29)
- [Plan the Web Application Proxy Server](/en-us/previous-versions/orphan-topics/ws.11/dn383647%28v=ws.11%29)

## Deployment considerations

This section describes various considerations about the intended audience, benefits, and limitations that are associated with this deployment topology.

### Who should use this topology?

- Organizations with 100 or fewer configured trust relationships that need to provide both their internal users and external users (who are logged on to computers that are physically located outside the corporate network) with single sign-on (SSO) access to federated applications or services
- Organizations that need to provide both their internal users and external users with SSO access to Microsoft Office 365
- Smaller organizations that have external users and require redundant, scalable services

### What are the benefits of using this topology?

- The same benefits as listed for the [Federation Server Farm Using WID](federation-server-farm-using-wid) topology, plus the benefit of providing additional access for external users

### What are the limitations of using this topology?

- The same limitations as listed for the [Federation Server Farm Using WID](federation-server-farm-using-wid) topology

    | 1-100 RP Trusts | More than 100 RP Trusts |
    | --- | --- |
    | **1-30 AD FS Nodes:** WID supported | **1-30 AD FS Nodes:** Not supported using WID - SQL Required |
    | **More than 30 AD FS Nodes:** Not supported using WID - SQL Required | **More than 30 AD FS Nodes:** Not supported using WID - SQL Required |

## Server placement and network layout recommendations

To deploy this topology, in addition to adding two web application proxies, you must make sure that your perimeter network can also provide access to a Domain Name System (DNS) server and to a second Network Load Balancing (NLB) host. The second NLB host must be configured with an NLB cluster that uses an Internet-accessible cluster IP address, and it must use the same cluster DNS name setting as the previous NLB cluster that you configured on the corporate network (fs.fabrikam.com). The web application proxies should also be configured with Internet-accessible IP addresses.

The following illustration shows the existing federation server farm with WID topology that was described previously and how the fictional Fabrikam, Inc., company provides access to a perimeter DNS server, adds a second NLB host with the same cluster DNS name (fs.fabrikam.com), and adds two web application proxies (wap1 and wap2) to the perimeter network.

![WID Farm and Proxies](media/widfarmadfsblue.gif)

For more information about how to configure your networking environment for use with federation servers or web application proxies, see "Name Resolution Requirements" section in [AD FS Requirements](ad-fs-requirements) and [Plan the Web Application Proxy Infrastructure (WAP)](/en-us/previous-versions/orphan-topics/ws.11/dn383648%28v=ws.11%29).