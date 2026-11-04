---
layout: Conceptual
title: Initialize HGS using TPM-trusted attestation | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Initialize HGS using TPM-trusted attestation'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: 909f6d4d-73a9-0687-2d23-0f9a8b76578f
document_version_independent_id: 1a85b952-fd41-7c74-fde2-c13db29726c6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7c01134-b8f3-438c-822d-13471e513908
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/82fff6b2-939d-4e9a-8f9c-d1c41a59749b
platformId: 8cb48975-09ab-0a35-a4fa-35af94c4ce90
---

# Initialize HGS using TPM-trusted attestation | Microsoft Learn

These steps vary depending on whether you are initializing HGS in a new forest or an existing bastion forest:

1. [Initialize the HGS cluster in a new forest (default)](guarded-fabric-initialize-hgs-tpm-mode-default)

    -Or-

    [Initialize the HGS cluster in an existing bastion forest](guarded-fabric-initialize-hgs-tpm-mode-bastion)
2. [Install trusted TPM root certificates](guarded-fabric-install-trusted-tpm-root-certificates)
3. [Configure the fabric DNS](guarded-fabric-configuring-fabric-dns)