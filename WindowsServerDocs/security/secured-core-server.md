---
layout: Conceptual
title: What is Secured-core server for Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/secured-core-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how Secured-core server by Windows Server hardware OEMs offers advanced protection of your operating system environment.
author: robinharwood
ms.author: roharwoo
ms.topic: concept-article
ms.date: 2023-04-06T00:00:00.0000000Z
ms.custom: template-overview, team=cloud_advocates, kr2b-contr-experiment
ms.contributors: socuff-01282022
locale: en-us
document_id: f39b84e8-6e28-7a71-6bd8-6deea5608c92
document_version_independent_id: d323d740-16d8-21e0-0818-2789c9283bf1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/secured-core-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/secured-core-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/secured-core-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 54752097-74bf-030a-8904-1a3ba2f2cd89
---

# What is Secured-core server for Windows Server | Microsoft Learn

Secured-core is a collection of capabilities that offers built-in hardware, firmware, driver and operating system security features. The protection provided by Secured-core systems begins before the operating system boots and continues whilst running. Secured-core server is designed to deliver a secure platform for critical data and applications.

Secured-core server is built on three key security pillars:

- Creating a hardware backed root of trust.
- Defense against firmware level attacks.
- Protecting the OS from the execution of unverified code.

## What makes a Secured-core server

The Secured-core initiative started with Windows PCs through a deep collaboration between Microsoft and PC manufacturing partners to provide the most elevated Windows security ever. Microsoft has expanded the partnership further with server manufacturing partners to help ensure Windows Server delivers a secure operating system environment.

Windows Server integrates closely with hardware to provide increasing levels of security:

- Recommended baseline: The recommended minimum for all systems to provide foundational system integrity using TPM 2.0 for a hardware root of trust and Secure Boot. TPM2.0 and Secure boot are required for Windows Server hardware certification. To learn more, see [Microsoft raises the security standard for next major Windows Server release](https://cloudblogs.microsoft.com/windowsserver/2020/06/11/microsoft-raises-the-security-standard-for-next-major-windows-server-release/)
- Secured-core server: Recommended for systems and industries requiring higher levels of assurance. Secured-core server builds on the previous features and uses advanced processor capabilities to provide protection from firmware attacks.

The following table shows how each security concept and feature are used to create a Secured-core server.

| Concept | Feature | Requirement | Recommended baseline | Secured-Core server |
| --- | --- | --- | --- | --- |
| **Create a hardware backed root of trust** |  |  |  |  |
|  | Secure Boot | Secure Boot is enabled in the Unified Extensible Firmware Interface (UEFI) BIOS by default. | ✓ | ✓ |
|  | Trusted Platform Module (TPM) 2.0 | Meet the latest Microsoft requirements for the Trusted Computing Group (TCG) specification. | ✓ | ✓ |
|  | Certified for Windows Server | Demonstrates that a server system meets Microsoft's highest technical bar for security, reliability and manageability. | ✓ | ✓ |
|  | Boot DMA protection | Support on devices that have the Input/Output Memory Management Unit (IOMMU). For example, Intel VT-D or AMD-Vi. |  | ✓ |
| **Defend against firmware level attacks** |  |  |  |  |
|  | System Guard Secure Launch | Enabled in the operating system with Dynamic Root of Trust for Measurement (DRTM) compatible Intel and AMD hardware. |  | ✓ |
| **Protect the OS from execution of unverified code** |  |  |  |  |
|  | Virtualization-based Security (VBS) | Requires the Windows hypervisor, which is only supported on 64-bit processors with virtualization extensions, including Intel VT-X and AMD-v. | ✓ | ✓ |
|  | Hypervisor Enhanced Code Integrity (HVCI) | Hypervisor Code Integrity (HVCI)-compatible drivers plus VBS requirements. | ✓ | ✓ |

### Create a hardware backed root of trust

[UEFI Secure boot](/en-us/windows-hardware/design/device-experiences/oem-secure-boot) is a security standard that protects your servers from malicious rootkits by verifying your systems boot components. Secure boot verifies a trusted author has digitally signed the UEFI firmware drivers and applications. When the server is started, the firmware checks the signature of each boot component including firmware drivers and the OS. If the signatures are valid, the server boots and the firmware gives control to the OS.

To learn more about the boot process, see [Secure the Windows boot process](/en-us/windows/security/information-protection/secure-the-windows-10-boot-process).

TPM 2.0 provides a secure, hardware-backed storage for sensitive keys and data. Every component loaded during the boot process is measured and the measurements stored in the TPM. By verifying the hardware root-of-trust it elevates the protection provided by capabilities like BitLocker, which uses TPM 2.0 and facilitates the creation of attestation-based workflows. These attestation-based workflows can be incorporated into zero-trust security strategies.

Learn more about [Trusted Platform Modules](/en-us/windows/security/information-protection/tpm/trusted-platform-module-overview) and [how Windows uses the TPM](/en-us/windows/security/information-protection/tpm/how-windows-uses-the-tpm).

Along with Secure Boot and TPM 2.0, Windows Server Secured-core uses [Boot DMA protection](/en-us/windows-hardware/design/device-experiences/oem-kernel-dma-protection) on compatible processors that have the Input/Output Memory Management Unit (IOMMU). For example, Intel VT-D or AMD-Vi. With boot DMA protection, systems are protected from Direct Memory Access (DMA) attacks during boot and during the operating system runtime.

### Defend against firmware level attacks

Endpoint protection and detection solutions usually have limited visibility of firmware, given that firmware runs underneath of the operating system. Firmware has a higher level of access and privilege than operating system and hypervisor kernel, making it an attractive target for attackers. Attacks targeting firmware undermine other security measures implemented by the operating system, making it more difficult to identify when a system or user has been compromised.

Beginning with Windows Server 2022, System Guard Secure Launch protects the boot process from firmware attacks by using hardware capabilities from AMD and Intel. With processor support for [Dynamic Root of Trust for Measurement (DRTM) technology](/en-us/windows/security/threat-protection/windows-defender-system-guard/how-hardware-based-root-of-trust-helps-protect-windows#secure-launchthe-dynamic-root-of-trust-for-measurement-drtm), Secured-core servers put firmware in a hardware-backed sandbox helping to limit the effects of vulnerabilities in highly privileged firmware code. System Guard uses the DRTM capabilities that are built into compatible processors to launch the operating system, ensuring the system launches into a trusted stated using verified code.

### Protect the OS from execution of unverified code

Secured-core server uses Virtualization Based Security (VBS) and hypervisor-protected code integrity (HVCI) to create and isolate a secure region of memory from the normal operating system. VBS uses the Windows hypervisor to create a [Virtual Secure Mode (VSM)](/en-us/virtualization/hyper-v-on-windows/tlfs/vsm) to offer security boundaries within the operating system, which can be used for other security solutions.

HVCI, commonly referred to as Memory integrity protection, is a security solution that helps ensure that only signed and trusted code is allowed to execute in the kernel. Using only signed and trusted code prevents attacks that attempt to modify the kernel mode code. For example, attacks that modify drivers, or exploits such as WannaCry that attempt to inject malicious code into the kernel.

To learn more about VBS and hardware requirements, see [Virtualization-based Security](/en-us/windows-hardware/design/device-experiences/oem-vbs).

## Simplified management

You can view and configure the OS security features of Secured-core systems using Windows PowerShell or the security extension in Windows Admin Center. With Azure Local integrated systems, manufacturing partners have further simplified the configuration experience for customers so that Microsoft’s best server security is available right out of the box.

[![Screenshot showing the Windows Admin Center security extension in a browser window with Secured-core enabled.](media/secured-core/windows-admin-center-server.png)](media/secured-core/windows-admin-center-server.png#lightbox)

Learn more about [Windows Admin Center](../manage/windows-admin-center/overview).

## Preventative defense

You can proactively defend against and disrupt many of the paths attackers use to exploit systems by enabling Secured-core functionality. Secured-core server enables advanced security features at the bottom layers of the technology stack, protecting the most privileged areas of the system before many security tools are aware of exploits. It also occurs without the need for extra tasks or monitoring by IT and SecOps teams.

## Begin your Secured-core journey

You can find hardware certified for Secured-core server from the [Windows Server Catalog](https://www.windowsservercatalog.com/), and Azure Local servers in the [Azure Local Catalog](https://azurelocalsolutions.azure.microsoft.com/#/catalog?FeatureSupported=securedCoreServer). These certified servers come fully equipped with industry-leading security mitigations built into the hardware, firmware, and the operating system to help thwart some of the most advanced attack vectors.