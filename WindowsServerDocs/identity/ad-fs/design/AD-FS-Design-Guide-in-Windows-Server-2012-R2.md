---
layout: Conceptual
title: AD FS Design Guide in Windows Server 2012 R2 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/ad-fs-design-guide-in-windows-server-2012-r2
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: AD FS Design Guide in Windows Server'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: best-practice
locale: en-us
document_id: b0868fef-594f-b3b5-7364-cd2d14d1662f
document_version_independent_id: 040b81a5-0d7e-6017-563d-32e0897b0e02
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/AD-FS-Design-Guide-in-Windows-Server-2012-R2.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/ad-fs-design-guide-in-windows-server-2012-r2
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/AD-FS-Design-Guide-in-Windows-Server-2012-R2.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 950c6947-935a-23cc-46b7-24a5f97e6ed5
---

# AD FS Design Guide in Windows Server 2012 R2 | Microsoft Learn

Active Directory Federation Services (AD FS) provides simplified, secured identity federation and Web single sign-on (SSO) capabilities for end users who want to access applications within an AD FS-secured enterprise, in federation partner organizations, or in the cloud.

In Windows Server® 2012 R2, AD FS includes a federation service role service that acts as an identity provider (authenticates users to provide security tokens to applications that trust AD FS) or as a federation provider (consumes tokens from other identity providers and then provides security tokens to applications that trust AD FS).

The function of providing extranet access to applications and services that are secured by AD FS in Windows Server 2012 R2 is now performed by a new Remote Access role service called Web Application Proxy. This is a departure from the prior versions of Windows Server in which this function was handled by an AD FS federation server proxy. Web Application Proxy is a server role designed to provide access for the AD FS-related extranet scenario and other extranet scenarios. For more information on Web Application Proxy, see [Web Application Proxy Walkthrough Guide](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn280944%28v=ws.11%29).

## About this guide

This guide provides recommendations to help you plan a new deployment of AD FS, based on the requirements of your organization. This guide is intended for use by an infrastructure specialist or system architect. It highlights your main decision points as you plan your AD FS deployment. Before you read this guide, you should have a good understanding of how AD FS works on a functional level. For more information, see [Understanding Key AD FS Concepts](../technical-reference/understanding-key-ad-fs-concepts).

## In this guide

- [Identify Your AD FS Deployment Goals](identify-your-ad-fs-deployment-goals)
- [Plan Your AD FS Deployment Topology](plan-your-ad-fs-deployment-topology)
- [AD FS Requirements](ad-fs-requirements)