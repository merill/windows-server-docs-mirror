---
layout: Conceptual
title: EAP - What's changed in Windows 11 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/extensible-authentication-protocol/windows-11-changes
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This article presents information about the changes in Windows 11 for Extensible Authentication Protocol (EAP) settings.
author: robinharwood
ms.author: roharwoo
ms.topic: concept-article
ms.date: 2024-06-27T00:00:00.0000000Z
locale: en-us
document_id: c8121181-78f8-a648-f02b-b70d9ee0aff9
document_version_independent_id: c8121181-78f8-a648-f02b-b70d9ee0aff9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/extensible-authentication-protocol/windows-11-changes.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/extensible-authentication-protocol/windows-11-changes
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/extensible-authentication-protocol/windows-11-changes.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 94098b98-5364-7823-bc52-b2f07c82c373
---

# EAP - What's changed in Windows 11 | Microsoft Learn

Windows 11 supports WPA3-Enterprise, a Wi-Fi security standard that defines a set of requirements around server certificate validation for EAP authentication. Windows 11 also supports TLS 1.3 by default. This article details the changes in EAP behavior in Windows 11 due to these features.

## Updated server certificate validation behavior in Windows 11

In previous Windows releases, including Windows 10, the server certificate validation logic varied between EAP methods. In Windows 11, we've adjusted all EAP methods to behave in a consistent and predictable way, which is also consistent with the WPA3-Enterprise specification. This new behavior applies to any EAP authentication using the first party EAP methods that ship with Windows, including Wi-Fi, Ethernet, and VPN scenarios.

Windows will trust the server certificate if one of the following conditions is met:

- The server certificate thumbprint has been added to the profile. 
    Note

    If the user is connecting without a preconfigured profile or if user prompts for server validation are enabled in the profile, the thumbprint will automatically be added to the profile if the user accepts the server through the UI prompt.
- All of the following conditions are met:
    1. The server certificate chain is trusted by the machine or user.
        - This trust is based on the root certificate being present in the machine or user trusted root store, depending on the OneX [authMode](/en-us/windows/win32/nativewifi/onexschema-onex-element).
    2. The trusted root certificate thumbprint has been added to the profile.
    3. If server name validation is enabled (recommended), the name matches what is specified in the profile.
        - For more information, see [Server validation](network-access#server-certificate-validation) for more information about configuring server name validation in the profile.

### Potential issues upgrading from Windows 10 to Windows 11

In Windows 10, under certain circumstances, PEAP and EAP-TLS authentications could successfully validate the server based solely on the presence of the trusted root certificate in the Windows trusted root store. If you observe that an EAP authentication is consistently failing after upgrading to Windows 11, check the connection profile to ensure they adhere to the new requirements for the behavior previously described.

In most cases, specifying the trusted root certificate thumbprint in the profile is enough to address the issue, assuming the root certificate is already present in the trusted root store.

Another thing to note is that server name matching is case sensitive in Windows 11 version 21H2 (build number 22000). The server name matching was adjusted back to be case insensitive in Windows 11 version 22H2 (build number 22621). If you're using server name validation, ensure that the name specified in the profile matches the server name exactly or upgrade to Windows 11 version 22H2 or later.

### Wildcard certificates

In Windows 11, Windows will no longer immediately reject server certificates that contain a wildcard (`*`) in the certificate Common Name (CN). However, it's recommended that DNS name in the Subject Alternate Name (SubjectAltName/SAN) extension field is used, as Windows will ignore the CN components when checking for a DNS match if the SAN contains a DNS name choice. The SubjectAltName DNS name supports a wildcard in Windows 11, as it has on prior versions of Windows.

Note

All of the conditions described above for trusting the server certificate still apply for wildcard certificates.

## WPA3-Enterprise Trust Override Disable (TOD) policies

WPA3-Enterprise requires that the device trusts the server certificate - if server validation fails, Windows won't enter into Phase 2 of the EAP exchange. If the server certificate isn't trusted, the user will be prompted to accept the server certificate. This behavior is called **User Override of Server Certificate** (UOSC). To disable UOSC for machines without a preconfigured profile, it's possible to set **Trust Override Disable** (TOD) policies on the server certificate.

The TOD policies are indicated in the **Certificate Policies** extension of the server certificate by including a specific OID. The following policies are supported:

- TOD-STRICT: If the server certificate isn't trusted, the user won't be prompted to accept the server certificate. The authentication will fail. This policy has the OID `1.3.6.1.4.1.40808.1.3.1`.
- TOD-TOFU (Trust On First Use): If the server certificate isn't trusted, the user will be prompted to accept the server certificate on the first connection only. If the user accepts the server certificate, the server certificate will be added to the profile, and the authentication continues. However, subsequent connections will require the server certificate to be trusted and will not prompt again. This policy has the OID `1.3.6.1.4.1.40808.1.3.2`.

## TLS 1.3

Windows 11 enabled TLS 1.3 by default systemwide, and while EAP-TLS used TLS 1.3, PEAP and EAP-TTLS continued to use TLS 1.2. Windows 11 version 22H2 (build number 22621) updated these methods to use TLS 1.3 by default.

### Known issues with TLS 1.3 and Windows 11

- NPS doesn't support TLS 1.3 at this time.
- Some older versions of third-party RADIUS servers may incorrectly advertise TLS 1.3 support. If you're experiencing issues with authenticating EAP-TLS with TLS 1.3 with Windows 11 22H2, ensure the RADIUS server is patched and up to date or has TLS 1.3 disabled.
- Session resumption is not currently supported. Windows clients will always do a full authentication.