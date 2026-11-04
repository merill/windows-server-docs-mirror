---
layout: Conceptual
title: Review HGS prerequisites | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-prepare-for-hgs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Review prerequisites for the Host Guardian Service'
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: 913bd164-8dc0-430f-baad-8c161815aeb6
document_version_independent_id: 22708da0-b59c-3c92-94fc-f6f976483f15
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-prepare-for-hgs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-prepare-for-hgs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-prepare-for-hgs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 6e333f5b-46c6-74b6-e5c0-7dadd0298c6a
---

# Review HGS prerequisites | Microsoft Learn

This topic covers HGS prerequisites and initial steps to prepare for the HGS deployment.

## Prerequisites

- **Hardware**: HGS can be run on physical or virtual machines, but physical machines are recommended.

    If you want to run HGS as a three-node physical cluster (for availability), you must have three physical servers. (As a best practice for clustering, the three servers should have very similar hardware.)
- **Operating system**: Host key attestation requires Windows Server 2019 Standard or Datacenter edition operating with [v2 attestation](guarded-fabric-tpm-trusted-attestation-capturing-hardware#versioned-attestation-policies). For TPM-based attestation, HGS can run Windows Server 2019 or Windows Server 2016, Standard or Datacenter edition.
- **Server Roles**: Host Guardian Service and supporting server roles.
- **Configuration permissions/privileges for the fabric (host) domain**: You will need to configure DNS forwarding between the fabric (host) domain and the HGS domain.

## Upgrading HGS

If you've already deployed HGS and want to upgrade its operating system, follow the [upgrade guidance](guarded-fabric-upgrade-to-2019) to upgrade your HGS and Hyper-V servers to the latest OS.