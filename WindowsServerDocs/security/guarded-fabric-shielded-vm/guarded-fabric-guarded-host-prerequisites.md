---
layout: Conceptual
title: Guarded host prerequisites | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-guarded-host-prerequisites
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Prerequisites for guarded hosts'
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: d046629b-e49c-f134-35ef-30c080c19b70
document_version_independent_id: eb095011-6b07-988e-f5dd-7a74a293027f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-guarded-host-prerequisites.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-guarded-host-prerequisites
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-guarded-host-prerequisites.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 207f68c9-079a-99b3-cde2-08ef8af62ae0
---

# Guarded host prerequisites | Microsoft Learn

Review the host prerequisites for the mode of attestation you've chosen, then click the next step to add guarded hosts.

## TPM-trusted attestation

Guarded hosts using TPM mode must meet the following prerequisites:

- **Hardware**: One host is required for initial deployment. To test Hyper-V live migration for shielded VMs, you must have at least two hosts.

    Hosts must have:

    - IOMMU and Second Level Address Translation (SLAT)
    - TPM 2.0
    - UEFI 2.3.1 or later
    - Configured to boot using UEFI (not BIOS or "legacy" mode)
    - Secure boot enabled
- **Operating system**: Windows Server 2016 Datacenter edition or later

    Important

    Make sure you install the [latest cumulative update](https://support.microsoft.com/help/4000825/windows-10-and-windows-server-2016-update-history).
- **Role and features**: Hyper-V role and the Host Guardian Hyper-V Support feature. The Host Guardian Hyper-V Support feature is only available on Datacenter editions of Windows Server.

Warning

The Host Guardian Hyper-V Support feature enables Virtualization-based protection of code integrity that may be incompatible with some devices. We strongly recommend testing this configuration in your lab before enabling this feature. Failure to do so may result in unexpected failures up to and including data loss or a blue screen error (also called a stop error). For more information, see [Compatible hardware with Windows Server Virtualization-based protection of Code Integrity](guarded-fabric-compatible-hardware-with-virtualization-based-protection-of-code-integrity).

**Next step:**

## Host key attestation

Guarded hosts using host key attestation must meet the following prerequisites:

- **Hardware**: Any server capable of running Hyper-V beginning with Windows Server 2019
- **Operating system**: Windows Server 2019 Datacenter edition
- **Role and features**: Hyper-V role and the Host Guardian Hyper-V Support feature

The host can be joined to either a domain or a workgroup.

For host key attestation, HGS must be running Windows Server 2019 and operating with v2 attestation. For more information see [HGS prerequisites](guarded-fabric-prepare-for-hgs#prerequisites).

**Next step:**

## Admin-trusted attestation

Important

Admin-trusted attestation (AD mode) is deprecated beginning with Windows Server 2019. For environments where TPM attestation is not possible, configure host key attestation. Host key attestation provides similar assurance to AD mode and is simpler to set up.

Hyper-V hosts must meet the following prerequisites for AD mode:

- **Hardware**: Any server capable of running Hyper-V beginning with Windows Server 2016. One host is required for initial deployment. To test Hyper-V live migration for shielded VMs, you need at least two hosts.
- **Operating system**: Windows Server 2016 Datacenter edition

    Important

    Install the [latest cumulative update](https://support.microsoft.com/help/4000825/windows-10-and-windows-server-2016-update-history).
- **Role and features**: Hyper-V role and the Host Guardian Hyper-V Support feature, which is only available in Windows Server 2016 Datacenter edition.

Warning

The Host Guardian Hyper-V Support feature enables Virtualization-based protection of code integrity that may be incompatible with some devices. We strongly recommend testing this configuration in your lab before enabling this feature. Failure to do so may result in unexpected failures up to and including data loss or a blue screen error (also called a stop error). For more information, see [Compatible hardware with Windows Server 2016 Virtualization-based protection of Code Integrity](guarded-fabric-compatible-hardware-with-virtualization-based-protection-of-code-integrity).

**Next step:**