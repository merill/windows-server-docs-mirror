---
layout: Conceptual
title: Initialize HGS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Initialize the Host Guardian Service (HGS)'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: ea577a85-1c00-f7f8-e0bb-f09369a532e6
document_version_independent_id: dc35e418-e1ed-73cc-fbf9-c6b3c09c7e0d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 873db0be-785e-553b-9941-ce3e1cb55528
---

# Initialize HGS | Microsoft Learn

When you initialize HGS, you specify the mode that HGS will use to measure the health of guarded hosts. There are two mutually exclusive options. For background information about which mode to choose, see [Guarded Fabric and Shielded VM Planning Guide for Hosters](guarded-fabric-planning-for-hosters).

The following topics cover deployment steps for each mode:

- [TPM-trusted attestation (TPM mode)](guarded-fabric-initialize-hgs-tpm-mode)
- [Host key attestation (Key mode)](guarded-fabric-initialize-hgs-key-mode)
- [Admin-trusted attestation (AD mode)](guarded-fabric-initialize-hgs-ad-mode)

You should perform these steps on a physical server.