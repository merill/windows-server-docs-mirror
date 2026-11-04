---
layout: Conceptual
title: Determine Allow-Deny List and Application Inventory for Software Restriction Policies | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/software-restriction-policies/determine-allow-deny-list-and-application-inventory-for-software-restriction-policies
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to create an allow and deny list for applications to be managed by Software Restriction Policies (SRP) beginning with Windows Server 2008 and Windows Vista.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2016-10-12T00:00:00.0000000Z
locale: en-us
document_id: f04afba8-26a0-64ac-1e64-9f4e7db60857
document_version_independent_id: 41404a21-cc7e-eaea-86d6-107d221aa7cb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/software-restriction-policies/determine-allow-deny-list-and-application-inventory-for-software-restriction-policies.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/software-restriction-policies/determine-allow-deny-list-and-application-inventory-for-software-restriction-policies
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/software-restriction-policies/determine-allow-deny-list-and-application-inventory-for-software-restriction-policies.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e686c762-8de5-570f-9725-17aa4991d163
---

# Determine Allow-Deny List and Application Inventory for Software Restriction Policies | Microsoft Learn

This topic for the IT professional gives guidance how to create an allow and deny list for applications to be managed by Software Restriction Policies (SRP) beginning with Windows Server 2008 and Windows Vista.

## Introduction

Software Restriction Policies (SRP) is Group Policy-based feature that identifies software programs running on computers in a domain, and controls the ability of those programs to run. You use software restriction policies to create a highly restricted configuration for computers, in which you allow only specifically identified applications to run. These are integrated with Microsoft Active Directory Domain Services and Group Policy but can also be configured on stand-alone computers. For a starting point for SRP, see the [Software Restriction Policies](software-restriction-policies).

Beginning with Windows Server 2008 R2 and Windows 7 , Windows AppLocker can be used instead of or in concert with SRP for a portion of your application control strategy.

For information about how to accomplish specific tasks using SRP, see the following:

- [Work with Software Restriction Policies Rules](work-with-software-restriction-policies-rules)
- [Use Software Restriction Policies to Help Protect Your Computer Against an Email Virus](use-software-restriction-policies-to-help-protect-your-computer-against-an-email-virus)

### What default rule to choose: Allow or Deny

Software restriction policies can be deployed in one of two modes that are the basis of your default rule: Allow List or Deny List. You can create a policy that identifies every application that is allowed to run in your environment; the default rule within your policy is Restricted and will block all applications that you do not explicitly allow to run. Or you can create a policy that identifies every application that cannot run; the default rule is Unrestricted and restricts only the applications that you have explicitly listed.

Important

The Deny List mode might be a high-maintenance strategy for your organization regarding application control. Creating and maintaining an evolving list that prohibits all malware and other problematic applications would be time consuming and susceptible to mistakes.

### Create an inventory of your applications for the Allow list

To effectively use the Allow default rule, you need to determine exactly which applications are required in your organization. There are tools designed to produce an application inventory, such as the Inventory Collector in the Microsoft Application Compatibility Toolkit. But SRP has an advanced logging feature to help you understand exactly what applications are running in your environment.

##### To discover which applications to allow

1. In a test environment, deploy Software Restriction Policy with the default rule set to Unrestricted and remove any additional rules. If you enable SRP without forcing it to restrict any applications, SPR will be able to monitor what applications are being run.
2. Create the following registry value in order to enable the advanced logging feature and set the path to where the log file should be written.

    **"HKEY\_LOCAL\_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Safer\CodeIdentifiers"**

    String Value: *LogFileName path to LogFileName*

    Because SRP is evaluating all applications when they run, an entry is written to the log file *NameLogFile* each time that application is run.
3. Evaluate the log file

    Each log entry states:

    - the caller of the software restriction policy and the process ID (PID) of the calling process
    - the target being evaluated
    - the SRP rule that was encountered when that application ran
    - an identifier for the SRP rule.

    An example of the output written to a log file:

**explorer.exe (PID = 4728) identifiedC:\Windows\system32\onenote.exe as Unrestricted usingpath rule, Guid ={320bd852-aa7c-4674-82c5-9a80321670a3}** All applications and associated code that SRP checks and set to block will be noted in the log file, which you then can use to determine which executables should be considered for your Allowed list.