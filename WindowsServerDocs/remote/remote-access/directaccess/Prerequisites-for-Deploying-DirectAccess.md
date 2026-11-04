---
layout: Conceptual
title: Prerequisites for Deploying DirectAccess | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/prerequisites-for-deploying-directaccess
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: This topic provides prerequisites for DirectAccess deployment in Windows Server 2016.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 657813ba-823c-74f9-69af-3adedeffabf8
document_version_independent_id: 6bb46442-fc7f-84fc-d5da-da7691c67836
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/Prerequisites-for-Deploying-DirectAccess.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/prerequisites-for-deploying-directaccess
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/Prerequisites-for-Deploying-DirectAccess.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: dad64158-2055-67b2-5792-b6ae046be9d1
---

# Prerequisites for Deploying DirectAccess | Microsoft Learn

The following table lists the prerequisites necessary for using the configuration wizards to deploy DirectAccess.

| Scenario | Prerequisites |
| --- | --- |
| [Deploy a Single DirectAccess Server Using the Getting Started Wizard](single-server-wizard/deploy-a-single-directaccess-server-using-the-getting-started-wizard) | - Windows Firewall must be enabled on all profiles<br>- Only supported for clients running Windows 10®,  Windows® 8, and Windows® 8.1 Enterprise.<br><br>- A public key infrastructure is not required.<br><br>- Not supported for deploying two-factor authentication. Domain credentials are required for authentication.<br><br>- Automatically deploys DirectAccess to all mobile computers in the current domain.<br><br>- Traffic to the Internet does not go through DirectAccess. Force tunnel configuration is not supported.<br><br>- DirectAccess server is the network location server.<br><br>- Network Access Protection (NAP) is not supported.<br><br>- Changing policies by using a feature other than the DirectAccess management console or Windows PowerShell cmdlets is not supported.<br><br>- For a multisite configuration, now or in the future, first follow the guidance in [Deploy a Single DirectAccess Server with Advanced Settings](single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings). |
| [Deploy a Single DirectAccess Server with Advanced Settings](single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings) | - A public key infrastructure must be deployed. For more information, see [Test Lab Guide Mini-Module: Basic PKI for Windows Server 2012](/en-us/answers/topics/windows-server-2012.html).<br>- Windows Firewall must be enabled on all profiles.<br><br>The following server operating systems support DirectAccess.<br><br>- You can deploy all versions of Windows Server 2016 as a DirectAccess client or a DirectAccess server.- You can deploy all versions of Windows Server 2012 R2 as a DirectAccess client or a DirectAccess server.- You can deploy all versions of Windows Server 2012 as a DirectAccess client or a DirectAccess server.- You can deploy all versions of Windows Server 2008 R2 as a DirectAccess client or a DirectAccess server.<br><br>The following client operating systems support DirectAccess.<br><br>- Windows 10® Enterprise- Windows 10® Enterprise 2015 Long Term Servicing Branch (LTSB)- Windows® 8 and 8.1 Enterprise- Windows® 7 Ultimate- Windows® 7 Enterprise<br><br>- Force tunnel configuration is not supported with KerbProxy authentication.<br><br>- Changing policies by using a feature other than the DirectAccess management console or Windows PowerShell cmdlets is not supported.<br><br>- Separating NAT64/DNS64 and IPHTTPS server roles on another server is not supported. |