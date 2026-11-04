---
layout: Conceptual
title: Post-Quantum Cryptography in AD CS overview - Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/post-quantum-cryptography-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about Post-Quantum Cryptography support in Active Directory Certificate Services, including algorithms available today and those planned for future releases.
author: robinharwood
ms.author: roharwoo
ms.reviewer: Tjha
ms.topic: concept-article
ms.date: 2026-05-12T00:00:00.0000000Z
ai-usage: ai-generated
locale: en-us
document_id: b328604e-ca22-646c-b6a1-af646d51e03a
document_version_independent_id: b328604e-ca22-646c-b6a1-af646d51e03a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/post-quantum-cryptography-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/post-quantum-cryptography-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/post-quantum-cryptography-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: f2f353ec-3ba0-0dfc-97cd-bddb58fe3e20
---

# Post-Quantum Cryptography in AD CS overview - Windows Server | Microsoft Learn

Post-Quantum Cryptography (PQC) in Active Directory Certificate Services (AD CS) enables issuing and managing certificates with algorithms designed to resist attacks from quantum-capable computers.

AD CS currently supports ML-DSA. This article describes the scope of PQC support in AD CS and the foundational requirements that apply across algorithms.

## Why Post-Quantum Cryptography matters

Certificates issued by AD CS protect critical enterprise operations, including domain authentication, code signing, Transport Layer Security (TLS), and device enrollment. Today, many of these certificates rely on asymmetric public-key algorithms such as RSA and Elliptic Curve Digital Signature Algorithm (ECDSA), which might be vulnerable to sufficiently powerful quantum computers. The risk is already real for two reasons:

- **Long-lived trust.** Root CA certificates, code signing certificates, and other long-lived signing identities issued today must remain trustworthy throughout their full validity period. An attacker can forge signatures that use a quantum-vulnerable algorithm once a quantum computer becomes available.
- **Harvest now, decrypt later.** Threat actors capture and store encrypted data today to decrypt it later, once quantum capabilities mature.

## Pure and composite post-quantum certificates

Post-quantum certificates can take one of two forms:

**Pure.** The certificate uses a single post-quantum algorithm. All relying parties in the trust chain must understand the post-quantum algorithm to validate signatures.

**Composite.** The certificate combines a classical algorithm (such as ECDSA or RSA) with a post-quantum algorithm (such as ML-DSA-65). The composite signature contains both a classical signature and a post-quantum signature, and both must validate for the certificate to be trusted. An attacker must break both algorithms to forge a composite signature. The certificate remains secure as long as either underlying algorithm remains unbroken. Composite certificates are larger than pure or classical certificates, and relying parties must understand the composite format and both algorithms to validate them.

## PQC algorithms supported in AD CS

AD CS adopts the post-quantum algorithms standardized by the National Institute of Standards and Technology (NIST). Support ships in phases.

| Algorithm | Standard | Purpose | AD CS support |
| --- | --- | --- | --- |
| **ML-DSA** | [FIPS 204](https://csrc.nist.gov/pubs/fips/204/final) | Digital signatures | Available (Phase 1) |
| **ML-KEM** | [FIPS 203](https://csrc.nist.gov/pubs/fips/203/final) | Key encapsulation | Planned (Phase 2) |
| **Composite ML-DSA** | [IETF draft](https://datatracker.ietf.org/doc/draft-ietf-lamps-pq-composite-sigs/) | Classical + PQ digital signatures | Planned (Phase 2) |
| **Composite ML-KEM** | [IETF draft](https://datatracker.ietf.org/doc/draft-ietf-lamps-pq-composite-kem/) | Classical + PQ key encapsulation | Planned (Phase 2) |

Microsoft plans to extend support across all relevant AD CS role services, including the Certificate Enrollment Policy Web Service (CEP), Certificate Enrollment Web Service (CES), the Network Device Enrollment Service (NDES), and the Online Responder (OCSP).

## Platform requirements

PQC support in AD CS depends on the following prerequisites. These requirements apply to all PQC algorithms as they become available.

- **Cryptography API: Next Generation (CNG) providers.** All PQC algorithms require CNG key storage providers. AD CS doesn't support legacy Cryptographic Service Providers (CSPs).
- **Up-to-date Windows servers and clients.** PQC support begins at the platform versions listed in the following table. Some algorithms might require later versions - see each algorithm's overview article for exact requirements.

| Component | OS version |
| --- | --- |
| AD CS servers | Windows Server 2025 with the 2026-05 Security update ([KB5087539](https://support.microsoft.com/help/5087539)) or later installed. |
| Client | Windows 11, version 24H2 and version 25H2 with the 2025-10 non-security update ([KB5067036](https://support.microsoft.com/help/5067036)) or later installed. |