---
layout: Conceptual
title: Plan for File Access Auditing | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/solution-guides/plan-for-file-access-auditing
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Plan for File Access Auditing'
author: robinharwood
ms.author: roharwoo
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: a62cbeac-b44d-8f67-bccf-cd945df44661
document_version_independent_id: f65ea624-6204-d6f2-f538-105a455cc795
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/solution-guides/Plan-for-File-Access-Auditing.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/solution-guides/plan-for-file-access-auditing
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/solution-guides/Plan-for-File-Access-Auditing.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 3b6dd88b-17c3-e32c-2018-939a47684d11
---

# Plan for File Access Auditing | Microsoft Learn

The information in this topic explains the security auditing enhancements that are introduced in Windows Server 2012 and new audit settings that you should consider as you deploy Dynamic Access Control in your enterprise. The actual audit policy settings that you deploy will depend on your goals, which can include regulatory compliance, monitoring, forensic analysis, and troubleshooting.

Note

Detailed information about how to plan and deploy an overall security auditing strategy for your enterprise is explained in [Planning and Deploying Advanced Security Audit Policies](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee513968%28v=ws.10%29). For more information about configuring and deploying a security audit policy, see the [Advanced Security Audit Policy Step-by-Step Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd408940%28v=ws.10%29).

The following security auditing capabilities in Windows Server 2012 can be used with Dynamic Access Control to extend your overall security auditing strategy.

- **Expression-based audit policies**. Dynamic Access Control enables you to create targeted audit policies by using expressions based on user, computer, and resource claims. For example, you could create an audit policy to track all Read and Write operations on files classified as high-business impact by employees who do not have a high-security clearance. Expression-based audit policies can be authored directly for a file or folder or centrally through Group Policy. For more information, see [Group Policy using Global Object Access Auditing](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd772630%28v=ws.10%29).
- **Additional information from object access auditing**. File access auditing is not new to Windows Server 2012 . With the right audit policy in place, the Windows and Windows Server operating systems generate an audit event each time a user accesses a file. Existing File Access events (4656, 4663) contain information about the attributes of the file that was accessed. This information can be used by event log filtering tools to help you identify the most relevant audit events. For more information, see [Audit Handle Manipulation](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd772626%28v=ws.10%29) and [Audit Security Accounts Manager](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd772719%28v=ws.10%29).
- **More information from user logon events**. With the right audit policy in place, Windows operating systems generate an audit event every time a user signs in to a computer locally or remotely. In Windows Server 2012 or Windows 8, you can also monitor user and device claims associated with a user's security token. Examples can include Department, Company, Project, and Security clearances.Event 4626 contains information about these user claims and device claims, which can be leveraged by audit log management tools to correlate user logon events with object access events to enable event filtering based on file attributes and user attributes. For more information about user logon auditing, see [Audit Logon](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd941635%28v=ws.10%29).
- **Change tracking for new types of securable objects**. Tracking changes to securable objects can be important in the following scenarios:

    - **Change tracking for central access policies and central access rules**. Central access policies and central access rules define the central policy that can be used to control access to critical resources. Any change to these can directly impact the file access permissions that are granted to users on multiple computers. Therefore, tracking changes to central access policies and central access rules can be important for your organization. Because central access policies and central access rules are stored in Active Directory Domain Services (AD DS), you can audit attempts to modify them, like auditing changes to any other securable object in AD DS. For more information, see [Audit Directory Service Access](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd941618%28v=ws.10%29).
    - **Change tracking for definitions in the claim dictionary**. Claim definitions include the claim name, description, and possible values. Any change to the claim definition can impact the access permissions on critical resources. Therefore, tracking changes to claim definitions can be important to your organization. Like central access policies and central access rules, claim definitions are stored in AD DS; therefore, they can be audited like any another securable object in AD DS. For more information, see [Audit Directory Service Access](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd941618%28v=ws.10%29).
    - **Change tracking for file attributes**. File attributes determine which central access rule applies to the file. A change to the file attributes can potentially impact the access restrictions on the file. Therefore, it can be important to track changes to file attributes. You can track changes to file attributes on any computer by configuring the authorization policy change auditing policy. For more information, see [Authorization Policy Change auditing](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd941587%28v=ws.10%29) and [Object Access auditing for File Systems](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd772661%28v=ws.10%29). In Windows Server 2012 , Event 4911 differentiates file attribute policy changes from other authorization policy change events.
    - **Chang tracking for the central access policy associated with a file.** Event 4913 displays the security identifiers (SIDs) of the old and new central access policies. Each central access policy also has a user friendly name that can be looked up using this security identifier. For more information, see [Authorization Policy Change auditing](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd941587%28v=ws.10%29).
    - **Change tracking for user and computer attributes**. Like files, user and computer objects can have attributes, and changes to these attributes can impact the user's ability to access files. Therefore, it can be valuable to track changes to user or computer attributes. User and computer objects are stored in AD DS; therefore, changes to their attributes can be audited. For more information, see [DS Access](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd941584%28v=ws.10%29).
- **Policy change staging**. Changes to central access policies can impact the access control decisions on all computers where the policies are enforced. A loose policy could grant more access than desired, and an overly restrictive policy could generate an excessive number of Help Desk calls. As a result, it can be extremely valuable to verify changes to a central access policy before enforcing the change. For that purpose, Windows Server 2012 introduces the concept of "staging." Staging enables users to verify their proposed policy changes before enforcing them. To use policy staging, proposed policies are deployed with the enforced policies, but staged policies do not actually grant or deny permissions. Instead, Windows Server 2012 logs an audit event (4818) any time the result of the access check that uses the staged policy is different from the result of an access check that uses the enforced policy.