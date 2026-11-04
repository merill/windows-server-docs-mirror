---
layout: Conceptual
title: Identifying Forest Design Requirements | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/identifying-forest-design-requirements
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Identifying Forest Design Requirements'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 6daf066c-06ee-0509-a85f-dfadfe97524e
document_version_independent_id: dc51db76-5c49-7985-c18a-7d2bccaa7d32
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Identifying-Forest-Design-Requirements.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/identifying-forest-design-requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Identifying-Forest-Design-Requirements.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 9741634b-9253-3836-6d3b-09e888d12fe1
---

# Identifying Forest Design Requirements | Microsoft Learn

To create a forest design for your organization, you must identify the business requirements that your directory structure needs to accommodate. This involves determining how much autonomy the groups in your organization need to manage their network resources and whether or not each group needs to isolate their resources on the network from other groups.

Active Directory Domain Services (AD DS) enables you to design a directory infrastructure that accommodates multiple groups within an organization that have unique management requirements and to achieve structural and operational independence between groups as needed.

Groups in your organization might have some of the following types of requirements:

- **Organizational structure requirements**. Parts of an organization might participate in a shared infrastructure to save costs but require the ability to operate independently from the rest of the organization. For example, a research group within a large organization might need to maintain control over all of their own research data.
- **Operational requirements**. One part of an organization might place unique constraints on the directory service configuration, availability, or security, or use applications that place unique constraints on the directory. For example, individual business units within an organization might deploy directory-enabled applications that modify the directory schema that are not deployed by other business units. Because the directory schema is shared between all the domains in the forest, creating multiple forests is one solution for such a scenario. Other examples are found in the following organizations and scenarios:

    - Military organizations
    - Hosting scenarios
    - Organizations maintaining a directory that is available both internally and externally (such as those publicly accessible to users on the Internet)
- **Legal requirements**. Some organizations have legal requirements to operate in a specific way, for example, restricting access to certain information as specified in a business contract. Some organizations have security requirements to operate on isolated internal networks. Failure to meet these requirements can result in loss of the contract and possibly legal action.

Part of identifying your forest design requirements involves identifying the degree to which groups in your organization can trust the potential forest owners and their service administrators and identifying the autonomy and isolation requirements for each group in your organization.

The design team must document the isolation and autonomy requirements for service and data administration for each group in the organization that intends to use AD DS. The team must also note any areas of limited connectivity that might affect the deployment of AD DS.

The design team must document the isolation and autonomy requirements for service and data administration for each group in the organization that intends to use AD DS. The team must also note any areas of limited connectivity that might affect the deployment of AD DS. For a worksheet to assist you in documenting the regions you identified, download Job\_Aids\_Designing\_and\_Deploying\_Directory\_and\_Security\_Services.zip from [Job Aids for Windows Server 2003 Deployment Kit](https://microsoft.com/download/details.aspx?id=9608) and open "Forest Design Requirements" (DSSLOGI\_2.doc).