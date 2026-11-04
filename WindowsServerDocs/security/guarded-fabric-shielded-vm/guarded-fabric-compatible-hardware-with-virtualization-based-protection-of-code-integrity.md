---
layout: Conceptual
title: Compatible hardware with Windows Server Virtualization-based protection of Code Integrity | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-compatible-hardware-with-virtualization-based-protection-of-code-integrity
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Compatible hardware with Windows Server Virtualization-based protection of Code Integrity'
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: 1ada5fc4-53f8-25b9-3281-2b97246081f3
document_version_independent_id: 126935da-6749-9ac0-30ef-7f6ed3d58d1f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-compatible-hardware-with-virtualization-based-protection-of-code-integrity.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-compatible-hardware-with-virtualization-based-protection-of-code-integrity
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-compatible-hardware-with-virtualization-based-protection-of-code-integrity.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 9cd20833-2a46-ec53-004c-a0d3e0191bad
---

# Compatible hardware with Windows Server Virtualization-based protection of Code Integrity | Microsoft Learn

Windows Server 2016 introduced a new Virtualization-based code protection to help protect physical and virtual machines from attacks that modify system code. To achieve this high protection level, Microsoft works in tandem with the computer hardware manufactures (Original Equipment Manufacturers, or OEMs) to prevent malicious writes into system execution code. This protection can be applied to any system and is being used as one of the building blocks for implementing the Hyper-V host health for shielded virtual machines (VMs).

As with any hardware based protection, some systems might not be compliant due to issues such as incorrect marking of memory pages as executables or by actually trying to modify code at run time, which may result in unexpected failures including data loss or a blue screen error (also called a stop error).

To be compatible and fully support the new security feature, OEMs need to implement the Memory Address Table defined in UEFI 2.6, which was published in Jan. 2016. The adoption of the new UEFI standard takes time; meanwhile, to prevent customers encountering issues, we want to provide information about systems and configurations that we have tested this feature set with as well as systems that we know to be not compatible.

## Non-compatible systems

The following configurations are known to be non-compatible with Virtualization-based protection of code integrity and cannot be used as a host for Shielded VMs:

- Dell PowerEdge Servers running PERC H330 RAID Controllers For more information, see the following article from Dell Support [H330 – Enabling "Host Guardian Hyper-V Support" or "Device Guard" on Win 2016 OS causes OS boot failure](https://www.dell.com/support/manuals/microsoft-windows-server-2016/ws2016_iig_pub/unable-to-boot-into-windows-server-2016-if-host-guardian-hyper-v-support-or-device-guard-is-enable%7E?guid=guid-a8273240-e45b-4c18-a553-97250a7e835d&amp;lang=en-us).

## Compatible systems

These are the systems we and our partners have been testing in our environment. Please make sure that you verify the system works as expected in your environment:

- Virtual Machines – You can enable Virtualization-based protection of code integrity on virtual machines that run on a Hyper-V host beginning with Windows Server 2016.