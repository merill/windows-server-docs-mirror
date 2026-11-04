---
layout: Conceptual
title: KMS Hardware-Secured Activation in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/kms-hardware-secured
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: Learn how KMS Hardware-Secured activation strengthens Windows Server volume activation with TPM 2.0 attestation and device integrity.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2026-08-05T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: a77fc1cc-457f-9b98-5a7c-44fea68930fc
document_version_independent_id: a77fc1cc-457f-9b98-5a7c-44fea68930fc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/kms-hardware-secured.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/kms-hardware-secured
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/kms-hardware-secured.md
platformId: 0aa64a79-e260-1404-d236-de827ca2a528
---

# KMS Hardware-Secured Activation in Windows Server | Microsoft Learn

KMS Hardware-Secured activation is a strengthened form of Key Management Services (KMS) volume activation that uses Trusted Platform Module (TPM) 2.0 attestation to confirm that activation requests come from trusted, hardware-backed environments. It binds activation to the integrity of the device, which mitigates spoofing and helps ensure that only verified, validated hosts participate in activation.

A KMS host that isn't hardware-secured relies on software alone to validate activation, which leaves your environment more exposed to unverified or emulated KMS hosts.

Beginning with the 2026-08 Cumulative Update for Windows Server 2025, KMS host readiness messaging tells you whether a host meets the hardware-based security requirements, so you can check and prepare your environment. The activation changes that build on hardware-based trust apply to future versions of Windows Server. To learn more, see [Strengthening Key Management Service (KMS) with hardware-based trust](https://techcommunity.microsoft.com/blog/windows-itpro-blog/strengthening-key-management-service---kms-with-hardware-based-trust/4539465).

After you read this article, you can identify whether a KMS host is Hardware-Secured, understand how it differs from a host that isn't Hardware-Secured, and know which requirements your environment must meet.

## How KMS Hardware-Secured activation works

KMS Hardware-Secured activation uses TPM 2.0 attestation to establish trust in the KMS host before it participates in activation. The TPM provides a hardware-backed measurement of the host, and attestation validates that measurement so that activation requests originate from a trusted, verified environment.

TPM attestation works in three parts:

- **Hardware identity**: The KMS host uses TPM-backed attestation to prove its hardware identity, which Microsoft verifies before the host activates devices.
- **Platform integrity**: The TPM confirms the KMS host's integrity.
- **Activation flow**: After verification, the KMS host securely serves activation requests for Windows devices.

This approach ties activation to a trusted host, not just to a software configuration that someone can copy or spoof.

Because the device hardware anchors trust rather than software configuration alone, KMS Hardware-Secured activation:

- Binds activation to the device's integrity.
- Resists tampering by binding activation secrets to hardware.
- Mitigates spoofing and the use of emulated or unverified KMS hosts.
- Provides perpetual activation without periodic renewal.

## KMS hardware-secured and KMS not hardware-secured hosts

A KMS host operates in one of two states. A KMS hardware-secured host adds a hardware root of trust, whereas a KMS not hardware-secured host relies on software alone. Understanding the difference helps you plan the right path for your environment.

| Aspect | KMS hardware-secured host | KMS not hardware-secured host |
| --- | --- | --- |
| Basis of trust | Hardware root of trust established through TPM 2.0 attestation. | Software only, which is vulnerable to spoofing. |
| Hardware requirement | TPM 2.0 installed and enabled. | None. |
| Activation renewal | Perpetual activation with no renewal required. | Standard KMS activation on Windows Server 2025. A future version of Windows Server might require periodic renewal. |
| When to use | Recommended state, for the strongest activation trust and the least ongoing maintenance. | Transition state, while you prepare hardware and complete the move to a KMS hardware-secured host. |

### When to choose a KMS hardware-secured host

A *KMS hardware-secured* host is the recommended state. This host uses TPM 2.0 attestation to establish hardware-based trust and provides perpetual activation without renewal. Choose this state when you want the strongest activation trust and the least ongoing maintenance.

### What to expect on a KMS not hardware-secured host

A non-hardware-secured KMS host uses standard KMS activation on Windows Server 2025 and continues to activate clients as it does today. In a future version of Windows Server, a non-hardware-secured host might require periodic renewal to keep clients activated. Prepare your hardware now to adopt KMS hardware-secured activation ahead of that change. To learn more, see [Strengthening Key Management Service (KMS) with hardware-based trust](https://techcommunity.microsoft.com/blog/windows-itpro-blog/strengthening-key-management-service---kms-with-hardware-based-trust/4539465).

## Requirements for a KMS hardware-secured host

To operate as a KMS hardware-secured host, a server must meet all the following requirements:

- The host has a TPM 2.0 chip installed and enabled.
- The server hardware is certified in the [Windows Server Catalog](https://www.windowsservercatalog.com/).

## Environment readiness for KMS hardware-secured activation

To prepare for KMS hardware-secured activation, assess what you have today, watch for readiness signals, and plan any hardware changes you need.

### Assess your current KMS setup

Start by understanding your existing KMS infrastructure so you know which hosts already qualify and which need changes:

- Inventory your KMS hosts, including both physical and virtual hosts.
- Verify that each host has a TPM 2.0 chip that's installed and enabled.
- Confirm that each host's server hardware is certified in the Windows Server Catalog.

To confirm that a host supports the TPM attestation capability, run the following command in an elevated PowerShell session:

```powershell
Get-TpmSupportedFeature -FeatureList "Key Attestation"
```

A response that shows `Key Attestation` confirms the server supports the TPM attestation capability for KMS Hardware-Secured activation.

### Monitor readiness signals

Beginning with the 2026-08 Cumulative Update for Windows Server 2025, KMS host readiness messaging helps you plan ahead. This messaging is informational and doesn't affect activation. Clients continue to activate as they do today. The messaging shows which hosts already meet the hardware-based security requirements, so you can prepare for KMS Hardware-Secured activation in a future version of Windows Server. To learn more about the change, see [Strengthening Key Management Service (KMS) with hardware-based trust](https://techcommunity.microsoft.com/blog/windows-itpro-blog/strengthening-key-management-service---kms-with-hardware-based-trust/4539465).

Readiness signals appear on two surfaces:

- **Command line**: Running `slmgr /dlv` shows either "This device is eligible to serve as a KMS host with hardware-based security." or "This device doesn't meet the requirements for using a KMS host with hardware-based security."
- **Event logs**: Warning entries appear under **Applications and Services Logs** &gt; **Key Management Service**.

### Plan your hardware transition

For hosts that don't yet qualify, plan the changes that move them to a KMS Hardware-Secured state:

- Install and enable TPM 2.0 on hosts that don't have it.
- Move to Windows Server–certified hardware where the current hardware isn't certified.
- Validate readiness after you make hardware changes to confirm the host qualifies as a KMS Hardware-Secured host.