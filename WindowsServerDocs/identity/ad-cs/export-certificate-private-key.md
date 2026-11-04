---
layout: Conceptual
title: Export a certificate with its private key in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/export-certificate-private-key
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to export a certificate with its private key.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-14T00:00:00.0000000Z
locale: en-us
document_id: 8c4005c8-6ce5-bc1e-239d-fac8cff1167d
document_version_independent_id: 8c4005c8-6ce5-bc1e-239d-fac8cff1167d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/export-certificate-private-key.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/export-certificate-private-key
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/export-certificate-private-key.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c19c8e0d-56fc-5791-2145-6687daeacd2a
---

# Export a certificate with its private key in Windows Server | Microsoft Learn

If you already have a certificate installed on a Windows device and you want to install the same certificate on a Windows device that requires a private key, you can export the certificate with the private key. This article describes how to export a certificate from the Windows certificate stores of the local computer with the private key.

## Prerequisites

Before you begin, you need:

- A certificate installed with the private key to a certificate store of the local computer.
- An Active Directory domain with an account that is a member of the **Domain Admins** or **Enterprise Admins** domain security group. For more information about using the appropriate accounts and group memberships, see [Active Directory security groups](/en-us/windows-server/identity/ad-ds/manage/understand-security-groups).

## Export a certificate from the Windows certificate stores with the private key

To export a certificate from the Windows certificate stores with the private key:

1. Open the certificate management console for the local computer by running the following command. Some methods of running this command are from the *Start menu*, the Windows *Run* prompt, PowerShell prompt, or command prompt.

    ```cmd
    certlm.msc
    ```
2. In the console tree, navigate to the certificate you want to export.
3. Right-click the certificate, select **All Tasks**, and then select **Export**.
4. On the screen **Welcome to the Certificate Export Wizard**, select **Next**.
5. To export the private key, select **Yes, export the private key**, then select **Next**.
6. For the file format, select **Personal Information Exchange - PKCS #12 (.PFX)**. Check the box for **Include all certificates in the certification path if possible**, to include the whole certificate chain, then select **Next**.
7. Check the box to enter and confirm a password to protect the private key, and select **AES256-SHA256** for the encryption method, then select **Next**. It's important to guard the security of the private key.
8. Enter or browse to the file path, then select **Next**.
9. Review the summary, then select **Finish**.

Once the certificate is exported, you can import it to another device that requires the certificate with private key.