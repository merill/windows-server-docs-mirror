---
layout: Conceptual
title: AD FS Decommission Reference | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/ad-fs-decommission
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: AD FS Decommission'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: upgrade-and-migration-article
locale: en-us
document_id: da474797-f3e4-82fc-3853-81deb16ba1a2
document_version_independent_id: da474797-f3e4-82fc-3853-81deb16ba1a2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/ad-fs-decommission.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/ad-fs-decommission
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/ad-fs-decommission.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: f4b0d793-2b52-e350-6e07-210487a39048
---

# AD FS Decommission Reference | Microsoft Learn

A detailed guide on information you need to know to decommission your AD FS servers.

| Resource | Description |
| --- | --- |
| [AD FS decommission guide](decommission/adfs-decommission-guide) | Detailed guide to decommissioning your AD FS servers. |
| [AD FS migration workshop](https://aka.ms/adfs2azureadworkshop) | Attend a workshop on how to successfully migrate off of AD FS. |
| [AD FS migration wizard](/en-us/entra/identity/enterprise-apps/migrate-ad-fs-application-howto) | Provides custom guidance on migrating to Microsoft Entra ID. |
| [AD FS to Microsoft Entra FAQ](decommission/ad-fs-to-azure-ad-faq) | FAQ for moving from AD FS to Microsoft Entra ID. |

## Resources for migrating authentication from AD FS to Microsoft Entra ID

Additional resources to help you migrate authentication to Microsoft Entra ID.

| Resource | Description |
| --- | --- |
| [Migrate from federation to cloud authentication](/en-us/azure/active-directory/hybrid/migrate-from-federation-to-cloud-authentication) | Detailed information on how to move from using federated authentication with AD FS to cloud authentication with Microsoft Entra ID. |
| [Deployment plan: Migrating from AD FS to password hash sync](https://aka.ms/ADFSTOPHSDPDownload) | With password hash synchronization, hashes of user passwords are synchronized from on-premises Active Directory to Microsoft Entra ID. This allows Microsoft Entra ID to authenticate users without interacting with the on-premises Active Directory. |
| [Deployment plan: Migrating from AD FS to pass-through authentication](https://aka.ms/ADFSTOPTADPDownload) | Microsoft Entra pass-through authentication helps users sign in to both on-premises and cloud-based applications by using the same password. This feature provides your users with a better experience since they have one less password to remember. It also reduces IT helpdesk costs because users are less likely to forget how to sign in when they only need to remember one password. When people sign in using Microsoft Entra ID, this feature validates users' passwords directly against your on-premises Active Directory. |
| [Deployment plans](/en-us/azure/active-directory/fundamentals/active-directory-deployment-plans) | Find more deployment plans for deploying features such as Microsoft Entra multifactor authentication, Conditional Access, user provisioning, seamless SSO, self-service password reset, and more! |
| [Tool: Active Directory Federation Services Migration Readiness Script](https://aka.ms/migrateapps/adfstools) | This is a script you can run on your on-premises Active Directory Federation Services (AD FS) server to determine the readiness of apps for migration to Microsoft Entra ID. |

## Resources for migrating applications from AD FS to Microsoft Entra ID

Additional resources to help you migrate application access to Microsoft Entra ID.

| Resource | Description |
| --- | --- |
| [Migrating your apps to Microsoft Entra ID](https://aka.ms/migrateapps/whitepaper) | This article presents the benefits of migration, and describes how to plan for migration in four clearly-outlined phases: discovery, classification, migration, and ongoing management. You’ll be guided through how to think about the process and break down your project into easy-to-consume pieces. Throughout the article there are links to important resources that will help you along the way. |
| [Developer tutorial: AD FS to Microsoft Entra application migration playbook for developers](https://aka.ms/adfsplaybook) | This set of ASP.NET code samples and accompanying tutorials will help you learn how to safely and securely migrate your applications integrated with Active Directory Federation Services (AD FS) to Microsoft Entra ID. This tutorial is focused towards developers who not only need to learn how to configure apps on both AD FS and Microsoft Entra ID, but also become aware and confident of changes their code base will require in this process. |
| [Deployment plan: Enabling single sign-on to a SaaS app with Microsoft Entra ID](https://aka.ms/SSODPDownload) | Single sign-on (SSO) helps you access all the apps and resources you need to do business, while signing in only once, using a single user account. For example, after a user has signed in, the user can move from Microsoft Office, to SalesForce, to Box without authenticating (for example, typing a password) a second time. |
| [Deployment plan: Extending apps to Microsoft Entra ID with Application Proxy](https://aka.ms/AppProxyDPDownload) | Providing access from employee laptops and other devices to on-premises applications has traditionally involved virtual private networks (VPNs) or demilitarized zones (DMZs). Not only are these solutions complex and hard to make secure, but they are costly to set up and manage. Microsoft Entra application proxy makes it easier to access on-premises applications. |
| [Identity governance for applications](/en-us/azure/active-directory/governance/identity-governance-applications-prepare) | This guide outlines what you need to do if you're migrating identity governance for an application from a previous identity governance technology, to connect Microsoft Entra ID to that application. |