---
layout: Conceptual
title: Understanding Key Active Directory Federation Services Concepts | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/technical-reference/understanding-key-ad-fs-concepts
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Understanding Key AD FS Concepts'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 2f52b43d-6e59-b36d-878b-e32123d7c7ee
document_version_independent_id: 2a12a565-9bb0-abd5-6a00-83f4d210f4e8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/technical-reference/understanding-key-ad-fs-concepts
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 337237d8-0b0d-04f1-8554-572fa9e07c3a
---

# Understanding Key Active Directory Federation Services Concepts | Microsoft Learn

It is recommended that you learn about the important concepts for Active Directory Federation Services and become familiar with its feature set.

Tip

You can find additional AD FS resource links at the Understanding Key AD FS Concepts.

## AD FS terminology used in this guide

| AD FS term | Definition |
| --- | --- |
| Account partner organization | A federation partner organization that is represented by a claims provider trust in the Federation Service. The account partner organization contains the users that will access Web-based applications in the resource partner. |
| Account federation server | The federation server in the account partner organization. The account federation server issues security tokens to users based on user authentication. The server authenticates the user, extracts the relevant attributes and group membership information out of the attribute store, packages this information into claims, and generates and signs a security token (which contains the claims) to return to the user—either to be used in its own organization or to be sent to a partner organization. |
| AD FS configuration database | A database used to store all configuration data that represents a single AD FS instance or Federation Service. This configuration data can be stored in either a SQL Server database or using the Windows Internal Database feature included with Windows Server 2016, Windows Server 2012 and 2012 R2, and Windows Server 2008 and 2008 R2. You can create the AD FS configuration database for SQL Server using the Fsconfig.exe command-line tool and for Windows Internal Database using the AD FS Federation Server Configuration Wizard. |
| Claims provider | The organization that provides claims to its users. See account partner organization. |
| Claims provider trust | In the AD FS Management snap-in, claims provider trusts are trust objects typically created in resource partner organizations to represent the organization in the trust relationship whose accounts will be accessing resources in the resource partner organization. A claims provider trust object consists of a variety of identifiers, names, and rules that identify this partner to the local Federation Service. |
| Local Claims Provider Trust | A trust object that represents AD LDS or third-party LDAP-based directories in an AD FS farm. A local claims provider trust object consists of a variety of identifiers, names, and rules that identify this LDAP-based directory to the local Federation Service. |
| Federation metadata | The data format for communicating configuration information between a claims provider and a relying party to facilitate proper configuration of claims provider trusts and relying party trusts. The data format is defined in Security Assertion Markup Language (SAML) 2.0, and it is extended in WS-Federation. |
| Federation server | A Windows Server that has been configured using the AD FS Federation Server Configuration Wizard to act in the federation server role. A federation server issues tokens and serves as part of a Federation Service. |
| Federation server proxy | A Windows Server that has been configured using the AD FS Federation Server Proxy Configuration Wizard to act as an intermediary proxy service between an Internet client and a Federation Service that is located behind a firewall on a corporate network. |
| Primary federation server | A Windows Server that has been configured in the federation server role using the AD FS Federation Server Configuration Wizard and has a read/write copy of the AD FS configuration database.  The primary federation server is created when you use the AD FS Federation Server Configuration Wizard and select the option to create a new Federation Service and make that computer the first federation server in the farm. All other federation servers in this farm must replicate changes made on the primary federation server to a read-only copy of the AD FS configuration database that is stored locally. The term "primary federation server" does not apply when the AD FS configuration database is stored in an SQL database as all federation servers can equally read and write to a configuration database stored on a SQL Server. |
| Relying party | The organization that receives and processes claims. See resource partner organization. |
| Relying party trust | In the AD FS Management snap-in, relying party trusts are trust objects typically created in:<br>- Account partner organizations to represent the organization in the trust relationship whose accounts will be accessing resources in the resource partner organization.- Resource partner organizations to represent the trust between the Federation Service and a single web-based application.<br><br>A relying party trust object consists of a variety of identifiers, names, and rules that identify this partner or web-application to the local Federation Service. |
| Resource federation server | The federation server in the resource partner organization. The resource federation server typically issues security tokens to users based on a security token that is issued by an account federation server. The server receives the security token, verifies the signature, applies claim rule logic to the unpackaged claims to produce the desired outgoing claims, generates a new security token (with the outgoing claims) based on information in the incoming security token, and signs the new token to return to the user and ultimately to the Web application. |
| Resource partner organization | A federation partner that is represented by a relying party trust in the Federation Service. The resource partner issues claims-based security tokens that contains published Web-based applications that users in the account partner can access. |

## Overview of AD FS

AD FS is an identity access solution that provides client computers (internal or external to your network) with seamless SSO access to protected Internet-facing applications or services, even when the user accounts and applications are located in completely different networks or organizations.

When an application or service is in one network and a user account is in another network, typically the user is prompted for secondary credentials when he or she attempts to access the application or service. These secondary credentials represent the user's identity in the realm where the application or service resides. They are usually required by the Web server that hosts the application or service so that it can make the most appropriate authorization decision.

With AD FS, organizations can bypass requests for secondary credentials by providing trust relationships (federation trusts) that these organizations can use to project a user's digital identity and access rights to trusted partners. In this federated environment, each organization continues to manage its own identities, but each organization can also securely project and accept identities from other organizations.

- [The Role of Attribute Stores](the-role-of-attribute-stores)
- [The Role of the AD FS Configuration Database](the-role-of-the-ad-fs-configuration-database)
- [The Role of Claims](the-role-of-claims)
- [The Role of Claim Rules](the-role-of-claim-rules)
- [The Role of the Claims Engine](the-role-of-the-claims-engine)
- [The Role of the Claims Pipeline](the-role-of-the-claims-pipeline)
- [The Role of the Claim Rule Language](the-role-of-the-claim-rule-language)
- [Determine the Type of Claim Rule Template to Use](determine-the-type-of-claim-rule-template-to-use)
- [How URIs Are Used in AD FS](how-uris-are-used-in-ad-fs)