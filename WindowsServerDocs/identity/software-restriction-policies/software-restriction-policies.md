---
layout: Conceptual
title: Software Restriction Policies | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/software-restriction-policies/software-restriction-policies
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about Software Restriction Policies (SRP) in Windows Server 2012 and Windows 8 and find links to technical information about SRP beginning with Windows Server 2003.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2016-10-12T00:00:00.0000000Z
locale: en-us
document_id: 5ddf4d84-bdef-765c-4533-6f5764a0cc95
document_version_independent_id: 6750c735-4c7c-4190-8528-a2427ee9e4d8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/software-restriction-policies/software-restriction-policies.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/software-restriction-policies/software-restriction-policies
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/software-restriction-policies/software-restriction-policies.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1e46d60c-7498-85fd-6191-22834c5629e2
---

# Software Restriction Policies | Microsoft Learn

This topic for the IT professional describes Software Restriction Policies (SRP) in Windows Server 2012 and 2016 and Windows 8, and provides links to technical information about SRP beginning with Windows Server 2003.

Important

Software Restriction Policies were deprecated beginning with Windows 10 build 1803 and also applies to Windows Server 2019 and above. You should use Windows Defender Application Control (WDAC) or AppLocker to control what software runs.

For procedures and troubleshooting tips, see [Administer Software Restriction Policies](administer-software-restriction-policies) and [Troubleshoot Software Restriction Policies](troubleshoot-software-restriction-policies).

## Software Restriction Policies description

Software Restriction Policies (SRP) is Group Policy-based feature that identifies software programs running on computers in a domain, and controls the ability of those programs to run. Software restriction policies are part of the Microsoft security and management strategy to assist enterprises in increasing the reliability, integrity, and manageability of their computers.

You can also use software restriction policies to create a highly restricted configuration for computers, in which you allow only specifically identified applications to run. Software restriction policies are integrated with Microsoft Active Directory and Group Policy. You can also create software restriction policies on stand-alone computers. Software restriction policies are trust policies, which are regulations set by an administrator to restrict scripts and other code that is not fully trusted from running.

You can define these policies through the Software Restriction Policies extension of the Local Group Policy Editor or the Local Security Policies snap-in to the Microsoft Management Console (MMC).

For in-depth information about SRP, see the [Software Restriction Policies Technical Overview](software-restriction-policies-technical-overview).

## Practical applications

Administrators can use software restriction policies for the following tasks:

- Define what is trusted code
- Design a flexible Group Policy for regulating scripts, executable files, and ActiveX controls

Software restriction policies are enforced by the operating system and by applications (such as scripting applications) that comply with software restriction policies.

Specifically, administrators can use software restriction policies for the following purposes:

- Specify which software (executable files) can run on clients
- Prevent users from running specific programs on shared computers
- Specify who can add trusted publishers to clients
- Set the scope of the software restriction policies (specify whether policies affect all users or a subset of users on clients)
- Prevent executable files from running on the local computer, organizational unit (OU), site, or domain. This would be appropriate in cases when you are not using software restriction policies to address potential issues with malicious users.

## New and changed functionality

There are no changes in functionality for Software Restriction Policies.

## Removed or deprecated functionality

There is no removed or deprecated functionality for Software Restriction Policies.

## Software requirements

The Software Restriction Policies extension to the Local Group Policy Editor can be accessed through the MMC.

The following features are required to create and maintain software restriction policies on the local computer:

- Local Group Policy Editor
- Windows Installer
- Authenticode and WinVerifyTrust

If your design calls for domain deployment of these policies, in addition to the above list, the following features are required:

- Active Directory Domain Services
- Group Policy

## Server Manager information

Software Restriction Policies is an extension of the Local Group Policy Editor and is not installed through Server Manager, Add Roles and Features.

## See also

The following table provides links to relevant resources in understanding and using SRP.

| Content type | References |
| --- | --- |
| **Product evaluation** | [Application Lockdown with Software Restriction Policies](/en-us/previous-versions/technet-magazine/cc510322%28v=msdn.10%29?pr=blog) |
| **Planning** | [Software Restriction Policies Technical Overview](software-restriction-policies-technical-overview) ( Windows Server 2012 )<br>[Software Restriction Policies Technical Reference](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc728085%28v=ws.10%29) (Windows Server 2003) |
| **Deployment** | No resources available. |
| **Operations** | [Administer Software Restriction Policies](administer-software-restriction-policies) ( Windows Server 2012 )<br>[Software Restriction Policies Product Help](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc779607%28v=ws.10%29) (Windows Server 2003) |
| **Troubleshooting** | [Troubleshoot Software Restriction Policies](troubleshoot-software-restriction-policies) ( Windows Server 2012 )<br>[Software Restriction Policies Troubleshooting](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc737011%28v=ws.10%29) (Windows Server 2003) |
| **Security** | [Threats and Countermeasures for Software Restriction Polices](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd349795%28v=ws.10%29) (Windows Server 2008)<br>[Threats and Countermeasures for Software Restriction Polices](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh125926%28v=ws.10%29) (Windows Server 2008 R2) |
| **Tools and settings** | [Software Restriction Policies Tools and Settings](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc782454%28v=ws.10%29) (Windows Server 2003) |
| **Community resources** | [Application Lockdown with Software Restriction Policies](/en-us/previous-versions/technet-magazine/cc510322%28v=msdn.10%29?pr=blog) |