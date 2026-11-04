---
layout: Conceptual
title: Provide Your Active Directory Users Access to the Applications and Services of Other Organizations | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/provide-your-active-directory-users-access-to-the-applications-and-services-of-other-organizations
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Provide Your Active Directory Users Access to the Applications and Services of Other Organizations'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: cbc8c295-4d65-ff9e-8d85-e9fb0700ab04
document_version_independent_id: 6715074d-8c4c-52d8-aea8-63f1f4294841
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Provide-Your-Active-Directory-Users-Access-to-the-Applications-and-Services-of-Other-Organizations.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/provide-your-active-directory-users-access-to-the-applications-and-services-of-other-organizations
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Provide-Your-Active-Directory-Users-Access-to-the-Applications-and-Services-of-Other-Organizations.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: a0925c67-877e-3eaa-b6cd-6a61c5ad6d26
---

# Provide Your Active Directory Users Access to the Applications and Services of Other Organizations | Microsoft Learn

This Active Directory Federation Services (AD FS) deployment goal builds on the goal in [Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services](provide-your-active-directory-users-access-to-your-claims-aware-applications-and-services).

When you are an administrator in the account partner organization and you have a deployment goal to provide federated access for employees to hosted resources in another organization:

- Employees who are logged on to an Active Directory domain in the corporate network can use single-sign-on (SSO) functionality to access multiple Web-based applications or services, which are secured by AD FS, when the applications or services are in a different organization. For more information, see [Federated Web SSO Design](federated-web-sso-design).

    For example, Fabrikam may want corporate network employees to have federated access to Web services that are hosted in Contoso.
- Remote employees who are logged on to an Active Directory domain can obtain AD FS tokens from the federation server in your organization to gain federated access to AD FS–secured Web-based applications or services that are hosted in another organization.

    For example, Fabrikam may want its remote employees to have federated access to AD FS–secured services that are hosted in Contoso, without requiring the Fabrikam employees to be on the Fabrikam corporate network.

In addition to the foundational components that are described in [Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services](provide-your-active-directory-users-access-to-your-claims-aware-applications-and-services) and that are shaded in the following illustration, the following components are required for this deployment goal:

- **Account partner federation server proxy:** Employees that access the federated service or application from the Internet can use this AD FS component to perform authentication. By default, this component performs forms authentication, but it can also perform basic authentication. You can also configure this component to perform Secure Sockets Layer (SSL) client authentication if employees at your organization have certificates to present. For more information, see [Where to Place a Federation Server Proxy](where-to-place-a-federation-server-proxy).
- **Perimeter DNS:** This implementation of Domain Name System (DNS) provides the host names for the perimeter network. For more information about how to configure perimeter DNS for a federation server proxy, see [Name Resolution Requirements for Federation Server Proxies](name-resolution-requirements-for-federation-server-proxies).
- **Remote employee:** The remote employee accesses a Web-based application (through a supported Web browser) or a Web-based service (through an application), using valid credentials from the corporate network, while the employee is offsite using the Internet. The employee's client computer in the remote location communicates directly with the federation server proxy to generate a token and authenticate to the application or service.

After reviewing the information in the linked topics, you can begin deploying this goal by following the steps in [Checklist: Implementing a Federated Web SSO Design](../deployment/checklist--implementing-a-federated-web-sso-design).

The following illustration shows each of the required components for this AD FS deployment goal.

![access to your apps](media/50af4837-31e0-451f-a942-e705c2300065.gif)