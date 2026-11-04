---
layout: Conceptual
title: Active Directory Domain Services Component Updates | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/component-updates/active-directory-domain-services-component-updates
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: This document discusses the AD DS component updates for Windows Server 2012 R2
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: overview
locale: en-us
document_id: dbe0864a-ad3b-d4f9-0b13-53e8b340928c
document_version_independent_id: ba5392a5-1c17-9b32-67fc-3a3839d5d381
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/component-updates/Active-Directory-Domain-Services-Component-Updates.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/component-updates/active-directory-domain-services-component-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/component-updates/Active-Directory-Domain-Services-Component-Updates.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 3fd928de-37d7-e454-e479-ae021cd01187
---

# Active Directory Domain Services Component Updates | Microsoft Learn

This module introduces the components that received minor updates in the Directory Services and Identity spaces.

| About the Author |
| --- |
| **Author:** |
| **Bio:** |
| **Contributors** |
| **Reviewers** |

Note

This content is written by a Microsoft customer support engineer, and is intended for experienced administrators and systems architects who are looking for deeper technical explanations of features and solutions in Windows Server 2012 R2 than topics on TechNet usually provide. However, it has not undergone the same editing passes, so some of the language may seem less polished than what is typically found on TechNet.

### What You Will Learn

After completing this module, you will be able to:

- Explain the component updates made within the Directory Services and Identity technology areas in Windows Server 2012 R2

    - [SPN and UPN uniqueness](spn-and-upn-uniqueness)
    - [Winlogon Automatic Restart Sign-On (ARSO)](winlogon-automatic-restart-sign-on--arso-)
    - [TPM Key Attestation](tpm-key-attestation)
    - [CA Backup and Restore Windows PowerShell cmdlets](ca-backup-and-restore-windows-powershell-cmdlets)
    - [Command line process auditing](command-line-process-auditing)
    - [Credentials Protection and Management](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn408190%28v=ws.11%29)
    - [Directory Services component updates](directory-services-component-updates)

        - [Domain and Forest Functional Levels](directory-services-component-updates#BKMK_FL)
        - [Deprecation of NTFRS](directory-services-component-updates#BKMK_NTFRS)
        - [LDAP Query Optimizer changes](directory-services-component-updates#BKMK_LDAPQuery)
        - [1644 Event improvements](directory-services-component-updates#BKMK_1644)
        - [Active Directory Replication throughput improvement](directory-services-component-updates#BKMK_ADRepl)