---
layout: Conceptual
title: Initialize HGS using Admin-trusted attestation | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-ad-mode
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Initialize HGS using Admin-trusted attestation'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: d8e671fb-7d39-bc24-e920-bd49de49d3d1
document_version_independent_id: d2181731-cd44-3437-0904-2d062f1305b6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-ad-mode.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-ad-mode
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-ad-mode.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: e0c104dd-856c-836c-f042-ec783a1360b1
---

# Initialize HGS using Admin-trusted attestation | Microsoft Learn

Important

Admin-trusted attestation (AD mode) is deprecated beginning with Windows Server 2019. For environments where TPM attestation is not possible, configure [host key attestation](guarded-fabric-initialize-hgs-key-mode). Host key attestation provides similar assurance to AD mode and is simpler to set up.

These steps vary depending on whether you are initializing HGS in a new forest or an existing bastion forest:

1. [Initialize the HGS cluster in a new forest (default)](guarded-fabric-initialize-hgs-ad-mode-default)

    -Or-

    [Initialize the HGS cluster in an existing bastion forest](guarded-fabric-initialize-hgs-ad-mode-bastion)
2. [Configure DNS forwarding in the fabric domain](guarded-fabric-configuring-fabric-dns)
3. [Configure DNS forwarding and a one-way trust in the HGS domain](guarded-fabric-configure-dns-forwarding-and-trust)