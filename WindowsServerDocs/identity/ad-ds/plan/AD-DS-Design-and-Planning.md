---
layout: Conceptual
title: AD DS Design and Planning | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD DS Design and Planning'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: best-practice
locale: en-us
document_id: 96c7f412-c33d-4f6a-e7aa-3dddee547fd2
document_version_independent_id: 5c41fe4a-02eb-b5da-19cc-9a835b4cf8df
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/AD-DS-Design-and-Planning.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/ad-ds-design-and-planning
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/AD-DS-Design-and-Planning.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 16ad4301-9bb3-7bb0-df67-4c22cc81ca28
---

# AD DS Design and Planning | Microsoft Learn

By deploying Windows Server Active Directory Domain Services (AD DS) in your environment, you can take advantage of the centralized, delegated administrative model and single sign-on (SSO) capability that AD DS provides. After you identify the deployment tasks and current environment for your organization, you can create the AD DS deployment strategy that meets your organization's needs.

## About this guide

This guide provides recommendations to help you develop an AD DS deployment strategy based on the requirements of your organization and the particular design that you want to create. This guide is intended for use by infrastructure specialists or system architects. Before you read this guide, you should have a good understanding of how AD DS works on a functional level. You should also have a good understanding of the organizational requirements that will be reflected in your AD DS deployment strategy.

This guide describes sets of tasks for several possible starting points of a Windows Server AD DS deployment. The guide helps you determine the most appropriate deployment strategy for your environment.

Although the strategies that are presented in this guide are appropriate for almost all server operating system deployments, they have been tested and validated specifically for environments that contain fewer than 100,000 users and fewer than 1,000 sites, with network connections of a minimum of 28.8 kilobits per second (Kbps). If your environment does not meet these criteria, consider using a consulting firm that has experience deploying AD DS in more complex environments.

For more information about testing the AD DS deployment process, see the article [Testing and Verifying the Deployment Process](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc772722%28v=ws.10%29).

## In this guide

[Understanding AD DS Design](understanding-ad-ds-design)

[Identifying Your AD DS Design and Deployment Requirements](identifying-your-ad-ds-design-and-deployment-requirements)

[Mapping Your Requirements to an AD DS Deployment Strategy](mapping-your-requirements-to-an-ad-ds-deployment-strategy)

[Designing the Logical Structure for Windows Server 2008 AD DS](designing-the-logical-structure)

[Designing the Site Topology for Windows Server 2008 AD DS](designing-the-site-topology)

[Enabling Advanced Features for AD DS](enabling-advanced-features-for-ad-ds)

[Evaluating AD DS Deployment Strategy Examples](evaluating-ad-ds-deployment-strategy-examples)

[Appendix A: Reviewing Key AD DS Terms](appendix-a--reviewing-key-ad-ds-terms)