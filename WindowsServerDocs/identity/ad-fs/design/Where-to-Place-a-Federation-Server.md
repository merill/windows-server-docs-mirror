---
layout: Conceptual
title: Where to Place a Federation Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/where-to-place-a-federation-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Where to Place a Federation Server'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 60e6e4fd-156e-3233-74e3-c5bcc6b61af1
document_version_independent_id: ba271746-da2c-8416-42dc-26a36f258e85
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Where-to-Place-a-Federation-Server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/where-to-place-a-federation-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Where-to-Place-a-Federation-Server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b3b73283-b59a-fafd-dad8-c96fe0adbd7c
---

# Where to Place a Federation Server | Microsoft Learn

As a security best practice, place Active Directory Federation Services (AD FS)federation servers behind a firewall and connect them to your corporate network to prevent exposure from the Internet. This is important because federation servers have full authorization to grant security tokens. Therefore, they should have the same protection as a domain controller. If a federation server is compromised, a malicious user has the ability to issue full access tokens to all Web applications and to federation servers that are protected by Active Directory Federation Services (AD FS) in all resource partner organizations.

Note

As a security best practice, avoid having your federation servers directly accessible on the Internet. Consider giving your federation servers direct Internet access only when you are setting up a test lab environment or when your organization does not have a perimeter network.

For typical corporate networks, an intranet-facing firewall is established between the corporate network and the perimeter network, and an Internet-facing firewall is often established between the perimeter network and the Internet. In this situation, the federation server sits inside the corporate network, and it is not directly accessible by Internet clients.

Note

Client computers that are connected to the corporate network can communicate directly with the federation server through Windows Integrated Authentication.

A federation server proxy should be placed in the perimeter network before you configure your firewall servers for use with AD FS. For more information, see [Where to Place a Federation Server Proxy](where-to-place-a-federation-server-proxy).

## Configuring your firewall servers for a federation server

So that the federation servers can communicate directly with federation server proxies, the intranet firewall server must be configured to allow Secure Hypertext Transfer Protocol (HTTPS) traffic from the federation server proxy to the federation server. This is a requirement because the intranet firewall server must publish the federation server using port 443 so that the federation server proxy in the perimeter network can access the federation server.

In addition, the intranet-facing firewall server, such as a server running Internet Security and Acceleration (ISA) Server, uses a process known as server publishing to distribute Internet client requests to the appropriate corporate federation servers. This means that you must manually create a server publishing rule on the intranet server running ISA Server that publishes the clustered federation server URL, for example, http://fs.fabrikam.com.

For more information about how to configure server publishing in a perimeter network, see [Where to Place a Federation Server Proxy](where-to-place-a-federation-server-proxy). For information about how to configure ISA Server to publish a server, see [Create a secure Web publishing rule](/en-us/previous-versions/tn-archive/bb794871%28v=technet.10%29).