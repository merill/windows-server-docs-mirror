---
layout: Conceptual
title: Web Application Proxy in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/web-application-proxy/web-app-proxy-windows-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: 'Learn more about: Web Application Proxy in Windows Server'
ms.author: roharwoo
author: robinharwood
ms.date: 2026-04-16T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 4eed377a-d761-5bac-f45a-5af6de77de2a
document_version_independent_id: 4eed377a-d761-5bac-f45a-5af6de77de2a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/web-application-proxy/web-app-proxy-windows-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/web-application-proxy/web-app-proxy-windows-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/web-application-proxy/web-app-proxy-windows-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: e08c7b79-90d3-81f2-f721-13abffe67fe5
---

# Web Application Proxy in Windows Server | Microsoft Learn

**This content is relevant for the on-premises version of Web Application Proxy. To enable secure access to on-premises applications over the cloud, see the [Microsoft Entra application proxy content](/en-us/entra/identity/app-proxy/overview-what-is-app-proxy).**

Web Application Proxy is a Remote Access role service in Windows Server. It functions as a reverse proxy, enabling users outside the corporate network to securely access web applications and services hosted on internal servers. Web Application Proxy integrates with Active Directory Federation Services (AD FS) to provide preauthentication, ensuring that only authenticated users can access published applications. It supports publishing applications for both AD FS preauthentication and pass-through authentication scenarios.

The content in this section describes what's new and changed in the Web Application Proxy for Windows Server. The new features and changes listed here are the ones most likely to have the greatest impact as you work with the Preview.

## Web Application Proxy features

- Preauthentication for HTTP Basic application publishing

    HTTP Basic is the authorization protocol used by many protocols, including ActiveSync, to connect rich clients, including smartphones, with your Exchange mailbox. Web Application Proxy traditionally interacts with AD FS using redirections which is not supported on ActiveSync clients. This new version of Web Application Proxy provides support to publish an app using HTTP basic by enabling the HTTP app to receive a non-claims relying party trust for the application to the Federation Service.

    For more information on HTTP basic publishing, see [Publishing Applications using AD FS Preauthentication](publishing-applications-using-ad-fs-preauthentication#publish-an-application-that-uses-http-basic)
- Wildcard domain publishing of applications

    To support scenarios such as SharePoint 2013, the external URL for the application can now include a wildcard to enable you to publish multiple applications from within a specific domain, for example, https://\*.sp-apps.contoso.com. This will simplify publishing of SharePoint apps.
- HTTP to HTTPS redirection

    In order to make sure your users can access your app, even if they neglect to type HTTPS in the URL, Web Application Proxy now supports HTTP to HTTPS redirection.
- HTTP Publishing

    It is now possible to publish HTTP applications using pass-through preauthentication
- Publishing of Remote Desktop Gateway apps

    For more information on RDG in Web Application Proxy, see [Publishing Applications with SharePoint, Exchange and RDG](publishing-applications-with-sharepoint,-exchange-and-rdg)
- New debug log for better troubleshooting and improved service log for complete audit trail and improved error handling

    For more information on troubleshooting, see [Troubleshooting Web Application Proxy](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn770156%28v=ws.11%29)
- Administrator Console UI improvements
- Propagation of client IP address to backend applications