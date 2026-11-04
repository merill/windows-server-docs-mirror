---
layout: Conceptual
title: When to Create a Federation Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/when-to-create-a-federation-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: When to Create a Federation Server'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 458c5164-0807-5c2b-ed2e-48ef87652ab2
document_version_independent_id: 39f43307-9c79-5081-3874-62b49cc7f211
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/When-to-Create-a-Federation-Server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/when-to-create-a-federation-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/When-to-Create-a-Federation-Server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 8821f774-6799-cb80-08f6-8c3037c8f0c7
---

# When to Create a Federation Server | Microsoft Learn

When you create a federation server in Active Directory Federation Services (AD FS), you provide a means by which your organization can:

- Engage in Web single-sign-on (SSO)–based communication with another organization (that also has at least one federation server) and, when necessary, with the employees in your own organization (who need access over the Internet).
- Enable front end services to impersonate users to infrastructure services using identity delegation. For more information, see [When to Use Identity Delegation](when-to-use-identity-delegation).

The following sections describe some of the key decisions for determining when and where to create one or more federation servers.

## Determine the organizational role for the federation server

To make an informed decision regarding when to create a new federation server, you must first determine in which organization the server will reside. The role that a federation server plays in an organization depends on whether you place the federation server in the account partner organization or in the resource partner organization.

When a federation server is placed in the corporate network of the account partner, its role is to authenticate the user credentials of browser, Web service, or identity selector clients and send security tokens to the clients. For more information, see [Review the Role of the Federation Server in the Account Partner](review-the-role-of-the-federation-server-in-the-account-partner).

When a federation server is placed in the corporate network of the resource partner, its role is to authenticate users, based on a security token that is issued by a federation server in the resource partner organization, or its role is to redirect token requests from configured Web applications or Web services to the account partner organization that the client belongs to. For more information, see [Review the Role of the Federation Server in the Resource Partner](review-the-role-of-the-federation-server-in-the-resource-partner).

## Determine which AD FS design to deploy

You create federation servers in your organization whenever you want to deploy any of the following AD FS designs:

- [Web SSO Design](web-sso-design)
- [Federated Web SSO Design](federated-web-sso-design)

If necessary, an organization that deploys a Federated Web SSO design can configure a single federation server so that it acts in both the account partner role and in the resource partner role. In this case, the federation server may produce Security Assertion Markup Language (SAML) tokens, based on user accounts in its own organization, or reroute token requests to the organization, based on where the users' accounts reside.

Note

For the Federated Web SSO design, there must be at least one federation server in the account partner and at least one federation server in the resource partner.

## Differences between a federation server and a federation server proxy

A federation server can serve out Web pages for sign-in, policy, authentication, and discovery in the same way that a federation server proxy does. The primary differences between a federation server and a federation server proxy have to do with what operations a federation server can perform that a federation server proxy cannot perform.

The following are the operations that only a federation server can perform:

- The federation server performs the cryptographic operations that produce the token. Although federation server proxies cannot produce tokens, they can be used to route or redirect the tokens to clients and, when necessary, back to the federation server. For more information about using federation servers, see [When to Create a Federation Server Proxy](when-to-create-a-federation-server-proxy).
- Federation servers support the use of Windows Integrated Authentication for clients on the corporate network; federation server proxies do not. For more information about using Windows Integrated Authentication with federation server, see [When to Create a Federation Server Farm](when-to-create-a-federation-server-farm).

Caution

Communication between federation servers and SQL Server configuration databases, SQL Server attribute stores, domain controllers, and AD LDS instances is not integrity or confidentiality protected by default. To mitigate this, consider protecting the communication channel between these servers using IPSEC or using a physically secure connection between all of these servers. For communication between federation servers and SQL servers, consider using SSL protection in the connection string. For connections between federation servers and domain controllers, consider turning on Kerberos signing and encryption. For LDAP, LDAP/S is not supported for AD LDS/AD DS.

## How to create a federation server

You can create a federation server using the AD FS Federation Server Configuration Wizard or the Fsconfig.exe command-line tool. When you use either of these tools, you can select any of the following options to create a federation server.

- Create a stand-alone federation server

    For more information about how to set up a stand-alone federation server, see [Create a Stand-Alone Federation Server](../deployment/create-a-stand-alone-federation-server).
- Create the first federation server in a federation server farm

    For more information about how to set up the first federation server or add a federation server to a farm, see [Create the First Federation Server in a Federation Server Farm](../deployment/create-the-first-federation-server-in-a-federation-server-farm).
- Add a federation server to a federation server farm

    For more information about how to add a federation server to a farm, see [Add a Federation Server to a Federation Server Farm](../deployment/add-a-federation-server-to-a-federation-server-farm).

For more detailed information about how each of these options work, see [The Role of the AD FS Configuration Database](../technical-reference/the-role-of-the-ad-fs-configuration-database).

For more information about how to set up all the prerequisites necessary to deploy a federation server, see [Checklist: Setting Up a Federation Server](../deployment/checklist--setting-up-a-federation-server).