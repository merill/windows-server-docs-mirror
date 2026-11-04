---
layout: Conceptual
title: AD FS Design Guide in Windows Server 2012 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/ad-fs-design-guide-in-windows-server-2012
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: AD FS Legacy Design Guide in Windows Server'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: best-practice
locale: en-us
document_id: c3f37b99-cd30-2aef-9c5d-8ba2b4681048
document_version_independent_id: f9fbc414-bb24-54b4-b925-b554556b0623
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/AD-FS-Design-Guide-in-Windows-Server-2012.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/ad-fs-design-guide-in-windows-server-2012
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/AD-FS-Design-Guide-in-Windows-Server-2012.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b90b9f87-b132-ccf0-8d24-e66e2a58126a
---

# AD FS Design Guide in Windows Server 2012 | Microsoft Learn

Note

For information about how to deploy AD FS in Windows Server 2012 R2 , see [Windows Server 2012 R2 AD FS Deployment Guide](../deployment/windows-server-2012-r2-ad-fs-deployment-guide).

You can use Active Directory® Federation Services (AD FS) with the Windows Server® 2012 operating system in a federation services provider role to seamlessly authenticate your users to any Web-based services or applications that reside in a resource partner organization, without the need for administrators to create or maintain external trusts or forest trusts between the networks of both organizations and without the need for the users to log on a second time. The process of authenticating to one network while accessing resources in another network—without the burden of repeated logon actions by users—is known as single sign-on (SSO).

## About this guide

This guide provides recommendations to help you plan a new deployment of AD FS, based on the requirements of your organization (also referred to in this guide as deployment goals) and the particular design that you want to create. This guide is intended for use by an infrastructure specialist or system architect. It highlights your main decision points as you plan your AD FS deployment. Before you read this guide, you should have a good understanding of how AD FS works on a functional level. You should also have a good understanding of the organizational requirements that will be reflected in your AD FS design.

This guide describes a set of deployment goals that are based on three primary AD FS designs, and it helps you decide the most appropriate design for your environment. You can use these deployment goals to form one of the following comprehensive AD FS designs or a custom design that meets the needs of your environment:

- Federated Web SSO to support business-to-business (B2B) scenarios and to support collaboration between business units with independent forests
- Web SSO to support customer access to applications in business-to-consumer (B2C) scenarios

For each design, you will find guidelines for gathering the required data about your environment. You can then use these guidelines to plan and design your AD FS deployment. After you read this guide and finish gathering, documenting, and mapping your organization's requirements, you will have the information necessary to begin deploying AD FS using the guidance in the [Windows Server 2012 AD FS Deployment Guide](../deployment/windows-server-2012-ad-fs-deployment-guide).

## In this guide

- [Identifying Your AD FS Deployment Goals](identifying-your-ad-fs-deployment-goals)
- [Mapping Your Deployment Goals to an AD FS Design](mapping-your-deployment-goals-to-an-ad-fs-design)
- [Determine Your AD FS Deployment Topology](determine-your-ad-fs-deployment-topology)
- [Planning Your Deployment](planning-your-deployment)
- [Planning Federation Server Placement](planning-federation-server-placement)
- [Planning Federation Server Proxy Placement](planning-federation-server-proxy-placement)
- [Planning for AD FS Server Capacity](planning-for-ad-fs-server-capacity)
- [Appendix A: Reviewing AD FS Requirements](appendix-a--reviewing-ad-fs-requirements)