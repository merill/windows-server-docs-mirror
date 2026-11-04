---
layout: Conceptual
title: Certificates and Trust Management in Windows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/certificate-trust
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how the Microsoft Root Certificate Program distributes trusted root certificates in Windows, even in disconnected environments. Discover how to manage certificates effectively.
author: robinharwood
ms.author: roharwoo
ms.topic: concept-article
ms.date: 2025-05-21T00:00:00.0000000Z
locale: en-us
document_id: 92a17e02-b462-33b1-cea2-5482051d9fe1
document_version_independent_id: 92a17e02-b462-33b1-cea2-5482051d9fe1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/certificate-trust.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/certificate-trust
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/certificate-trust.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5d9c4b94-c832-d468-92c1-0db5a71e30e2
---

# Certificates and Trust Management in Windows | Microsoft Learn

The Microsoft Root Certificate Program enables distribution of trusted and untrusted root certificates within Windows operating systems. This article explains how certificates and trust lists are managed in Windows, and the benefits of automatic updates for maintaining security. For more information about the list of members in Windows Root Certificate Program, see [List of Participants - Microsoft Trusted Root Program](/en-us/security/trusted-root/participants-list).

Trusted and untrusted root certificates are used by Windows operating systems and applications as a reference when determining whether public key infrastructure (PKI) hierarchies and digital certificates are trustworthy. Untrusted root certificates are certificates that are publicly known to be fraudulent. Trusted and untrusted root certificates functionality works across all environments, whether connected or disconnected.

Trusted and untrusted root certificates are contained in a certificate trust list (CTL). When you want to distribute root certificates, you use a CTL. Windows Server features automatic daily update functionality that includes downloads of latest CTLs. The list of trusted and untrusted root certificates are called the Trusted CTL and Untrusted CTL, respectively. For more information, see [Announcing the automated updater of untrustworthy certificates and keys](https://blogs.technet.com/b/pki/archive/2012/06/12/announcing-the-automated-updater-of-untrustworthy-certificates-and-keys.aspx).

Servers and clients access the Windows Update site to update the CTL using the automatic daily update mechanism (CTL updater) discussed in this article. You can take advantage of CTL updater functionality by installing the appropriate software updates. See the article [Configure Trusted Roots and Disallowed Certificates](configure-trusted-roots-disallowed-certificates) for guidance in installing the software updates on supported operating systems discussed in this article.

## Automatic certificate trust list updates

By default, Windows downloads the CTLs from the Internet via an automatic mechanism called the CTL Updater. The public URLs used by the CTL Updater can be made available to clients:

- `http://ctldl.windowsupdate.com/msdownload/update/v3/static/trustedr/en/disallowedcertstl.cab`
- `http://ctldl.windowsupdate.com/msdownload/update/v3/static/trustedr/en/authrootstl.cab`

Automatic update functionality also can be disabled if necessary, although isn't recommended.

Alternately, you also can create a Group Policy administrative templates (ADMX policy) to redirect to an internal server for updates.

The registry location where trusted and untrusted CTLs are stored as follows:

- `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates\AuthRoot\AutoUpdate\EncodedCtl`
- `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates\AuthRoot\AutoUpdate\DisallowedCertEncodedCtl`

## Benefits of CTL Updater

Automatic update functionality using the CTL Updater delivers several benefits:

- **Registry settings for storing CTLs** New settings enable changing the location for uploading trusted or untrusted CTLs from the Windows Update site to a shared location in an organization. See [Registry Settings Modified](configure-trusted-roots-disallowed-certificates#registry-settings-modified).
- **Synchronization options** If the URL for the Windows Update site is moved to a local shared folder, the local shared folder must be synchronized with the Windows Update folder. This software update adds a set of options in the Certutil tool that you use to enable synchronization. For more information, see the [Certutil -syncWithWU](../../administration/windows-commands/certutil) Windows command reference.
- **Tool to select trusted root certificates** This software update introduces a tool for managing the set of trusted root certificates in your enterprise environment. You can view and select the set of trusted root certificates, export them to a serialized certificate store, and distribute them by using Group Policy. For more information, see the [Certutil -generateSSTFromWU SSTFile](../../administration/windows-commands/certutil) Windows command reference.
- **Independent configurability** The automatic update mechanism for trusted and untrusted certificates are independently configurable; you can use the automatic update mechanism to download only the untrusted CTLs and manage your own list of trusted CTLs. For more information, see [Registry settings modified](configure-trusted-roots-disallowed-certificates#registry-settings-modified).

See [Configure Trusted Roots and Disallowed Certificates](configure-trusted-roots-disallowed-certificates) for guidance in installing the software updates on supported operating systems discussed in this article.

Automatic update functionality can be disabled if necessary, however it isn't recommended.