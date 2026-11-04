---
layout: Conceptual
title: Active Directory Forest Recovery - Virtualization | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-virtualization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Virtualized domain controller (DC) cloning simplifies and expedites the process for installing additional virtualized DCs in a domain, especially in centralized locations such as datacenters where several DCs run on hypervisors. After you restore one virtual DC in each domain from backup, additional DCs in each domain can be rapidly brought online by using the virtualized DC cloning process. You can prepare the first virtualized DC that you recover, shut it down, and then copy that virtual hard disk as many times as is necessary to create cloned virtualized DCs and build out the domain.
ms.author: roharwoo
author: robinharwood
ms.date: 2023-06-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: e34f26a6-7bff-904f-7c45-df9a13095a18
document_version_independent_id: e34f26a6-7bff-904f-7c45-df9a13095a18
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-virtualization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-virtualization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-virtualization.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f89e5476-158a-7933-a8f6-c0fc4d5742a1
---

# Active Directory Forest Recovery - Virtualization | Microsoft Learn

## Use virtualized domain controller cloning to expedite forest recovery

Virtualized domain controller (DC) cloning simplifies and expedites the process for installing additional virtualized DCs in a domain, especially in centralized locations such as datacenters where several DCs run on hypervisors.

After you restore one virtual DC in each domain from backup, additional DCs in each domain can be rapidly brought online by using the virtualized DC cloning process.

You can prepare the first virtualized DC that you recover, shut it down, and then copy that virtual hard disk as many times as is necessary to create cloned virtualized DCs and build out the domain.

## Requirements for virtualized DC cloning

The requirements for virtualized DC cloning are:

- The hypervisor must support `VM-GenerationID`. For example, Hyper-V supports that mechanism from Windows Server 2012, Windows 8, and newer operating systems. Check with your hypervisor vendor to find out if `VM-GenerationID` is supported.
- The virtualized DC that is used as a source for cloning must be a member of the Cloneable Domain Controllers group.

The PDC Emulator must be available during cloning operations.For step-by-step instructions for virtualized DC cloning, see [Safely virtualizing Active Directory Domain Services (AD DS)](/en-us/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100). For details about how virtualized DC cloning works, see [Virtualized Domain Controller Technical Reference](/en-us/windows-server/identity/ad-ds/deploy/virtual-dc/virtualized-domain-controller-technical-reference--level-300-).