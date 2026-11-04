---
layout: Conceptual
title: AD FS to Microsoft Entra FAQ | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/decommission/ad-fs-to-azure-ad-faq
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: FAQ for migrating from AD FS to Microsoft Entra ID
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: faq
locale: en-us
document_id: 967cf275-c5f8-b0f2-b17a-66bc137dcf98
document_version_independent_id: 967cf275-c5f8-b0f2-b17a-66bc137dcf98
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/decommission/ad-fs-to-azure-ad-faq.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/decommission/ad-fs-to-azure-ad-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/decommission/ad-fs-to-azure-ad-faq.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 872946ca-8b3e-0f36-7c8e-0c538bb3d169
---

# AD FS to Microsoft Entra FAQ | Microsoft Learn

Microsoft Entra ID provides a simple cloud-based sign-in experience to all your resources and apps with strong authentication and real-time, risk-based adaptive access policies to grant access to resources reducing operational costs of managing and maintaining an AD FS environment and increasing IT efficiency.

For more info on **why** you should upgrade from AD FS to Microsoft Entra ID, visit [moving from AD FS to Microsoft Entra ID](https://aka.ms/adfs2aad). See [migrate from federation to cloud authentication](/en-us/azure/active-directory/hybrid/migrate-from-federation-to-cloud-authentication) to understand **how** to upgrade from AD FS.

## General questions

This document will provide you with answers to frequently asked questions with migrating from AD FS to Microsoft Entra ID.

**Can I run AD FS side by side with Password Hash Sync or Pass Through Authentication?**

Yes you can. This is quite common. Using staged rollout can help you validate a subset of your users are able to authenticate to Microsoft Entra ID directly while the domain remains federated. This document [Migrate from federation to cloud authentication](/en-us/azure/active-directory/hybrid/migrate-from-federation-to-cloud-authentication) will walk you through the process.

**When accessing sites through AD FS internally users get a single-sign on experience. How do we keep the same experience when moving to Microsoft Entra ID?**

There are a few ways. The first and recommend way is to [Microsoft Entra hybrid join](/en-us/azure/active-directory/devices/concept-azure-ad-join-hybrid) your existing Windows 10/11 domain joined machines or use Microsoft Entra join. This will provide you with the same seamless signle-sign on experience. The second way would be to leverage [seamless single-sign on](/en-us/azure/active-directory/hybrid/how-to-connect-sso-how-it-works) for non Microsoft Entra hybrid joined machines or downlevel Windows clients can still get that same experience.

**I’m registering Microsoft Entra hybrid joined devices using AD FS device claims. How do I allow devices to continue to complete their Hybrid AADJ process with AD FS?**

You can follow the [configure Microsoft Entra hybrid join](/en-us/azure/active-directory/devices/howto-hybrid-azure-ad-join#managed-domains) process for devices to complete the registration process without AD FS.

**I have authorization rules in AD FS. What are the equivalent way to do this in Microsoft Entra ID?**

These would translate into [Microsoft Entra Conditional Access policies](/en-us/azure/active-directory/conditional-access/overview). There are several pre-built [template](/en-us/azure/active-directory/conditional-access/concept-conditional-access-policy-common) policies to start with.

**When putting users into a staged rollout group are their current sessions impacted and forced to re-authenticate?**

No, their current session will remain valid and the next time they would need to authenticate they would authenticate using managed authentication instead of federation.

**I have a claims provider trust with another company to access resources? How should I move this trust relationship?**

You should look to take advantage of [Microsoft Entra B2B](/en-us/azure/active-directory/external-identities/what-is-b2b) to accomplish the same authentication access.

**We have custom claim rules can Microsoft Entra ID support these?**

Yes depending on the rules needed. The best place to investigate is to use [AD FS application activity report](/en-us/azure/active-directory/manage-apps/migrate-adfs-application-activity) and then see how to [customize SAML claims](/en-us/azure/active-directory/develop/active-directory-saml-claims-customization)

**When switching a domain from federated to managed how long does it take for the change to take place?**

It can take up to 4 hours to fully cutover so [plan your maintenance window accordingly](/en-us/azure/active-directory/hybrid/migrate-from-federation-to-cloud-authentication#plan-the-maintenance-window)

**Is AD FS required for using O365?**

No, O365 can authenticate you directly without needing ADFS.

**Once I move the application configuration to Microsoft Entra ID, is there anything else I have to do to complete the migration?**

Yes, the migration of an application to Microsoft Entra isn’t complete until you have reconfigured the app itself (cutover) to use Microsoft Entra ID.

**Is ADFS required so users can login with their Email Address or User Principal Name (UPN)?**

No, Microsoft Entra ID supports sign-in with an [Email Address](/en-us/azure/active-directory/authentication/howto-authentication-use-email-signin) or User Principal Name.