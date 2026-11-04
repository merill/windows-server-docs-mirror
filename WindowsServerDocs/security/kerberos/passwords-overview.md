---
layout: Conceptual
title: Passwords Overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/kerberos/passwords-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about passwords as they are used in the Windows operating systems, and find links to documentation and discussions about the use of passwords in a credential management strategy.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2016-10-12T00:00:00.0000000Z
locale: en-us
document_id: 50803f68-14fb-cebc-a36d-2018cd4ad9fa
document_version_independent_id: 1dbc1e00-ffeb-619a-6c28-01ca2953fa50
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/kerberos/passwords-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/kerberos/passwords-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/kerberos/passwords-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 92c2a0e9-79af-3be7-40d3-57c2744271dd
---

# Passwords Overview | Microsoft Learn

This topic for the IT professional describes passwords as used in the Windows operating systems, and links to documentation and discussions about the use of passwords in a credential management strategy.

## Feature description

Operating systems and applications today are architected around passwords and even if you use smart cards or biometric systems, all accounts still have passwords and they can still be used in some circumstances. Some accounts, notably accounts used to run services, cannot even use smart cards and biometric tokens and therefore must use a password to authenticate. Windows protects passwords using cryptographic hashes.

For more information about Windows passwords, see [Passwords Technical Overview](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh994558%28v=ws.10%29).

## Practical applications

In Windows and many other operating systems, the most common method for authenticating a user's identity is to use a secret passphrase or password. Securing your network environment requires that strong passwords be used by all users. This helps avoid the threat of a malicious user guessing a weak password, whether through manual methods or by using tools, to acquire the credentials of a compromised user account. This is especially true for administrative accounts. When you change a complex password regularly, it reduces the likelihood of a password attack compromising that account.

## New and changed functionality

In Windows Server 2012 and Windows 8, picture passwords are new. Picture passwords are a combination of a user selected image coupled with a series of gestures. Picture password functionality is disabled on domain-joined computers. Links to more information about picture passwords are listed in See Also below.

There has been no change to password functionality in Windows Server 2012 and Windows 8. No new Group Policy settings have been added. However, improvements and enhancements have been made in credential (and password) management, such as with picture passwords, Credential Locker and signing in to Windows 8 with a Microsoft account, formerly known as a Windows Live ID.

## Deprecated functionality

No password functionality has been deprecated in Windows Server 2012 and Windows 8.

## Software requirements

In enterprise environments, passwords are typically managed with Active Directory Domain Services. Passwords can also be managed on the local computer using the settings in local Security Settings, Account Policies, Password Policy.

## See also

This table lists additional resources for password features, technology and credential management.

| Content type | References |
| --- | --- |
| **Scenario documentation** | [Protecting your digital identity](https://blogs.msdn.com/b/b8/archive/2011/12/14/protecting-your-digital-identity.aspx) |
| **Operations** | [Active Directory Users and Computers](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754217%28v=ws.11%29) |
| **Troubleshooting** | [Find out when your Password Expires - Active Directory PowerShell Blog](https://blogs.msdn.com/b/adpowershell/archive/2010/08/09/9970198.aspx) |
| **Security** | Windows Server 2008 R2 and Windows 7 [Threats and Countermeasures Guide: Account Policies](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh125920%28v=ws.10%29)<br>Guidance to [change and create strong passwords](https://support.microsoft.com/en-us/windows/create-and-use-strong-passwords-c5cebb49-8c53-4f5e-2bc4-fe357ca048eb) |
| **Tools and settings** | [Group Policy Settings Reference for Windows and Windows Server on the Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=104005) |
| **Community resources** | [Protecting your digital identity](https://blogs.msdn.com/b/b8/archive/2011/12/14/protecting-your-digital-identity.aspx)<br>[Signing in to Windows 8 with a Windows Live ID](https://blogs.msdn.com/b/b8/archive/2011/09/26/signing-in-to-windows-8-with-a-windows-live-id.aspx)<br><br>[Signing in with a picture password](/en-us/archive/blogs/b8/signing-in-with-a-picture-password)<br><br>[Optimizing picture password security](/en-us/archive/blogs/b8/optimizing-picture-password-security) |