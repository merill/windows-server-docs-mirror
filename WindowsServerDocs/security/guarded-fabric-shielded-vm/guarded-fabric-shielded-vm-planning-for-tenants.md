---
layout: Conceptual
title: Guarded Fabric and Shielded VM Planning Guide for Tenants | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-shielded-vm-planning-for-tenants
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Provides a guide to guarded fabric and shielded VM planning for VM owners who need to protect their virtual machines.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2020-12-10T00:00:00.0000000Z
locale: en-us
document_id: 9659169c-e868-1dae-5edc-cb898ed41a51
document_version_independent_id: 7169e88e-c4d2-0b79-c803-01d957ff01a4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-shielded-vm-planning-for-tenants.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-shielded-vm-planning-for-tenants
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-shielded-vm-planning-for-tenants.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 364532a6-9609-47e6-1e73-bd0c0873b05f
---

# Guarded Fabric and Shielded VM Planning Guide for Tenants | Microsoft Learn

This topic focuses on VM owners who would like to protect their virtual machines (VMs) for compliance and security purposes. Regardless of whether the VMs run on a hosting provider's guarded fabric or a private guarded fabric, VM owners need to control the security level of their shielded VMs, which includes maintaining the ability to decrypt them if needed.

There are three areas to consider when using shielded VMs:

- The security level for the VMs
- The cryptographic keys used to protect them
- Shielding data—sensitive information used to create shielded VMs

## Security level for the VMs

When deploying shielded VMs, one of two security levels must be selected:

- Shielded
- Encryption Supported

Both shielded and encryption-supported VMs have a virtual TPM attached to them and those that run Windows are protected by BitLocker. The primary difference is that shielded VMs block access by fabric administrators while encryption-supported VMs permit fabric administrators the same level of access as they would have to a regular VM. For more details about these differences, see [Guarded fabric and shielded VMs overview](guarded-fabric-and-shielded-vms).

Choose **Shielded VMs** if you are looking to protect the VM from a compromised fabric (including compromised administrators). They should be used in environments where fabric administrators and the fabric itself are not trusted. Choose **Encryption Supported VMs** if you are looking to meet a compliance bar that might require both encryption at-rest and encryption of the VM on the wire (e.g., during live migration).

Encryption-supported VMs are ideal in environments where fabric administrators are fully trusted but encryption remains a requirement.

You can run a mixture of regular VMs, shielded VMs, and encryption-supported VMs on a guarded fabric and even on the same Hyper-V host.

Whether a VM is shielded or encryption-supported is determined by the shielding data that is selected when creating the VM. VM owners configure the security level when creating the shielding data (see the Shielding data section). Note that once this choice has been made, it cannot be changed while the VM remains on the virtualization fabric.

## Cryptographic keys used for shielded VMs

Shielded VMs are protected from virtualization fabric attack vectors using encrypted disks and various other encrypted elements which can only be decrypted by:

- An Owner key – this is a cryptographic key maintained by the VM-owner that is typically used for last-resort recovery or troubleshooting. VM owners are responsible for maintaining owner keys in a secure location.
- One or more Guardians (Host Guardian keys) – each Guardian represents a virtualization fabric on which an owner authorizes shielded VMs to run. Enterprises often have both a primary and a disaster recovery (DR) virtualization fabric and would typically authorize their shielded VMs to run on both. In some cases, the secondary (DR) fabric might be hosted by a public cloud provider. The private keys for any guarded fabric are maintained only on the virtualization fabric, while its public keys can be downloaded and are contained within its Guardian.

**How do I create an owner key?** An owner key is represented by two certificates. A certificate for encryption and a certificate for signing. You can create these two certificates using your own PKI infrastructure or obtain SSL certificates from a public certificate authority (CA). For test purposes, you can also create a self-signed certificate on any computer beginning with Windows 10 or Windows Server 2016.

**How many owner keys should you have?** You can use a single owner key or multiple owner keys. Best practices recommend a single owner key for a group of VMs that share the same security, trust or risk level, and for administrative control. You can share a single owner key for all your domain-joined shielded VMs and escrow that owner key to be managed by the domain administrators.

**Can I use my own keys for the Host Guardian?** Yes, you can "Bring Your Own" key to the hosting provider and use that key for your shielded VMs. This enables you to use your specific keys (vs. using the hosting provider key) and can be used when you have specific security or regulations that you need to abide by. For key hygiene purposes, the Host Guardian keys should be different than the Owner key.

## Shielding data

Shielding data contains the secrets necessary to deploy shielded or encryption-supported VMs. It is also used when converting regular VMs to shielded VMs.

Shielding data is created using the Shielding Data File Wizard and is stored in PDK files which VM owners upload to the guarded fabric.

Shielded VMs help protect against attacks from a compromised virtualization fabric, so we need a safe mechanism to pass sensitive initialization data, such as the administrator's password, domain join credentials, or RDP certificates, without revealing these to the virtualization fabric itself or to its administrators. In addition, shielding data contains the following:

1. Security level – Shielded or encryption-supported
2. Owner and list of trusted Host Guardians where the VM can run
3. Virtual machine initialization data (unattend.xml, RDP certificate)
4. List of trusted signed template disks for creating the VM in the virtualization environment

When creating a shielded or encryption-supported VM or converting an existing VM, you will be asked to select the shielding data instead of being prompted for the sensitive information.

**How many shielding data files do I need?** A single shielding data file can be used to create every shielded VM. If, however, a given shielded VM requires that any of the four items be different, then an additional shielding data file is necessary. For example, you might have one shielding data file for your IT department and a different shielding data file for the HR department because their initial administrator password and RDP certificates differed.

While using separate shielding data files for each shielded VM is possible, it is not necessarily the optimal choice and should be done for the right reasons. For example, if every shielded VM needs to have a different administrator password, consider instead using a password management service or tool such as [Microsoft's Local Administrator Password Solution (LAPS)](https://www.microsoft.com/download/details.aspx?id=46899).

## Creating a shielded VM on a virtualization fabric

There are several options for creating a shielded VM on a virtualization fabric (the following is relevant for both shielded and encryption-supported VMs):

1. Create a shielded VM in your environment and upload it to the virtualization fabric
2. Create a new shielded VM from a signed template on the virtualization fabric
3. Shield an existing VM (the existing VM must be generation 2 and must be running Windows Server 2012 or later)

Creating new VMs from a template is normal practice. However, since the template disk that is used to create new Shielded VM resides on the virtualization fabric, additional measures are necessary to ensure that it has not been tampered with by a malicious fabric administrator or by malware running on the fabric. This problem is solved using signed template disks—signed template disks and their disk signatures are created by trusted administrators or the VM owner. When a shielded VM is created, the template disk's signature is compared with the signatures contained within the specified shielding data file. If any of the shielding data file's signatures match the template disk's signature, the deployment process continues. If no match can be found, the deployment process is aborted, ensuring that VM secrets will not be compromised because of an untrustworthy template disk.

When using signed template disks to create shielded VMs, two options are available:

1. Use an existing signed template disk that is provided by your virtualization provider. In this case, the virtualization provider maintains signed template disks.
2. Upload a signed template disk to the virtualization fabric. The VM owner is responsible for maintaining signed template disks.