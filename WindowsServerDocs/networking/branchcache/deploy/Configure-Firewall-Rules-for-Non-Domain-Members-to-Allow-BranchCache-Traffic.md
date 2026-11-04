---
layout: Conceptual
title: Configure Firewall Rules for Non-Domain Members to Allow BranchCache Traffic | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/configure-firewall-rules-for-non-domain-members-to-allow-branchcache-traffic
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to configure third party firewall products and to manually configure a client computer with firewall rules that allow BranchCache to run in distributed cache mode.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 7fb1f66a-6a3e-f6f2-6295-b5cff348766e
document_version_independent_id: 413a00e7-5481-02c5-4751-30b54a519d76
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Configure-Firewall-Rules-for-Non-Domain-Members-to-Allow-BranchCache-Traffic.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/configure-firewall-rules-for-non-domain-members-to-allow-branchcache-traffic
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Configure-Firewall-Rules-for-Non-Domain-Members-to-Allow-BranchCache-Traffic.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: cbdbbe72-46de-3c25-eff6-5d265fc846fa
---

# Configure Firewall Rules for Non-Domain Members to Allow BranchCache Traffic | Microsoft Learn

You can use the information in this topic to configure third party firewall products and to manually configure a client computer with firewall rules that allow BranchCache to run in distributed cache mode.

Note

- If you have configured BranchCache client computers using Group Policy, the Group Policy settings override any manual configuration of client computers to which the policies are applied.
- If you have deployed BranchCache with DirectAccess, you can use the settings in this topic to configure IPsec rules to allow BranchCache traffic.

Membership in **Administrators**, or equivalent is the minimum required to make these configuration changes.

## [MS-PCCRD]: Peer Content Caching and Retrieval Discovery Protocol

Distributed cache clients must allow inbound and outbound MS-PCCRD traffic, which is carried in the Web Services Dynamic Discovery (WS-Discovery) protocol.

Firewall settings must allow multicast traffic in addition to inbound and outbound traffic. You can use the following settings to configure firewall exceptions for distributed cache mode.

IPv4 multicast: 239.255.255.250

IPv6 multicast: FF02::C

Inbound traffic: Local port: 3702, Remote port: ephemeral

Outbound traffic: Local port: ephemeral, Remote port: 3702

Program: %systemroot%\system32\svchost.exe (BranchCache Service [PeerDistSvc])

## [MS-PCCRR]: Peer Content Caching and Retrieval: Retrieval Protocol

Distributed cache clients must allow inbound and outbound MS-PCCRR traffic, which is carried in the HTTP 1.1 protocol as documented in request for comments (RFC) 2616.

Firewall settings must allow inbound and outbound traffic. You can use the following settings to configure firewall exceptions for distributed cache mode.

Inbound traffic: Local port: 80, Remote port: ephemeral

Outbound traffic: Local port: ephemeral, Remote port: 80