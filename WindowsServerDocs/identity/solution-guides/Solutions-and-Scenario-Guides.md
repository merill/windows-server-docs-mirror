---
layout: Conceptual
title: Solutions and Scenario Guides | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/solution-guides/solutions-and-scenario-guides
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Solutions and Scenario Guides'
author: robinharwood
ms.author: roharwoo
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: solution-overview
locale: en-us
document_id: d3d94a23-8db0-93de-5ba1-aab34393c72e
document_version_independent_id: bc380574-aca5-7949-f07b-cc4bf0abef78
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/solution-guides/Solutions-and-Scenario-Guides.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/solution-guides/solutions-and-scenario-guides
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/solution-guides/Solutions-and-Scenario-Guides.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 84f9f52c-6f38-4444-960a-ab2fb100b622
---

# Solutions and Scenario Guides | Microsoft Learn

With Microsoft's access and information protection solutions, you can deploy and configure access to corporate resources across your on-premises environment and cloud applications. And you can do it while protecting corporate information.

Access and Information Protection

| Guide | How can this guide help you |
| --- | --- |
| [Secure access to company resources from any location on any device](/en-us/previous-versions/windows/it-pro/solutions-guidance/dn550982%28v=ws.11%29) | This guide shows how to allow employees to use personal and company devices to securely access corporate applications and data. |
| [Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications](../ad-fs/operations/join-to-workplace-from-any-device-for-sso-and-seamless-second-factor-authentication-across-company-applications) | Employees can access applications and data everywhere, on any device. Employees can use Single Sign-On in browser applications or enterprise applications. Administrators can control who has access to company resources that are based on application, user, device, and location. |
| [Manage Risk with Additional Multi-Factor Authentication for Sensitive Applications](../ad-fs/operations/manage-risk-with-additional-multi-factor-authentication-for-sensitive-applications) | In this scenario, you enable MFA based on the user's group membership data for a specific application. In other words, you will set up an authentication policy on your federation server to require MFA when users that belong to a certain group request access to a specific application that is hosted on a web server. |
| [Manage Risk with Conditional Access Control](../ad-fs/operations/manage-risk-with-conditional-access-control) | Access control in AD FS is implemented with issuance authorization claim rules that are used to issue a permit or deny claims that will determine whether a user or a group of users will be allowed to access AD FS-secured resources or not. Authorization rules can only be set on relying party trusts. |
| [Configuring Certificate Enrollment Web Service for certificate key-based renewal on a custom port](certificate-enrollment-certificate-key-based-renewal) | This article provides step-by-step instructions to implement the Certificate Enrollment Web Service (or Certificate Enrollment Policy (CEP) / Certificate Enrollment Service (CES)) on a custom port other than 443 for certificate key-based renewal to take advantage of the automatic renewal feature of CEP and CES. |