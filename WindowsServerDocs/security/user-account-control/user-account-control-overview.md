---
layout: Conceptual
title: User Account Control Overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/user-account-control/user-account-control-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about User Account Control, how it is a fundamental component of Microsoft's overall security vision, and how it helps mitigate the impact of a malicious program.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2016-10-12T00:00:00.0000000Z
locale: en-us
document_id: 7beb7cbb-db85-a52a-b40d-260fcb32c58a
document_version_independent_id: 976cddbc-5e87-af58-bd3e-7fd32165052b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/user-account-control/user-account-control-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/user-account-control/user-account-control-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/user-account-control/user-account-control-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d7f8710e-fbb0-4d09-b930-11c1b544a877
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d01d0bfd-3c23-4b54-82d6-f9d06ad11cbd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/deb137bf-5bfd-48db-9740-aeec6d9667dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/da7889d8-fed4-4c4c-a52d-b6a3ea4ce02a
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6a888ea1-a67d-80fe-b1fc-a6cd8e7e1bbc
---

# User Account Control Overview | Microsoft Learn

User Account Control (UAC) is a fundamental component of Microsoft's overall security vision. UAC helps mitigate the impact of a malicious program.

## Feature description

UAC allows all users to log on to their computers using a standard user account. Processes launched using a standard user token may perform tasks using access rights granted to a standard user. For instance, Windows Explorer automatically inherits standard user level permissions. Additionally, any programs that are executed using Windows Explorer (for example, by double-clicking an application shortcut) also run with the standard set of user permissions. Many applications, including those that are included with the operating system itself, are designed to work properly in this way.

Other applications, especially those that were not specifically designed with security settings in mind, often require additional permissions to run successfully. These types of programs are referred to as legacy applications. Additionally, actions such as installing new software and making configuration changes to programs such as Windows Firewall, require more permissions than what is available to a standard user account.

When an applications needs to run with more than standard user rights, UAC can restore additional user groups to the token. This enables the user to have explicit control of programs that are making system level changes to their computer or device.

## Practical applications

Admin Approval Mode in UAC helps prevent malicious programs from silently installing without an administrator's knowledge. It also helps protect from inadvertent system-wide changes. Lastly, it can be used to enforce a higher level of compliance where administrators must actively consent or provide credentials for each administrative process.