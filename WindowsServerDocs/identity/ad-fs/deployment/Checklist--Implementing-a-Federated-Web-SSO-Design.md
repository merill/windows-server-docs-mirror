---
layout: Conceptual
title: Checklist - Implementing a Federated Web SSO Design | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/checklist--implementing-a-federated-web-sso-design
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Checklist: Implementing a Federated Web SSO Design'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: checklist
locale: en-us
document_id: 28177dd2-b964-0074-8f0e-72350777f066
document_version_independent_id: 4ba112a1-99aa-e980-1cbd-e8967bc45f4d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Checklist--Implementing-a-Federated-Web-SSO-Design.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/checklist--implementing-a-federated-web-sso-design
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Checklist--Implementing-a-Federated-Web-SSO-Design.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 2bc1edc8-51d8-ad2a-eeab-c5aeab64ec58
---

# Checklist - Implementing a Federated Web SSO Design | Microsoft Learn

This parent checklist includes cross-reference links to important concepts about the Federated Web Single-Sign-On (SSO) design for Active Directory Federation Services (AD FS). It also contains links to subordinate checklists that will help you complete the tasks that are required to implement this design.

Note

Complete the tasks in this checklist in order. When a reference link takes you to a conceptual topic or to a subordinate checklist, return to this topic after you review the conceptual topic or you complete the tasks in the subordinate checklist so that you can proceed with the remaining tasks in this checklist.

![Icon for the Implementing a Federated Web SSO Design check list.](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**Checklist: Implementing a Federated Web SSO Design**

| Task | Reference |
| --- | --- |
| Review important concepts about the Federated Web SSO design and determine which AD FS deployment goals you can use to customize this design to meet the needs of your organization. | ![Icon for the Federated Web SSO Design link you can use in reference to implementing a federated Web SSO design.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Federated Web SSO Design](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807050%28v=ws.11%29)<br>![Icon for the Identifying Your AD FS Deployment Goals link you can use in reference to implementing a federated Web SSO design.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Identifying Your AD FS Deployment Goals](../design/identifying-your-ad-fs-deployment-goals)<br><br>![Icon for the Planning Your Deployment link you can use in reference to implementing a federated Web SSO design.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Planning Your Deployment](../design/planning-your-deployment) |
| Review the hardware, software, certificate, Domain Name System (DNS), attribute store, and client requirements for deploying AD FS in your organization. | ![Icon for the Appendix A: Reviewing AD FS Requirements link you can use in reference to implementing a federated Web SSO design.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Appendix A: Reviewing AD FS Requirements](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff678034%28v=ws.11%29) |
| Review important concepts about claims, claim rules, attribute stores, and the AD FS configuration database before deploying AD FS in both partner organizations. | ![Icon for the Understanding Key AD FS Concepts link you can use in reference to implementing a federated Web SSO design.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Understanding Key AD FS Concepts](../technical-reference/understanding-key-ad-fs-concepts) |
| According to your design plan, install one or more federation servers in each partner organization. **Note:** For the Federated Web SSO design, you need at least one federation server in the account partner organization and at least one federation server in the resource partner organization. | ![Icon for the Checklist: Setting Up a Federation Server link you can use in reference to implementing a federated Web SSO design.](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server) |
| (Optional) Determine whether or not your organization needs a federation server proxy. If your design plan calls for a proxy, you can install one or more federation server proxies in each partner organization. | ![Icon for the Checklist: Setting Up a Federation Server Proxy link you can use in reference to implementing a federated Web SSO design.](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Checklist: Setting Up a Federation Server Proxy](checklist--setting-up-a-federation-server-proxy) |
| According to your design plan, share certificates, configure clients, and configure the trust relationships in both partner organizations so that they can communicate over a federation trust. | ![Icon for the Checklist: Configuring the Account Partner Organization link you can use in reference to implementing a federated Web SSO design.](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Checklist: Configuring the Account Partner Organization](checklist--configuring-the-account-partner-organization)<br>![Icon for the Checklist: Configuring the Resource Partner Organization link you can use in reference to implementing a federated Web SSO design.](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Checklist: Configuring the Resource Partner Organization](checklist--configuring-the-resource-partner-organization) |
| If you are an administrator in the resource partner organization, claims-enable your Web browser application, Web service application, or Microsoft® Office SharePoint® Server application using WIF and the WIF SDK. | ![Icon for the Windows Identity Foundation link you can use in reference to implementing a federated Web SSO design.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Windows Identity Foundation](/en-us/previous-versions/troubleshoot/dotnet/framework/windows-identity-foundation)<br>![federated web sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Windows Identity Foundation SDK](/en-us/previous-versions/troubleshoot/dotnet/framework/windows-identity-foundation) |