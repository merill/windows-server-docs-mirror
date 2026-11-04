---
layout: Conceptual
title: Administer Software Restriction Policies | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/software-restriction-policies/administer-software-restriction-policies
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to administer application control policies using Software Restriction Policies (SRP) beginning with Windows Server 2008 and Windows Vista.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2016-10-12T00:00:00.0000000Z
locale: en-us
document_id: 28a06a11-59fd-1a36-1e94-ecf088f4c3f3
document_version_independent_id: 9b05d267-d03a-adc3-f7cb-4a037191ec7a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/software-restriction-policies/administer-software-restriction-policies.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/software-restriction-policies/administer-software-restriction-policies
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/software-restriction-policies/administer-software-restriction-policies.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 92e14032-2e35-6e6a-79e3-1edc92883e8d
---

# Administer Software Restriction Policies | Microsoft Learn

This topic for the IT professional contains procedures how to administer application control policies using Software Restriction Policies (SRP) beginning with Windows Server 2008 and Windows Vista.

## Introduction

Software Restriction Policies (SRP) is Group Policy-based feature that identifies software programs running on computers in a domain, and controls the ability of those programs to run. You use software restriction policies to create a highly restricted configuration for computers, in which you allow only specifically identified applications to run. These are integrated with Microsoft Active Directory Domain Services and Group Policy but can also be configured on stand-alone computers. For more information about SRP, see the [Software Restriction Policies](software-restriction-policies).

Beginning with Windows Server 2008 R2 and Windows 7 , Windows AppLocker can be used instead of or in concert with SRP for a portion of your application control strategy.

This topic contains:

- To open Software Restriction Policies
- To create new software restriction policies
- To add or delete a designated file type
- To prevent software restriction policies from applying to local administrators
- To change the default security level of software restriction policies
- To apply software restriction policies to DLLs

For information about how to accomplish specific tasks using SRP, see the following:

- [Determine Allow-Deny List and Application Inventory for Software Restriction Policies](determine-allow-deny-list-and-application-inventory-for-software-restriction-policies)
- [Work with Software Restriction Policies Rules](work-with-software-restriction-policies-rules)
- [Use Software Restriction Policies to Help Protect Your Computer Against an Email Virus](use-software-restriction-policies-to-help-protect-your-computer-against-an-email-virus)

## To open Software Restriction Policies

- For your local computer
- For a domain, site, or organizational unit, and you are on a member server or on a workstation that is joined to a domain
- For a domain or organizational unit, and you are on a domain controller or on a workstation that has the Remote Server Administration Tools installed
- For a site, and you are on a domain controller or on a workstation that has the Remote Server Administration Tools installed

### For your local computer

1. Open Local Security Settings.
2. In the console tree, click **Software Restriction Policies**.

    **Where?**

    - Security Settings/Software Restriction Policies

Note

To perform this procedure, you must be a member of the Administrators group on the local computer, or you must have been delegated the appropriate authority.

### For a domain, site, or organizational unit, and you are on a member server or on a workstation that is joined to a domain

1. Open Microsoft Management Console (MMC).
2. On the **File** menu, click **Add/Remove Snap-in**, and then click **Add**.
3. Click **Local Group Policy Object Editor**, and then click **Add**.
4. In **Select Group Policy Object**, click **Browse**.
5. In **Browse for a Group Policy Object**, select a Group Policy Object (GPO) in the appropriate domain, site, or organizational unit-or create a new one, and then click **Finish**.
6. Click **Close**, and then click **OK**.
7. In the console tree, click **Software Restriction Policies**.

    **Where?**

    - *Group Policy Object* [*ComputerName*] Policy/Computer Configuration or

        User Configuration/Windows Settings/Security Settings/Software Restriction Policies

Note

To perform this procedure, you must be a member of the Domain Admins group.

### For a domain or organizational unit, and you are on a domain controller or on a workstation that has the Remote Server Administration Tools installed

1. Open Group Policy Management Console.
2. In the console tree, right-click the Group Policy Object (GPO) that you want to open software restriction policies for.
3. Click **Edit** to open the GPO that you want to edit. You can also click **New** to create a new GPO, and then click **Edit**.
4. In the console tree, click **Software Restriction Policies**.

    **Where?**

    - *Group Policy Object* [*ComputerName*] Policy/Computer Configuration or

        User Configuration/Windows Settings/Security Settings/Software Restriction Policies

Note

To perform this procedure, you must be a member of the Domain Admins group.

### For a site, and you are on a domain controller or on a workstation that has the Remote Server Administration Tools installed

1. Open Group Policy Management Console.
2. In the console tree, right-click the site that you want to set Group Policy for.

    **Where?**

    - Active Directory Sites and Services [*Domain\_Controller\_Name.Domain\_Name*]/Sites/Site
3. Click an entry in **Group Policy Object Links** to select an existing Group Policy Object (GPO), and then click **Edit**. You can also click **New** to create a new GPO, and then click **Edit**.
4. In the console tree, click **Software Restriction Policies**.

    **Where**

    - *Group Policy Object* [*ComputerName*] Policy/Computer Configuration or

        User Configuration/Windows Settings/Security Settings/Software Restriction Policies

Note

- To perform this procedure, you must be a member of the Administrators group on the local computer, or you must have been delegated the appropriate authority. If the computer is joined to a domain, members of the Domain Admins group might be able to perform this procedure.
- To set policy settings that will be applied to computers, regardless of which users log on to them, click **Computer Configuration**.
- To set policy settings that will be applied to users, regardless of which computer they log on to, click **User Configuration**.

## To create new software restriction policies

1. Open Software Restriction Policies.
2. On the **Action** menu, click **New Software Restriction Policies**.

Warning

- Different administrative credentials are required to perform this procedure, depending on your environment:

    - If you create new software restriction policies for your local computer: Membership in the local **Administrators** group, or equivalent, is the minimum required to complete this procedure.
    - If you create new software restriction policies for a computer that is joined to a domain, members of the Domain Admins group can perform this procedure.
- If software restriction policies have already been created for a Group Policy Object (GPO), the **New Software Restriction Policies** command does not appear on the **Action** menu. To delete the software restriction policies that are applied to a GPO, in the console tree, right-click **Software Restriction Policies**, and then click **Delete Software Restriction Policies**. When you delete software restriction policies for a GPO, you also delete all software restriction policies rules for that GPO. After you delete software restriction policies, you can create new software restriction policies for that GPO.

## To add or delete a designated file type

1. Open Software Restriction Policies.
2. In the details pane, double-click **Designated File Types**.
3. Do one of the following:

    - To add a file type, in **File name extension**, type the file name extension, and then click **Add**.
    - To delete a file type, in **Designated file types**, click the file type, and then click **Remove**.

Note

- Different administrative credentials are required to perform this procedure, depending on the environment in which you add or delete a designated file type:

    - If you add or delete a designated file type for your local computer: Membership in the local **Administrators** group, or equivalent, is the minimum required to complete this procedure.
    - If you create new software restriction policies for a computer that is joined to a domain, members of the Domain Admins group can perform this procedure.
- It may be necessary to create a new software restriction policy setting for the Group Policy Object (GPO) if you have not already done so.
- The list of designated file types is shared by all rules for both Computer Configuration and User Configuration for a GPO.

## To prevent software restriction policies from applying to local administrators

1. Open Software Restriction Policies.
2. In the details pane, double-click **Enforcement**.
3. Under **Apply software restriction policies to the following users**, click **All users except local administrators**.

Warning

- Membership in the local **Administrators** group, or equivalent, is the minimum required to complete this procedure.
- It may be necessary to create a new software restriction policy setting for the Group Policy Object (GPO) if you have not already done so.
- If it is common for users to be members of the local Administrators group on their computers in your organization, you may not want to enable this option.
- If you are defining a software restriction policy setting for your local computer, use this procedure to prevent local administrators from having software restriction policies applied to them. If you are defining a software restriction policy setting for your network, filter user policy settings based on membership in security groups through Group Policy.

## To change the default security level of software restriction policies

1. Open Software Restriction Policies.
2. In the details pane, double-click **Security Levels**.
3. Right-click the security level that you want to set as the default, and then click **Set as default**.

Caution

In certain directories, setting the default security level to **Disallowed** can adversely affect your operating system.

Note

- Different administrative credentials are required to perform this procedure, depending on the environment for which you change the default security level of software restriction policies.
- It may be necessary to create a new software restriction policy setting for this Group Policy Object (GPO) if you have not already done so.
- In the details pane, the current default security level is indicated by a black circle with a check mark in it. If you right-click the current default security level, the **Set as default** command does not appear in the menu.
- Software restriction policies rules are created to specify exceptions to the default security level. When the default security level is set to **Unrestricted**, rules can specify software that is not allowed to run. When the default security level is set to **Disallowed**, rules can specify software that is allowed to run.
- At installation, the default security level of software restriction policies on all files on your system is set to **Unrestricted**.

## To apply software restriction policies to DLLs

1. Open Software Restriction Policies.
2. In the details pane, double-click **Enforcement**.
3. Under **Apply software restriction policies to the following**, click **All software files**.

Note

- To perform this procedure, you must be a member of the Administrators group on the local computer, or you must have been delegated the appropriate authority. If the computer is joined to a domain, members of the Domain Admins group might be able to perform this procedure.
- By default, software restriction policies do not check dynamic-link libraries (DLLs). Checking DLLs can decrease system performance, because software restriction policies must be evaluated every time a DLL is loaded. However, you may decide to check DLLs if you are concerned about receiving a virus that targets DLLs. If the default security level is set to **Disallowed**, and you enable DLL checking, you must create software restriction policies rules that allow each DLL to run.