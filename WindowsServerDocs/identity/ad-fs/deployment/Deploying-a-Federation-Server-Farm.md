---
layout: Conceptual
title: Deploying a Federation Server Farm for Windows Server 2012 R2 AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/deploying-a-federation-server-farm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Deploying a Federation Server Farm'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: checklist
locale: en-us
document_id: 99395519-3960-edd7-2979-d1fe64dc59dd
document_version_independent_id: 8a4793fc-cd3c-d412-ecfc-d51b6e18b33e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Deploying-a-Federation-Server-Farm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/deploying-a-federation-server-farm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Deploying-a-Federation-Server-Farm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 833906ed-8964-0da7-3ede-ef3c1833bad6
---

# Deploying a Federation Server Farm for Windows Server 2012 R2 AD FS | Microsoft Learn

In order to deploy a federation server farm, complete the tasks in this checklist in order. When a reference link takes you to a conceptual topic, return to this checklist after you review the conceptual topic so that you can proceed with the remaining tasks in this checklist.

![Icon for the Deploying a Federation Server Farm check list.](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**Checklist: Deploying a Federation Server Farm**

| Task | Reference |
| --- | --- |
| Review important concepts and considerations as you prepare to deploy Active Directory Federation Services (AD FS). | ![Icon for the AD FS Design Guide in Windows Server 2012 R2 link you can use in reference to deploying a federation server farm.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[AD FS Design Guide in Windows Server 2012 R2](../design/ad-fs-design-guide-in-windows-server-2012-r2)<br>![Icon for the Understanding Key AD FS Concepts link you can use in reference to deploying a federation server farm.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Understanding Key AD FS Concepts](../technical-reference/understanding-key-ad-fs-concepts) |
|  | **Note:** If you decide to use Microsoft SQL Server for your AD FS configuration store, ensure to deploy a functional instance of [SQL Server](/en-us/sql/sql-server/)<br>**Warning:** In Windows Server 2012 R2, if you want to create an AD FS farm and use SQL Server to store your configuration data, you can use SQL Server 2008 and newer versions, including SQL Server 2012. |
| Join your computer to an Active Directory domain. | ![Icon for the Join a Computer to a Domain link you can use in reference to deploying a federation server farm.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Join a Computer to a Domain](../../ad-ds/manage/join-computer-to-domain) |
| Enroll a Secure Socket Layer (SSL) certificate for AD FS. | ![Icon for the Enroll an SSL Certificate for AD FS link you can use in reference to deploying a federation server farm.](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Enroll an SSL Certificate for AD FS](enroll-an-ssl-certificate-for-ad-fs) |
| Install the AD FS role service. | ![Icon for the Install the AD FS Role Service link you can use in reference to deploying a federation server farm.](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Install the AD FS Role Service](install-the-ad-fs-role-service) |
| Configure a federation server. | ![Icon for the Configure a Federation Server link you can use in reference to deploying a federation server farm.](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Configure a Federation Server](configure-a-federation-server) |
| Optional step: Configure a federation server with Device Registration Service (DRS). | ![Icon for the Configure a federation server with Device Registration Service link you can use in reference to deploying a federation server farm.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Configure a federation server with Device Registration Service](configure-a-federation-server-with-device-registration-service) |
| Add a host (A) and alias (CNAME) resource record to corporate Domain Name System (DNS) for the federation service and DRS. | ![Icon for the Configure Corporate DNS for the Federation Service and DRS link you can use in reference to deploying a federation server farm.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Configure Corporate DNS for the Federation Service and DRS](configure-corporate-dns-for-the-federation-service-and-drs) |
| Verify that a federation server is operational. | ![deploying federated server farm](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Verify That a Federation Server Is Operational](verify-that-a-federation-server-is-operational) |