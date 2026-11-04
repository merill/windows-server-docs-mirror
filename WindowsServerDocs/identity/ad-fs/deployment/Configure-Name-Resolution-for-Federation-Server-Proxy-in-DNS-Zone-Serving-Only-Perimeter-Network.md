---
layout: Conceptual
title: Configure Name Resolution for a Federation Server Proxy in a DNS Zone That Serves Only the Perimeter Network | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/configure-name-resolution-for-federation-server-proxy-in-dns-zone-serving-only-perimeter-network
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configure Name Resolution for a Federation Server Proxy in a DNS Zone That Serves Only the Perimeter Network'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 81228e08-116d-219f-51e6-fb6ff26960df
document_version_independent_id: f17b9169-d343-f296-e194-2ba7c6646ce6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Configure-Name-Resolution-for-Federation-Server-Proxy-in-DNS-Zone-Serving-Only-Perimeter-Network.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/configure-name-resolution-for-federation-server-proxy-in-dns-zone-serving-only-perimeter-network
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Configure-Name-Resolution-for-Federation-Server-Proxy-in-DNS-Zone-Serving-Only-Perimeter-Network.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0db13c34-705c-5173-0a26-5542b8b35a66
---

# Configure Name Resolution for a Federation Server Proxy in a DNS Zone That Serves Only the Perimeter Network | Microsoft Learn

So that name resolution can work successfully for a federation server in an Active Directory Federation Services (AD FS) scenario in which one or more Domain Name System (DNS) zones serve only the perimeter network, the following tasks must be completed:

- The hosts file on the federation server proxy must be updated to add the IP address of a federation server.
- DNS in the perimeter network must be configured to resolve all client requests for the AD FS host name to the federation server proxy. To do this, you add a host (A) resource record to perimeter DNS for the federation server proxy.

Note

These procedures assume that a host (A) resource record for the federation server has already been created in the corporate network DNS. If this record does not yet exist, create this record, and then perform these procedures. For more information about how to create the host (A) resource record for the federation server, see [Add a Host (A) Resource Record to Corporate DNS for a Federation Server](add-a-host--a--resource-record-to-corporate-dns-for-a-federation-server).

## Add the IP address of a federation server to the hosts file

So that a federation server proxy can work as expected in the perimeter network of an account partner, you must add an entry to the hosts file on that federation server proxy that points to a federation server's DNS host name (for example, fs.fabrikam.com) and IP address (for example, 192.168.1.4) in the corporate network of the account partner. Adding this entry to the hosts file prevents the federation server proxy from contacting itself to resolve a client-initiated call to a federation server in the account partner.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

#### To add the IP address of a federation server to the hosts file

1. Navigate to the %systemroot%\Winnt\System32\Drivers directory folder and locate the **hosts** file.
2. Start Notepad, and then open the **hosts** file.
3. Add the IP address and the host name of a federation server in the account partner to the **hosts** file, as shown in the following example:

    **192.168.1.4fs.fabrikam.com**
4. Save and close the file.

## Add a host (A) resource record to perimeter DNS for a federation server proxy

So that clients on the Internet can successfully access a federation server through a newly deployed federation server proxy, you must first create a host (A) resource record in the perimeter DNS. This resource record resolves the host name of the account federation server (for example, fs.fabrikam.com) to the IP address of the account federation server proxy (for example, 131.107.27.68) in the perimeter network.

Note

It is assumed that you are using a DNS server, running Windows 2000 Server, Windows Server 2003, or Windows Server 2008 with the DNS Server service, to control the perimeter DNS zone.

Membership in **Administrators**, or equivalent, is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

#### To add a host (A) resource record to perimeter DNS for a federation server proxy

1. On a DNS server for the perimeter network, open the DNS snap-in. Click **Start**, point to **Administrative Tools**, and then click **DNS**.
2. In the console tree, right-click the applicable forward lookup zone, and then click **New Host (A or AAAA)**.
3. In **Name**, type only the computer name of the federation server. For example, for the fully qualified domain name (FQDN) fs.fabrikam.com, type **fs**.
4. In **IP address**, type the IP address for the new federation server proxy, for example, **131.107.27.68**.
5. Click **Add Host**.

## Additional references

[Checklist: Setting Up a Federation Server Proxy](checklist--setting-up-a-federation-server-proxy)

[Name Resolution Requirements for Federation Server Proxies](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807055%28v=ws.11%29)