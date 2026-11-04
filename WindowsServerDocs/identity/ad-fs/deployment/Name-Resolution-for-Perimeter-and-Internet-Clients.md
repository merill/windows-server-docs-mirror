---
layout: Conceptual
title: Name Resolution for Perimeter and Internet Clients | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/name-resolution-for-perimeter-and-internet-clients
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Name Resolution for Perimeter and Internet Clients'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 2227cc75-a405-6062-6143-a63b40e21c2b
document_version_independent_id: d7ca37d9-a3ee-cd72-12e7-a6bc4b79e049
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Name-Resolution-for-Perimeter-and-Internet-Clients.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/name-resolution-for-perimeter-and-internet-clients
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Name-Resolution-for-Perimeter-and-Internet-Clients.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a9b78b12-15f3-8f7b-764d-495fa83cd11e
---

# Name Resolution for Perimeter and Internet Clients | Microsoft Learn

So that name resolution can work successfully for a federation server proxy in an Active Directory Federation Services (AD FS) scenario in which one or more Domain Name System (DNS) zones serve both the perimeter network and Internet clients, the following tasks must be completed:

- DNS in the Internet zone that you control must be configured to resolve all Internet client requests for the AD FS host name to the federation server proxy. To accomplish this, you add a host (A) resource record to the Internet DNS zone for the federation server proxy.
- DNS in the perimeter network must be configured to resolve all incoming client requests for the AD FS host name to the federation server. To accomplish this, you add a host (A) resource record to the perimeter DNS zone for the federation server proxy.

Note

It is assumed that a host (A) resource record for the federation server has already been created in the corporate network DNS. If this record does not yet exist, create this record and then perform these procedures. For more information about how to create a host (A) resource record for the federation server, see [Add a Host (A) Resource Record to Corporate DNS for a Federation Server](add-a-host--a--resource-record-to-corporate-dns-for-a-federation-server).

## Add a host (A) resource record to the Internet DNS zone for a federation server proxy

So that client computers on the Internet can successfully access a federation server through a newly deployed federation server proxy, you must first create a host (A) resource record in the Internet DNS zone that you control. This resource record resolves the host name of the account federation server (for example, fs.fabrikam.com) to the IP address of the account federation server proxy (for example, 131.107.27.68) in the perimeter network.

Note

It is assumed that you are using a DNS server running Windows 2000 Server, Windows Server 2003, or Windows Server 2008 with the DNS Server service to control the Internet DNS zone.

Membership in **Administrators**, or equivalent, is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

#### To add a host (A) resource record to the Internet DNS zone for a federation server proxy

1. On a DNS server for the Internet DNS zone, open the DNS snap-in.
2. In the console tree, right-click the applicable forward lookup zone, and then click **New Host (A or AAAA)**.
3. In **Name**, type only the computer name of the federation server. For example, for the fully qualified domain name (FQDN) fs.fabrikam.com, type **fs**.
4. In **IP address**, type the IP address for the new federation server proxy, for example, 131.107.27.68.
5. Click **Add Host**.

## Add a host (A) resource record to the perimeter DNS zone for a federation server proxy

So that Internet client requests can be processed successfully by the federation server proxy and reach the federation server after they are resolved by the Internet DNS zone, you must create a host (A) resource record in the perimeter DNS zone. This resource record resolves the host name of the account federation server (for example, fs. fabrikam.com) to the IP address of the account federation server (for example, 192.168.1.4) in the corporate network.

Note

It is assumed that you are using a DNS server running Windows 2000 Server, Windows Server 2003, Windows Server 2008 , or Windows Server® 2012 with the DNS Server service to control the perimeter DNS zone.

Membership in **Administrators**, or equivalent, is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

#### To add a host (A) resource record to the perimeter DNS zone for a federation server proxy

1. On a DNS server for the perimeter network, open the **DNS snap-in**.
2. In the console tree, right-click the applicable forward lookup zone, and then click **New Host (A or AAAA)**.
3. In **Name**, type only the computer name of the federation server. For example, for the FQDN fs.fabrikam.com, type **fs**.
4. In the **IP address** text box, type the IP address for the federation server in the corporate network, for example, 192.168.1.4.
5. Click **Add Host**.

## Additional references

[Checklist: Setting Up a Federation Server Proxy](checklist--setting-up-a-federation-server-proxy)

[Name Resolution Requirements for Federation Server Proxies](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807055%28v=ws.11%29)