---
layout: Conceptual
title: Performance Tuning Active Directory Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/role/active-directory-server/
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Performance Tuning for Active Directory Servers
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 6f69ab21-c4f1-0a81-3c85-c9be40656026
document_version_independent_id: 0e761426-b9ec-3f2e-10d0-f985860e4c2b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/role/active-directory-server/index.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/role/active-directory-server/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/role/active-directory-server/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 39ee5ff5-71bd-642c-5c44-ab8aa695532c
---

# Performance Tuning Active Directory Servers | Microsoft Learn

Performance tuning Active Directory is focused on two goals:

- Active Directory is optimally configured to service the load in the most efficient manner possible
- Workloads submitted to Active Directory should be as efficient as possible

This requires proper attention to three separate areas:

- Proper capacity planning – ensuring sufficient hardware is in place to support existing load
- Server side tuning – configuring domain controllers to handle the load as efficiently as possible
- Active Directory client/application tuning – ensuring that clients and applications are using Active Directory in an optimal fashion

## Start with capacity planning

Properly deploying a sufficient number of domain controllers, in the right domain, in the right locales, and to accommodate redundancy is critical to ensuring servicing client requests in a timely fashion. This is an in-depth topic and outside of the scope of this guide. Readers are encouraged start to their Active Directory performance tuning by reading and understanding the recommendations and guidance found in [Capacity planning for Active Directory Domain Services](capacity-planning-for-active-directory-domain-services).

Important

Proper configuration and sizing of Active Directory has a significant potential impact on overall system and workload performance. Readers are highly encouraged to start by reading [Capacity planning for Active Directory Domain Services](capacity-planning-for-active-directory-domain-services).

## Updates and evolving recommendations

Massive improvements in both Active Directory and client performance optimizations have occurred over the last several generations of the operating system and these efforts continue. We recommend that the most current versions of the platform be deployed to get the benefits, including:

- Increased reliability
- Better performance
- Better logging and tools to troubleshoot

However, we realize that this takes time and many environments are running in a scenario where 100% adoption of the most current platform is impossible. Some improvements have been added to older versions of the platform and we'll continue to add more.

We encourage you to stay up to date on the latest news, guidance and best practices for managing ADDS by following our team blog, ["Ask the Directory Services Team"](https://techcommunity.microsoft.com/t5/Ask-the-Directory-Services-Team/bg-p/AskDS).

## Additional References

- [Capacity planning for AD DS](capacity-planning-for-active-directory-domain-services)
- [Hardware considerations](hardware-considerations)
- [Memory usage considerations](memory-usage-considerations)
- [LDAP considerations](ldap-considerations)
- [Proper placement of domain controllers and site considerations](site-definition-considerations)
- [Troubleshooting AD DS performance](troubleshoot)