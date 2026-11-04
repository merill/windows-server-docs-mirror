---
layout: Conceptual
title: Windows Server 2012 AD FS Deployment Guide | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/windows-server-2012-ad-fs-deployment-guide
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Windows Server 2012 AD FS Deployment Guide'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: install-set-up-deploy
locale: en-us
document_id: 104adf3a-b61c-c5cd-8e49-7c6f4df3237d
document_version_independent_id: fd0d63f8-c8f2-5e66-196f-a0b5cab56a1d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Windows-Server-2012-AD-FS-Deployment-Guide.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/windows-server-2012-ad-fs-deployment-guide
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Windows-Server-2012-AD-FS-Deployment-Guide.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: dd842cb5-269f-5b2c-11f2-44270f243d0c
---

# Windows Server 2012 AD FS Deployment Guide | Microsoft Learn

You can use Active Directory® Federation Services (AD FS) with the Windows Server® 2012 operating system to build a federated identity management solution that extends distributed identification, authentication, and authorization services to Web-based applications across organization and platform boundaries. By deploying AD FS, you can extend your organization's existing identity management capabilities to the Internet.

You can deploy AD FS to:

- Provide your employees or customers with a Web-based, single-sign-on (SSO) experience when they need remote access to internally hosted Web sites or services.
- Provide your employees or customers with a Web-based, SSO experience when they access cross-organizational Web sites or services from within the firewalls of your network.
- Provide your employees or customers with seamless access to Web-based resources in any federation partner organization on the Internet without requiring employees or customers to log on more than once.
- Retain complete control over your employee or customer identities without using other sign-on providers (Windows Live ID, Liberty Alliance, and others).

## About this guide

This guide is intended for use by system administrators and system engineers. It provides detailed guidance for deploying an AD FS design that has been preselected by you or an infrastructure specialist or system architect in your organization.

If a design has not yet been selected, we recommend that you wait to follow the instructions in this guide until after you have reviewed the design options in the [AD FS Design Guide in Windows Server 2012](../design/ad-fs-design-guide-in-windows-server-2012) and you have selected the most appropriate design for your organization. For more information about using this guide with a design that has already been selected, see [Implementing Your AD FS Design Plan](implementing-your-ad-fs-design-plan).

After you select your design from the design guide and gather the required information about claims, token types, attribute stores, and other items, you can use this guide to deploy your AD FS design in your production environment. This guide provides steps for deploying either of the following primary AD FS designs:

- Web SSO
- Federated Web SSO

Use the checklists in [Implementing Your AD FS Design Plan](implementing-your-ad-fs-design-plan) to determine how best to use the instructions in this guide to deploy your particular design. For information about hardware and software requirements for deploying AD FS, see the [Appendix A: Reviewing AD FS Requirements](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff678034%28v=ws.11%29) in the AD FS Design Guide.

### What this guide does not provide

This guide does not provide:

- Guidance regarding when and where to place federation servers, federation server proxies, or Web servers in your existing network infrastructure. For this information, see [Planning Federation Server Placement](../design/planning-federation-server-placement) and [Planning Federation Server Proxy Placement](../design/planning-federation-server-proxy-placement) in the AD FS Design Guide.
- Guidance for using certification authorities (CAs) to set up AD FS
- Guidance for setting up or configuring specific Web-based applications
- Setup instructions that are specific to setting up a test lab environment.
- Information about how to customize federated logon screens, web.config files, or the configuration database.

## In this guide

- [Planning to Deploy AD FS](planning-to-deploy-ad-fs)
- [Implementing Your AD FS Design Plan](implementing-your-ad-fs-design-plan)
- [Checklist: Implementing a Web SSO Design](checklist--implementing-a-web-sso-design)
- [Checklist: Implementing a Federated Web SSO Design](checklist--implementing-a-federated-web-sso-design)
- [Configuring Partner Organizations](configuring-partner-organizations)
- [Configuring Claim Rules](configuring-claim-rules)
- [Deploying Federation Servers](deploying-federation-servers)
- [Deploying Federation Server Proxies](deploying-federation-server-proxies)
- [Interoperating with AD FS 1.x](interoperating-with-ad-fs-1.x)