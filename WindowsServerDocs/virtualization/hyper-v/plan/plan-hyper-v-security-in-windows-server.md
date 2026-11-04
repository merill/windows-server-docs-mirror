---
layout: Conceptual
title: Plan for Hyper-V security in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/plan/plan-hyper-v-security-in-windows-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Provides a list of security considerations for Hyper-V hosts and virtual machines
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2018-08-03T00:00:00.0000000Z
locale: en-us
document_id: d08a577e-a4bc-93df-4d5c-bc2fafedc554
document_version_independent_id: 6df4d1e8-f726-a0cd-08f3-031d4127d95d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/plan/plan-hyper-v-security-in-windows-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/plan/plan-hyper-v-security-in-windows-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/plan/plan-hyper-v-security-in-windows-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 20707363-c2b5-1e65-eaa6-c0ab03423536
---

# Plan for Hyper-V security in Windows Server | Microsoft Learn

Secure the Hyper-V host operating system, the virtual machines, configuration files, and virtual machine data. Use the following list of recommended practices as a checklist to help you secure your Hyper-V environment.

## Secure the Hyper-V host

- **Keep the host OS secure.**

    - Minimize the attack surface by using the minimum Windows Server installation option that you need for the management operating system. For more information, see the [Installation Options section](../../../get-started/install-upgrade-migrate) of the Windows Server technical content library. We don't recommend that you run production workloads on Hyper-V on Windows 10.
    - Keep the Hyper-V host operating system, firmware, and device drivers up to date with the latest security updates. Check your vendor's recommendations to update firmware and drivers.
    - Don't use the Hyper-V host as a workstation or install any unnecessary software.
    - Remotely manage the Hyper-V host. If you must manage the Hyper-V host locally, use Credential Guard. For more information, see [Protect derived domain credentials with Credential Guard](/en-us/windows/access-protection/credential-guard/credential-guard).
    - Enable code integrity policies. Use virtualization-based security protected Code Integrity services. For more information, see [Device Guard Deployment Guide](/en-us/windows/device-security/device-guard/device-guard-deployment-guide).
- **Use a secure network.**

    - Use a separate network with a dedicated network adapter for the physical Hyper-V computer.
    - Use a private or secure network to access VM configurations and virtual hard disk files.
    - Use a private/dedicated network for your live migration traffic. Consider enabling IPSec on this network to use encryption and secure your VM's data going over the network during migration. For more information, see [Set up hosts for live migration without Failover Clustering](../deploy/set-up-hosts-for-live-migration-without-failover-clustering).
- **Secure storage migration traffic.**

    Use SMB 3.0 for end-to-end encryption of SMB data and data protection tampering or eavesdropping on untrusted networks. Use a private network to access the SMB share contents to prevent man-in-the-middle attacks. For more information, see [SMB Security Enhancements](/en-us/windows-server/storage/file-server/smb-security).
- **Configure hosts to be part of a guarded fabric.**

    For more information, see [Guarded fabric](../../../security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms-top-node).
- **Secure devices.**

    Secure the storage devices where you keep virtual machine resource files.
- **Secure the hard drive.**

    Use BitLocker Drive Encryption to protect resources.
- **Harden the Hyper-V host operating system.**

    Use the baseline security setting recommendations described in the [Windows Server Security Baseline](/en-us/windows/device-security/windows-security-baselines).
- **Grant appropriate permissions.**

    - Add users that need to manage the Hyper-V host to the Hyper-V administrators group.
    - Don't grant virtual machine administrators permissions on the Hyper-V host operating system.
- **Configure anti-virus exclusions and options for Hyper-V.**

    Windows Defender already has [automatic exclusions](/en-us/windows/security/threat-protection/windows-defender-antivirus/configure-server-exclusions-windows-defender-antivirus) configured. For more information about exclusions, see [Recommended antivirus exclusions for Hyper-V hosts](https://support.microsoft.com/kb/3105657).
- **Don't mount unknown VHDs.** This can expose the host to file system level attacks.
- **Don't enable nesting in your production environment unless it's required.**

    If you enable nesting, don't run unsupported hypervisors on a virtual machine.

For more secure environments:

- **Use hardware with a Trusted Platform Module (TPM) 2.0 chip to set up a guarded fabric.**

    For more information, see [System requirements for Hyper-V on Windows Server 2016](../host-hardware-requirements).

## Secure virtual machines

- **Create generation 2 virtual machines for supported guest operating systems.**

    For more information, see [Generation 2 security settings](../learn-more/generation-2-virtual-machine-security-settings-for-hyper-v).
- **Enable Secure Boot.**

    For more information, see [Generation 2 security settings](../learn-more/generation-2-virtual-machine-security-settings-for-hyper-v).
- **Keep the guest OS secure.**

    - Install the latest security updates before you turn on a virtual machine in a production environment.
    - Install integration services for the supported guest operating systems that need it and keep it up to date. Integration service updates for guests that run supported Windows versions are available through Windows Update.
    - Harden the operating system that runs in each virtual machine based on the role it performs. Use the baseline security setting recommendations that are described in the [Windows Security Baseline](/en-us/windows/device-security/windows-security-baselines).
- **Use a secure network.**

    Make sure virtual network adapters connect to the correct virtual switch and have the appropriate security setting and limits applied.
- **Store virtual hard disks and snapshot files in a secure location.**
- **Secure devices.**

    Configure only required devices for a virtual machine. Don't enable discrete device assignment in your production environment unless you need it for a specific scenario. If you do enable it, make sure to only expose devices from trusted vendors.
- **Configure antivirus, firewall, and intrusion detection software** within virtual machines as appropriate based on the virtual machine role.
- **Enable virtualization based security for guests that run Windows 10 or Windows Server 2016 or later.**

    For more information, see the [Device Guard Deployment Guide](/en-us/windows/device-security/device-guard/device-guard-deployment-guide).
- **Only enable Discrete Device Assignment if needed for a specific workload**.

    Due to the nature of passing through a physical device, work with the device manufacturer to understand if it should be used in a secure environment.

For more secure environments:

- **Deploy virtual machines with shielding enabled and deploy them to a guarded fabric.**

    For more information, see [Generation 2 security settings](../learn-more/generation-2-virtual-machine-security-settings-for-hyper-v) and [Guarded fabric](../../../security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms-top-node).