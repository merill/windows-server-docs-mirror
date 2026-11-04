---
layout: Conceptual
title: Distribute certificates to Windows devices by using Group Policy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/distribute-certificates-group-policy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to distribute certificates to Windows devices by using Group Policy.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2024-02-16T00:00:00.0000000Z
locale: en-us
document_id: 3e56732d-6765-0469-fbf0-5fe8312c52eb
document_version_independent_id: 3e56732d-6765-0469-fbf0-5fe8312c52eb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/distribute-certificates-group-policy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/distribute-certificates-group-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/distribute-certificates-group-policy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f10e9f9b-08e7-bfb1-9a83-4fd32f00ecda
---

# Distribute certificates to Windows devices by using Group Policy | Microsoft Learn

You can distribute certificates that chain to a trusted root in an Active Directory domain to Windows devices by using Group Policy.

## Prerequisites

Before you begin, you need:

- A certificate with the private key. If you need to export a certificate, see [Export a certificate with its private key](export-certificate-private-key).
- An Active Directory domain controller with the **Group Policy Management** snap-in installed, or a device with Remote Server Administration Tools (RSAT) installed that can connect to a domain controller.
- An Active Directory domain with an account that is a member of the **Domain Admins** or **Enterprise Admins** domain security group. For more information about using the appropriate accounts and group memberships, see [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

## Import certificates to Group Policy

1. On a domain controller or device with RSAT installed, start the **Group Policy Management** snap-in.
2. Find an existing Group Policy Object (GPO) or create a new GPO for the certificate settings. Ensure that the GPO is associated with the domain, site, or organizational unit (OU) where the appropriate user and computer accounts reside.
3. Right-click the GPO, then select **Edit**.
4. In the console tree, open **Computer Configuration &gt; Policies &gt; Windows Settings &gt; Security Settings &gt; Public Key Policies**, right-click the store you want to import the certificate to, such as **Trusted Root Certification Authorities**, then select **Import**.
5. On the screen **Welcome to the Certificate Import Wizard**, select **Next**.
6. For **File to Import**, enter or browse to the path to the appropriate certificate files, for example `\\fs1\c$\fs1.cer`, then select **Next**.
7. For **Private key protection**, enter the password for the private key and select **Include all extended properties**, then select **Next**.
8. For **Certificate Store**, select **Place all certificates in the following store** and browse to the certificate store you want to store the certificate, then select **Next**.
9. Review the summary, then select **Finish**.
10. Once you import the certificate, apply the policy to your devices, then restart them for the settings to take effect.