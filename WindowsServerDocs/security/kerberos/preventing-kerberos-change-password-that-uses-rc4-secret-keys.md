---
layout: Conceptual
title: Preventing Kerberos change password that use RC4 secret keys | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/kerberos/preventing-kerberos-change-password-that-uses-rc4-secret-keys
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Preventing Kerberos change password that uses RC4 secret keys'
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
locale: en-us
document_id: 9f128b86-49d9-d48a-21dc-16018aff18db
document_version_independent_id: 54aee3ca-7a31-d5c1-2628-b1592bc1a74a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/kerberos/preventing-kerberos-change-password-that-uses-rc4-secret-keys.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/kerberos/preventing-kerberos-change-password-that-uses-rc4-secret-keys
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/kerberos/preventing-kerberos-change-password-that-uses-rc4-secret-keys.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6c57776-ab71-4356-880c-c5ff411d7fe1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/e2d3fbf8-36df-4730-9ac5-e1c53887f039
platformId: 6a9bc689-3634-63a0-4abc-0337380bc575
---

# Preventing Kerberos change password that use RC4 secret keys | Microsoft Learn

This topic for the IT professional explains some limitations in the Kerberos protocol that could lead to a malicious user taking control of a user's account. There is a limitation in the Kerberos Network Authentication Service (V5) standard (RFC 4120), which is well-known within the industry, whereby an attacker can authenticate as a user or change that user's password if the attacker knows the user's secret key.

Possession of a user's password-derived Kerberos secret keys (RC4 and Advanced Encryption Standard [AES] by default) is validated during the Kerberos password change exchange per RFC 4757. The user's plaintext password is never provided to the Key Distribution Center (KDC), and by default, Active Directory domain controllers do not possess a copy of plaintext passwords for accounts. If the domain controller does not support a Kerberos encryption type, that secret key cannot be used to change the password.

In the Windows operating systems designated in the Applies To list at the beginning of this topic, there are three ways to block the ability to change passwords by using Kerberos with RC4 secret keys:

- Configure the user account to include the account option Smart card is required for interactive logon. This limits the user to only signing in with a valid smart card so that RC4 authentication service requests (AS-REQs) are rejected. To set the account options on an account, right-click on the account, the click Properties, and click the Account tab.
- Disable RC4 support for Kerberos on all domain controllers. This requires a minimum of a Windows Server 2008 domain functional level and an environment where all Kerberos clients, application servers, and trust relationships to and from the domain must support AES. Support for AES was introduced in Windows Server 2008 and Windows Vista.

    Note

    There is a known issue with disabling RC4 which can cause the system to restart. See the following hotfixes:

    - [Windows Server 2012 R2](https://support.microsoft.com/kb/3038261)
    - [Windows Server 2012](https://support.microsoft.com/kb/3086213)
    - No hotfix is available for earlier versions of Windows Server
- Deploy domains set to Windows Server 2012 R2 domain functional level or higher, and configure users as members of the Protected Users security group. Because this feature disrupts more than just RC4 usage in the Kerberos protocol, see resources in the following See also section.