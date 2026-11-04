---
layout: Conceptual
title: Generation 1 virtual machine security settings for Hyper-V | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/generation-1-virtual-machine-security-features
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Describes the security settings available in Hyper-V Manager for generation 1 virtual machines
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2016-10-04T00:00:00.0000000Z
locale: en-us
document_id: 99812656-51d0-130b-1e84-c2f4a00a4acd
document_version_independent_id: 99812656-51d0-130b-1e84-c2f4a00a4acd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/generation-1-virtual-machine-security-features.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/generation-1-virtual-machine-security-features
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/generation-1-virtual-machine-security-features.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: bfc4a693-be95-084c-0758-3e8d7738fb21
---

# Generation 1 virtual machine security settings for Hyper-V | Microsoft Learn

Use the generation 1 virtual machine security settings in Hyper-V Manager to help protect the data and state of a virtual machine.

## Encryption support settings in Hyper-V Manager

You can help protect the data and state of the virtual machine by selecting the following encryption support option.

- **Encrypt state and virtual machine migration traffic** - Encrypts the virtual machine saved state when it's written to disk and the live migration traffic.

To enable this option, you must add a key storage drive for the virtual machine.

## Key storage drive in Hyper-V Manager

A key storage drive provides a small drive to the virtual machine for a BitLocker key to be stored. This allows the virtual machine to encrypt its operating system disk without requiring a virtualized Trusted Platform Module (TPM) chip. The contents of the key storage drive are encrypted by using a Key Protector. The Key Protector authories the Hyper-V host to run the virtual machine. Both the contents of the key storage drive and the Key Protector are stored as part of the virtual machine's runtime state.

To decrypt the contents of the key storage drive and start the virtual machine, the Hyper-V host needs to be either:

- Part of an authorized guarded fabric for this virtual machine, or
- Have the private key from one of the virtual machine's guardians.

To learn more about guarded fabrics, please see the Introducing Shielded VMs section in [Security and Assurance](../../security/security-and-assurance).

You can add a key storage drive to an empty slot on one of the virtual machine's IDE controllers. To do this, click **Add Key Storage Drive** to add a key storage drive to the first free IDE controller slot of this virtual machine.

## Additional References

- [Generation 2 virtual machine security settings in Hyper-V manager](generation-2-virtual-machine-security-features)
- [Security and Assurance](../../security/security-and-assurance)