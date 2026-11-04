---
layout: Conceptual
title: Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/provide-your-active-directory-users-access-to-your-claims-aware-applications-and-services
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 8b7c8308-89a5-910c-e7cb-38b760ae5481
document_version_independent_id: 37ca152c-6ab9-21e6-8e3a-05862a2c849e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/provide-your-active-directory-users-access-to-your-claims-aware-applications-and-services
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: de5b163a-d1ae-ef84-a734-91db18257f3f
---

# Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services | Microsoft Learn

When you are an administrator in the account partner organization in an Active Directory Federation Services (AD FS) deployment and you have a deployment goal to provide single-sign-on (SSO) access for employees on the corporate network to your hosted resources:

- Employees who are logged on to an Active Directory forest in the corporate network can use SSO to access multiple applications or services in the perimeter network in your own organization. These applications and services are secured by AD FS.

    For example, Fabrikam may want corporate network employees to have federated access to Web-based applications that are hosted in the perimeter network for Fabrikam.
- Remote employees who are logged on to an Active Directory domain can obtain AD FS tokens from the federation server in your organization to gain federated access to AD FS-secured Web-based applications or services that also reside in your organization.
- Information in the Active Directory attribute store can be populated into the employees' AD FS tokens.

The following components are required for this deployment goal:

- **Active Directory Domain Services (AD DS):** AD DS contains the employees' user accounts that are used to generate AD FS tokens. Information, such as group memberships and attributes, is populated into AD FS tokens as group claims and custom claims.

    Note

    You can also use Lightweight Directory Access Protocol (LDAP) or Structured Query Language (SQL) to contain the identities for AD FS token generation.
- **Corporate DNS:** This implementation of Domain Name System (DNS) contains a simple host (A) resource record so that intranet clients can locate the account federation server. This implementation of DNS may also host other DNS records that are required in the corporate network. For more information, see [Name Resolution Requirements for Federation Servers](name-resolution-requirements-for-federation-servers).
- **Account partner federation server:** This federation server is joined to a domain in the account partner forest. It authenticates employee user accounts and generates AD FS tokens. The client computer for the employee performs Windows Integrated Authentication against this federation server to generate an AD FS token. For more information, see [Review the Role of the Federation Server in the Account Partner](review-the-role-of-the-federation-server-in-the-account-partner).

    The account partner federation server can authenticate the following users:

    - Employees with user accounts in this domain
    - Employees with user accounts anywhere in this forest
    - Employees with user accounts anywhere in forests that are trusted by this forest (through a two-way Windows trust)
- **Employee:** An employee accesses a Web-based service (through an application) or a Web-based application (through a supported Web browser) while he or she is logged on to the corporate network. The employee's client computer on the corporate network communicates directly with the federation server for authentication.

After reviewing the information in the linked topics, you can begin deploying this goal by following the steps in [Checklist: Implementing a Federated Web SSO Design](../deployment/checklist--implementing-a-federated-web-sso-design).

The following illustration shows each of the required components for this AD FS deployment goal.

![access to your claims](media/31394ea8-fecb-4372-ac3f-cc3cf566ffc9.gif)