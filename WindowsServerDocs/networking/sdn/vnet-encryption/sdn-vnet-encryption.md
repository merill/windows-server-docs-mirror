---
layout: Conceptual
title: Virtual Network Encryption | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/vnet-encryption/sdn-vnet-encryption
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: Learn about the requirements of virtual network encryption.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2018-08-08T00:00:00.0000000Z
locale: en-us
document_id: 4723fb4d-d332-fedd-5e1a-d45e4d219ba8
document_version_independent_id: 5e5e78f1-eff3-e2f4-3ee4-641b8f390e58
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/vnet-encryption/sdn-vnet-encryption.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/vnet-encryption/sdn-vnet-encryption
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/vnet-encryption/sdn-vnet-encryption.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
platformId: c588346f-3bf6-06b3-f2ee-be3bc8dd5bb2
---

# Virtual Network Encryption | Microsoft Learn

Virtual network encryption allows encryption of virtual network traffic between virtual machines that communicate with each other within subnets marked as ‘Encryption Enabled.' It also utilizes Datagram Transport Layer Security (DTLS) on the virtual subnet to encrypt packets. DTLS protects against eavesdropping, tampering, and forgery by anyone with access to the physical network.

Virtual network encryption requires:

- Encryption certificates installed on each of the SDN-enabled Hyper-V hosts.
- A credential object in the Network Controller referencing the thumbprint of that certificate.
- Configuration on each of the Virtual Networks contain subnets that require encryption.

Once you enable encryption on a subnet, all network traffic within that subnet is encrypted automatically, in addition to any application-level encryption that may also take place. Traffic that crosses between subnets, even if marked as encrypted, is sent unencrypted automatically. Any traffic that crosses the virtual network boundary also gets sent unencrypted.

Tip

If you must restrict applications to only communicate on the encrypted subnet, you can use Access Control Lists (ACLs) only to allow communication within the current subnet. For more information, see [Use Access Control Lists (ACLs) to Manage Datacenter Network Traffic Flow](/en-us/azure/azure-local/manage/use-datacenter-firewall-powershell?context=/windows-server/context/windows-server-edge-networking).

### Next steps

[Configure encryption for a virtual network](sdn-config-vnet-encryption)