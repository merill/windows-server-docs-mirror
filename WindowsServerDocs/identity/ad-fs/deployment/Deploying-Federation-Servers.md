---
layout: Conceptual
title: Deploying Federation Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/deploying-federation-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Deploying Federation Servers'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 7f89fc59-b291-1a5e-304b-2fe21d78253e
document_version_independent_id: 81e774f7-21f6-33b2-9e4c-c83875959996
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Deploying-Federation-Servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/deploying-federation-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Deploying-Federation-Servers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: df585334-b6d7-3054-f5b2-b6300e02eed6
---

# Deploying Federation Servers | Microsoft Learn

To deploy federation servers in Active Directory Federation Services (AD FS), complete each of the tasks in [Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server).

Note

When you use this checklist, we recommend that you first read the references to federation server planning in the [AD FS Design Guide in Windows Server 2012](../design/ad-fs-design-guide-in-windows-server-2012) before you begin the procedures for configuring the servers. Following the checklist in this way provides a better understanding of the design and deployment process for federation servers.

## About federation servers

Federation servers are computers running Windows Server 2008 with the AD FS software installed that have been configured to act in the federation server role. Federation servers authenticate or route requests from user accounts in other organizations and from client computers that can be located anywhere on the Internet.

The act of installing the AD FS software on a computer and using the AD FS Federation Server Configuration Wizard to configure it for the federation server role makes that computer a federation server. It also makes the AD FS Management snap-in available on that computer in the **Start\Administrative Tools\** menu so that you can specify the following:

- The AD FS host name where partner organizations and applications will send token requests and responses
- The AD FS identifier that partner organizations and applications will use to identify the unique name or location of your organization
- The token-signing certificate that all federation servers in a server farm will use to issue and sign tokens
- The location of customized ASP.NET Web pages for client logon, logoff, and account partner discovery that will enhance the client experience

    Note

    The majority of these core user interface (UI) settings are contained in the web.config file on each federation server. The AD FS host name and AD FS identifier values are not specified in the web.config file.

Federation servers host a claims issuance engine that issues tokens based on the credentials (for example, user name and password) that are presented to it. A security token is a cryptographically signed data unit that expresses one or more claims. A claim is a statement that a server makes (for example, name, identity, key, group, privilege, or capability) about a client. After the credentials are verified on the federation server (through the user logon process), claims for the user are collected through examination of the user attributes that are stored in the specified attribute store.

In Federated Web Single-Sign-On (SSO) designs (AD FS designs in which two or more organizations are involved), claims can be modified by claim rules for a specific relying party. The claims are built into a token that is sent to a federation server in the resource partner organization. After a federation server in the resource partner receives the claims as incoming claims, it executes the claims issuance engine to run a set of claim rules to filter, pass through, or transform those claims. The claims are then built into a new token that is sent to the Web server in the resource partner.

In the Web SSO design (an AD FS design in which only one organization is involved), a single federation server can be used so that employees can log on once and still access multiple applications.