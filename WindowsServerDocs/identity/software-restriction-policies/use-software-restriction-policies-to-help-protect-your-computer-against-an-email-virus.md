---
layout: Conceptual
title: Use Software Restriction Policies to Help Protect Your Computer Against an Email Virus | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/software-restriction-policies/use-software-restriction-policies-to-help-protect-your-computer-against-an-email-virus
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to set application control polices using Software Restriction Policies (SRP) to help protect your computer against e-mail virus beginning with Windows Server 2008 and Windows Vista.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2016-10-12T00:00:00.0000000Z
locale: en-us
document_id: ea3ce88d-2bec-6e8d-f282-9a9eb54bc861
document_version_independent_id: 2878e32d-f337-16e8-a183-a1358aa57533
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/software-restriction-policies/use-software-restriction-policies-to-help-protect-your-computer-against-an-email-virus.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/software-restriction-policies/use-software-restriction-policies-to-help-protect-your-computer-against-an-email-virus
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/software-restriction-policies/use-software-restriction-policies-to-help-protect-your-computer-against-an-email-virus.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8ad46699-9867-21d1-81a2-852c291f54cd
---

# Use Software Restriction Policies to Help Protect Your Computer Against an Email Virus | Microsoft Learn

This topic provides information how to set application control polices using Software Restriction Policies (SRP) to help protect your computer against e-mail virus beginning with Windows Server 2008 and Windows Vista.

## Introduction

Software Restriction Policies (SRP) is Group Policy-based feature that identifies software programs running on computers in a domain, and controls the ability of those programs to run. You use software restriction policies to create a highly restricted configuration for computers, in which you allow only specifically identified applications to run. These are integrated with Microsoft Active Directory Domain Services and Group Policy but can also be configured on stand-alone computers. For a starting point for SRP, see the [Software Restriction Policies](software-restriction-policies).

Beginning with Windows Server 2008 R2 and Windows 7 , Windows AppLocker can be used instead of or in concert with SRP for a portion of your application control strategy.

#### Configure SRP to help protect against an e-mail virus

1. Review the best practices for software restriction policies to understand how SRP works.

    - [Best practices](software-restriction-policies-technical-overview#BKMK_Best_Practices)
    - [How Software Restriction Policies Work](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc786941%28v=ws.10%29)
2. Open Software Restriction Policies.

    - [For your local computer](administer-software-restriction-policies#BKMK_1)
    - [For a domain, site, or organizational unit, and you are on a member server or on a workstation that is joined to a domain](administer-software-restriction-policies#BKMK_2)
3. If you have not previously defined software restriction policies, create new software restriction policies.

    - [To create new software restriction policies](administer-software-restriction-policies#BKMK_Create_SRP)
4. Create a path rule for the folder that your e-mail program uses to run e-mail attachments, and then set the security level to **Disallowed**.

    - [Working with path rules](work-with-software-restriction-policies-rules#BKMK_Path_Rules)
5. Specify the file types to which the rule applies.

    - [To add or delete a designated file type](administer-software-restriction-policies#BKMK_Add_Del)
6. Modify policy settings so that they apply to the users and groups that you want:

    - Specify users or groups to which you do not want the Group Policy Object's (GPO) policy settings to apply.
    - Exclude local administrators from the software restriction policies of a specific policy setting in Group Policy and still have the rest of Group Policy apply to the administrators.

        - [To prevent software restriction policies from applying to local administrators](administer-software-restriction-policies#BKMK_Prevent_Admin)
7. Test the policy.