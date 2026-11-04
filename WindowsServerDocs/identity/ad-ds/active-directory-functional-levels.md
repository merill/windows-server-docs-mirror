---
layout: Conceptual
title: Active Directory Domain Services Functional Levels | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/active-directory-functional-levels
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Discover the capabilities of Active Directory Domain Services functional levels and learn how they impact domain controllers and Windows Server compatibility.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-10-30T00:00:00.0000000Z
locale: en-us
document_id: 418dc0a0-0312-9d6f-b2dc-2eb4841285ba
document_version_independent_id: 600b0469-3c96-5737-c39b-2ce9021b0f5a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/active-directory-functional-levels.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/active-directory-functional-levels
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/active-directory-functional-levels.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 95c6cc16-5b4d-f550-b111-c0332a9a566c
---

# Active Directory Domain Services Functional Levels | Microsoft Learn

Functional levels determine the available Active Directory Domain Services (AD DS) domain or forest capabilities. They also determine which Windows Server operating systems you can run on domain controllers in the domain or forest. However, functional levels don't affect which operating systems you can run on workstations and member servers joined to the domain or forest. This article describes which functioning levels are compatible with which versions of Windows Server.

When you deploy AD DS, set the domain and forest functional levels to the highest value that your environment can support in order to use as many AD DS features as possible. When you deploy a new forest, you need to set both the forest and domain functional levels. You can set a domain functional level higher than the forest functional level. You can't set a domain functional level lower than the forest functional level.

## Windows Server functional level interoperability

The following interoperability matrix summarizes which Windows Server versions you can run as domain controllers for each currently supported AD DS forest and domain functional level.

| Windows Server version (DC) | Windows Server 2025 functional level | Windows Server 2016 functional level | Windows Server 2012 R2 functional level |
| --- | --- | --- | --- |
| Windows Server 2025 | ✅ Supported | ✅ Supported | ❌ Not supported |
| Windows Server 2022 | ❌ Not supported | ✅ Supported | ✅ Supported |
| Windows Server 2019 | ❌ Not supported | ✅ Supported | ✅ Supported |
| Windows Server 2016 | ❌ Not supported | ✅ Supported | ✅ Supported |
| Windows Server 2012 R2 | ❌ Not supported | ❌ Not supported | ✅ Supported |

✅ Supported means you can run a domain controller with that Windows Server release at the specified forest and domain functional level; ❌ Not supported means you cannot.

Note

Windows Server 2019 and Windows Server 2022 use Windows Server 2016 as the most recent functional level. For earlier functional levels (for example Windows Server 2008 R2), see [Understanding Active Directory Domain Services (AD DS) Functional Levels](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754918%28v=ws.10%29).

### Windows Server 2025 functional levels

You can use the following operating systems as domain controllers (DCs) with the Windows Server 2025 forest and domain functional level.

- Windows Server 2025

#### Windows Server 2025 forest and domain functional level features

The Windows Server 2025 domain functional level includes all features available in earlier domain functional levels, but also has the following new features:

- Database 32k pages optional feature. To learn more about using the 32k database page size, see [Database 32k pages for Active Directory](/en-us/windows-server/identity/ad-ds/32k-pages-optional-feature).

To learn more about new features, see [What's new in Windows Server 2025](../../get-started/whats-new-windows-server-2025).

Note

Windows Server 2019 and Windows Server 2022 use Windows Server 2016 as the most recent functional levels.

### Windows Server 2016 functional levels

You can use the following operating systems as domain controllers (DCs) with the Windows Server 2016 forest and domain functional level.

- Windows Server 2025
- Windows Server 2022
- Windows Server 2019
- Windows Server 2016

Note

Domains must use DFSR as the engine to replicate SYSVOL. To learn more about migrating to DFSR, see [Streamlined Migration of FRS to DFSR SYSVOL](https://techcommunity.microsoft.com/blog/filecab/streamlined-migration-of-frs-to-dfsr-sysvol/425405). Windows Server 2016 is the last Windows Server release that supports the File Replication Service (FRS). See [Windows Server version 1709 no longer supports FRS](/en-us/troubleshoot/windows-server/networking/windows-server-version-1709-no-longer-supports-frs) for information on how to work around this issue.

#### Windows Server 2016 forest and domain functional level features

All default Active Directory features in earlier forest functional levels are available, plus the following features:

- [Privileged access management (PAM) using Microsoft Identity Manager (MIM)](../whats-new-active-directory-domain-services#privileged-access-management)

All default Active Directory features in earlier domain functional levels are available, plus the following features:

- DCs can support automatic rolling of the New Technology LAN Manager (NTLM) and other password-based secrets on a user account configured to require public key infrastructure (PKI) authentication. This configuration is also known as *Smart card required for interactive logon*.
- DCs can support allowing network NTLM when a user is restricted to specific domain-joined devices.
- Kerberos clients successfully authenticating with the PKInit Freshness Extension get the fresh public key identity security identifier (SID).

    For more information, see [What's New in Kerberos Authentication](../../get-started/whats-new-in-windows-server-2016#kerberos-authentication).

### Windows Server 2012 R2 functional levels

You can use the following operating systems as domain controllers (DCs) with the Windows Server 2012 R2 forest and domain functional level.

- Windows Server 2022
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2

#### Windows Server 2012 R2 forest and domain functional level features

All default Active Directory features, all features from the Windows Server 2012 domain functional level, plus the following features:

- DC-side protections for Protected Users. When Protected Users authenticate to a Windows Server 2012 R2 domain, they're no longer able to:

    - Authenticate with NTLM authentication.
    - Use DES or RC4 cipher suites in Kerberos preauthentication.
    - Be delegated with unconstrained or constrained delegation.
    - Renew user tickets (TGTs) beyond the initial four hour lifetime.
- Authentication policies

    - New forest-based authentication policies can be applied to accounts. The policies can control which hosts an account can sign on from, and apply access control conditions for authentication to services running as an account.
- Authentication policy silos

    - A new forest-based Active Directory object to be used to classify accounts for authentication policies or for authentication isolation. The new object can create a relationship between user, managed service, and computer accounts.

### Functional and domain levels in previous versions of Windows Server

If you want to identify functional levels for a previous version of Windows Server, such as Windows Server 2008 R2, see [Understanding Active Directory Domain Services (AD DS) Functional Levels](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754918%28v=ws.10%29).