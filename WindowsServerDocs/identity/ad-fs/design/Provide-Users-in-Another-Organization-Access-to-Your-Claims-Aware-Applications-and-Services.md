---
layout: Conceptual
title: Provide Users in Another Organization Access to Your Claims-Aware Applications and Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/provide-users-in-another-organization-access-to-your-claims-aware-applications-and-services
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Provide Users in Another Organization Access to Your Claims-Aware Applications and Services'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 616c9abc-37a0-d8c5-8862-88d2e38afd83
document_version_independent_id: 80f283e0-8799-489f-9379-31914134e0f7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Provide-Users-in-Another-Organization-Access-to-Your-Claims-Aware-Applications-and-Services.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/provide-users-in-another-organization-access-to-your-claims-aware-applications-and-services
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Provide-Users-in-Another-Organization-Access-to-Your-Claims-Aware-Applications-and-Services.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e304a407-aebc-7a9e-1c86-fe7a4289a5c9
---

# Provide Users in Another Organization Access to Your Claims-Aware Applications and Services | Microsoft Learn

When you are an administrator in the resource partner organization in Active Directory Federation Services (AD FS) and you have a deployment goal to provide federated access for users in another organization (the account partner organization) to a claims-aware application or a Web-based service that is located in your organization (the resource partner organization):

- Federated users both in your organization and in organizations who have configured a federation trust to your organization (account partner organizations) can access the AD FS secured application or service that is hosted by your organization. For more information, see [Federated Web SSO Design](federated-web-sso-design).

    For example, Fabrikam may want its corporate network employees to have federated access to Web services that are hosted in Contoso.
- Federated users who have no direct association with a trusted organization (such as individual customers), who are logged on to an attribute store that is hosted in your perimeter network, can access multiple AD FS-secured applications, which are also hosted in your perimeter network, by logging on one time from client computers that are located on the Internet. In other words, when you host customer accounts to enable access to applications or services in your perimeter network, customers that you host in an attribute store can access one or more applications or services in the perimeter network simply by logging on once. For more information, see [Web SSO Design](web-sso-design).

    For example, Fabrikam may want its customers to have single-sign-on (SSO) access to multiple applications or services that are hosted in its perimeter network.

The following components are required for this deployment goal:

- **Active Directory Domain Services (AD DS):** The resource partner federation server must be joined to an Active Directory domain.
- **Perimeter DNS:** Domain Name System (DNS) should contain a simple host (A) resource record so that client computers can locate the resource partner federation server and the Web server. The DNS server may host other DNS records that are also required in the perimeter network. For more information, see [Name Resolution Requirements for Federation Servers](name-resolution-requirements-for-federation-servers).
- **Resource partner federation server:** The resource partner federation server validates AD FS tokens that the account partners send. Account partner discovery is performed through this federation server. For more information, see [Review the Role of the Federation Server in the Resource Partner](review-the-role-of-the-federation-server-in-the-resource-partner).
- **Web server:** The Web server can host either a Web application or a Web service. The Web server confirms that it receives valid AD FS tokens from federated users before it allows access to the protected Web application or Web service.

    By using Windows Identity Foundation (WIF), you can develop your Web application or service so that it accepts federated user logon requests that are made with any standard logon method, such as user name and password.

After reviewing the information in the linked topics, you can begin deploying this goal by following the steps in [Checklist: Implementing a Federated Web SSO Design](../deployment/checklist--implementing-a-federated-web-sso-design) and [Checklist: Implementing a Web SSO Design](../deployment/checklist--implementing-a-web-sso-design).

The following illustration shows each of the required components for this AD FS deployment goal.

![access to your claims](media/75358b16-2a6f-4e16-9cc4-b0e614480305.gif)