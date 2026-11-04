---
layout: Conceptual
title: Determine Your Federated Application Strategy in the Resource Partner | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/determine-your-federated-application-strategy-in-the-resource-partner
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Determine Your Federated Application Strategy in the Resource Partner'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 019a5dd2-0f8d-c444-0f0a-58cf3a74a54e
document_version_independent_id: bcf32891-8893-ff5c-4e0a-9164a6e1a89d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Determine-Your-Federated-Application-Strategy-in-the-Resource-Partner.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/determine-your-federated-application-strategy-in-the-resource-partner
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Determine-Your-Federated-Application-Strategy-in-the-Resource-Partner.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 6b77f062-8bf8-c2d3-15eb-d146d2f98908
---

# Determine Your Federated Application Strategy in the Resource Partner | Microsoft Learn

An important part of designing a new Active Directory Federation Services (AD FS) infrastructure in the resource partner organization is determining your full set of applications and services that will be used to participate in the federation and which account partners will be the recipients of those resources. Before you design a federated application and services strategy, consider the following questions:

- Will you be enabling and deploying an ASP.NET application or a Windows Communication Foundation (WCF) service for federation?
- Will users on your corporate network require access to the federated application or service through Windows Integrated Authentication?
- Will the federated application or service be used by users in your perimeter network? If so, will Windows Integrated Authentication be required?
- Are all of the Web servers that host federated applications running a Windows Server operating system and Internet Information Services (IIS)?
- Who will the federated application or service provide resources for?

Answering these questions will help you plan a solid AD FS design. It will also assist you in creating a federated application and services strategy that is cost effective and resource efficient. For more information about designing the most appropriate federated application and services strategy for your organization, see the following topics in this guide:

- [Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services](provide-your-active-directory-users-access-to-your-claims-aware-applications-and-services)
- [Provide Your Active Directory Users Access to the Applications and Services of Other Organizations](provide-your-active-directory-users-access-to-the-applications-and-services-of-other-organizations)
- [Provide Users in Another Organization Access to Your Claims-Aware Applications and Services](provide-users-in-another-organization-access-to-your-claims-aware-applications-and-services)

For more information about how to create a claims-aware ASP.NET application or WCF service, see [Windows Identity Foundation SDK](/en-us/previous-versions/troubleshoot/dotnet/framework/windows-identity-foundation).