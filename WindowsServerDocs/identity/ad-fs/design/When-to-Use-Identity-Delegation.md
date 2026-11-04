---
layout: Conceptual
title: When to Use Identity Delegation | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/when-to-use-identity-delegation
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: When to Use Identity Delegation'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: bf97e101-f9f8-3691-e3db-494a0a3a0510
document_version_independent_id: 1cd9713f-7f83-19c5-e32e-04f723b18993
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/When-to-Use-Identity-Delegation.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/when-to-use-identity-delegation
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/When-to-Use-Identity-Delegation.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 1960825d-8586-ca46-927c-43a852bc944e
---

# When to Use Identity Delegation | Microsoft Learn

## What is identity delegation?

Identity delegation is a feature of Active Directory Federation Services (AD FS) that allows administrator-specified accounts to impersonate users. The account that impersonates the user is called the *delegate*. This delegation capability is critical for many distributed applications for which there is a series of access control checks that must be made sequentially for each application, database, or service that is in the authorization chain for the originating request. Many real-world scenarios exist in which a Web application "front end" must retrieve data from a more secure "back end", such as a Web service that is connected to a Microsoft SQL Server database.

For example, an existing parts-ordering Web site can be enhanced programmatically so that it allows partner organizations to view their own purchase history and account status. For security reasons, all partner financial data is stored in a secure database on a dedicated Structured Query Language (SQL) server. In this situation, the code in the front-end application knows nothing about the partner organization's financial data. Therefore, it must retrieve that data from another computer elsewhere on the network that hosts (in this case) the Web service for the parts database (the back end).

For this data-retrieval process to succeed, some succession of authorization "hand-shaking" must take place between the Web application and the Web service for the parts database, as shown in the following illustration.

![identity delegation](media/adfs2_identitydelegationconcept.gif)

Because the original request was made to the Web server itself, which is likely to be located in a completely different organization from the organization of the user who is attempting to access the Web server, the security token that is sent along with the request does not meet the authorization criteria required to access any other computer besides the Web server. Therefore, the only way that the originating user request can be fulfilled is by placing an intermediate federation server in the resource partner organization to help with reissuing a security token that does have the appropriate access privileges.

## How does identity delegation work?

Web applications in multitier application architectures often call Web services to access common data or functionality. It is important for these Web services to know the identity of the original user so that the service can make authorization decisions and facilitate auditing. In this case, the front-end Web application represents the user to the Web service as a delegate. AD FS facilitates this scenario by allowing Active Directory accounts to act as a user to another relying party. An identity delegation scenario is shown in the following illustration.

![Illustration that shows an identity delegation scenario.](media/adfs2_identitydelegationsteps.gif)

1. Frank attempts to access part-ordering history from a Web application in another organization. His client computer requests and receives a token from AD FS for the front-end part-ordering Web application.
2. The client computer sends a request to the Web application, including the token obtained in step 1, to prove the client's identity.
3. The Web application needs to communicate with the Web service to complete its transaction for the client. The Web application contacts AD FS to obtain a delegation token to interact with the Web service. Delegation tokens are security tokens that are issued to a delegate to act as a user. AD FS returns a delegation token with claims about the client, targeted for the Web service.
4. The Web application uses the token that was obtained from AD FS in step 3 to access the Web service that is acting as the client. Examining the delegation token, the Web service can determine that the Web application is acting as the client. The Web service executes its authorization policy, logs the request, and provides the needed parts history data that was originally requested by Frank to the Web application and therefore to Frank.

For a particular delegate, AD FS can limit the Web services for which the Web application may request a delegation token. The client computer does not have to have an Active Directory account for this operation to succeed. Finally, as noted previously, the Web service can easily determine the identity of the delegate that is acting as the user. This allows Web services to exhibit different behavior based on whether they are talking directly to the client computer or through a delegate.

## Configuring AD FS for identity delegation

You can use the AD FS Management snap-in to configure AD FS for identity delegation whenever you need to facilitate the data retrieval process. After you configure it, AD FS can generate new security tokens that will include the authorization context that the back-end service may require before it can provide access to the protected data.

AD FS does not restrict which users can be impersonated. After you configure AD FS for identity delegation, it does the following:

- It determines which servers can be delegated the authority to request tokens to impersonate a user.
- It establishes and keeps separate both the identity context for the client account that is delegated and the server that acts as a delegate.

You can configure identity delegation by adding delegation authorization rules to a relying party trust in the AD FS Management snap-in. For more information about how to do this, see [Checklist: Creating Claim Rules for a Relying Party Trust](../deployment/checklist--creating-claim-rules-for-a-relying-party-trust).

## Configuring the front-end Web application for identity delegation

Developers have several options that they can use to appropriately program the Web front-end application or service to redirect delegation requests to an AD FS computer. For more information about how to customize a Web application to work with identity delegation, see the [Windows Identity Foundation SDK](/en-us/previous-versions/troubleshoot/dotnet/framework/windows-identity-foundation).