---
layout: Conceptual
title: Add a Host (A) Resource Record to Corporate DNS for a Federation Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/add-a-host--a--resource-record-to-corporate-dns-for-a-federation-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Add a Host (A) Resource Record to Corporate DNS for a Federation Server'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 3f9ab151-cf48-64d7-609a-9a9e035609bb
document_version_independent_id: 075775cc-92bb-0f67-d603-85ebe8b285f9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Add-a-Host--A--Resource-Record-to-Corporate-DNS-for-a-Federation-Server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/add-a-host--a--resource-record-to-corporate-dns-for-a-federation-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Add-a-Host--A--Resource-Record-to-Corporate-DNS-for-a-Federation-Server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4b37d88e-56b9-89f4-6071-056b9c920221
---

# Add a Host (A) Resource Record to Corporate DNS for a Federation Server | Microsoft Learn

For clients on the corporate network to successfully access a federation server using Windows Integrated authentication, a host (A) resource record must first be created in the corporate Domain Name System (DNS) that resolves the host name of the account federation server (for example, fs.fabrikam.com) to the IP address of the federation server or federation server cluster. You can use the following procedure to add a host (A) resource record to corporate DNS for a federation server.

Membership in **Administrators**, or equivalent, is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

### To add a host (A) resource record to corporate DNS for a federation server

1. On a DNS server for the corporate network, open the DNS snap-in.
2. In the console tree, right-click the applicable forward lookup zone, and then click **New Host (A or AAAA)**.
3. In **Name**, type only the computer name of the federation server or federation server cluster; for example, for the fully qualified domain name (FQDN) fs.fabrikam.com, type **fs**.
4. In **IP address**, type the IP address for the federation server or federation server cluster, for example, 192.168.1.4.
5. Click **Add Host**.

## Additional references

[Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server)

[Name Resolution Requirements for Federation Servers](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807055%28v=ws.11%29)