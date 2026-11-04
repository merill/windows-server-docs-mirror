---
layout: Conceptual
title: Supported Windows security configurations for Remote Desktop Services VDI | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-vdi-supported-config
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Provides information about supported configurations for Windows VDI with RDS in Windows Server.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: concept-article
author: robinharwood
locale: en-us
document_id: cc67d0f1-d552-ed54-1a94-e0bf2b6168a6
document_version_independent_id: 7c5eb702-bc62-b2bf-3a45-55bc43692eaa
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-vdi-supported-config.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-vdi-supported-config
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-vdi-supported-config.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 20e5fa4a-34f2-fff8-b4c8-8c18d3ad2886
---

# Supported Windows security configurations for Remote Desktop Services VDI | Microsoft Learn

Windows and Windows Server have new layers of protection built into the operating system to:

- Safeguard against security breaches
- Help block malicious attacks
- Enhance the security of virtual machines, applications, and data.

Note

- Features like Credential Guard may have performance implication on user density. Ensure to test your scenarios. Learn more about other considerations for [credential guard configuration](/en-us/windows/security/identity-protection/credential-guard/considerations-known-issues).
- Make sure to review the [Remote Desktop Services supported configuration information](rds-supported-config).

The following table outlines which of these new features are supported in a VDI deployment using RDS.

| VDI collection type | Managed pooled | Managed personal | Unmanaged pooled | Unmanaged personal |
| --- | --- | --- | --- | --- |
| [Credential Guard](/en-us/windows/security/identity-protection/credential-guard/credential-guard) | Yes | Yes | Yes | Yes |
| [Device Guard](/en-us/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide) | Yes | Yes | Yes | Yes |
| [Remote Credential Guard](/en-us/windows/security/identity-protection/remote-credential-guard) | No | No | No | No |
| [Shielded & Encryption Supported VMs](../../security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms) | No | No | Encryption supported VMs with extra configuration | Encryption supported VMs with extra configuration |

## Remote Credential Guard

Remote Credential Guard is only supported for direct connections to the target machines and not for the ones via Remote Desktop Connection Broker and Remote Desktop Gateway.

Note

If you have a Connection Broker in a single-instance environment, and the DNS name matches the computer name, you may be able to use Remote Credential Guard, although this isn't supported.

## Shielded VMs and Encryption Supported VMs

Shielded VMs aren't supported in Remote Desktop Services VDI.

For leveraging Encryption Supported VMs:

- Use an unmanaged collection and a provisioning technology outside of the Remote Desktop Services collection creation process to provision the virtual machines.
- User Profile Disks aren't supported as they rely on differential disks