---
layout: Conceptual
title: Deploy Hosted Cache Servers (Optional) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/deploy-hosted-cache-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to install and configure BranchCache hosted cache servers that are located in branch offices where you want to deploy BranchCache hosted cache mode.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 3b6236e1-681b-20bf-dffb-565e7e447103
document_version_independent_id: f0858f74-8445-b2aa-2033-f25ec35d2fb4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/deploy-hosted-cache-servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/deploy-hosted-cache-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/deploy-hosted-cache-servers.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4befe3d6-f3b5-10d2-6795-85790f58eb07
---

# Deploy Hosted Cache Servers (Optional) | Microsoft Learn

You can use this procedure to install and configure BranchCache hosted cache servers that are located in branch offices where you want to deploy BranchCache hosted cache mode. With BranchCache in Windows Server 2016, you can deploy multiple hosted cache servers in one branch office.

Important

This step is optional because distributed cache mode does not require a hosted cache server computer in branch offices. If you are not planning on deploying hosted cache mode in any branch offices, you do not need to deploy a hosted cache server, and you do not need to perform the steps in this procedure.

You must be a member of **Administrators**, or equivalent to perform this procedure.

### To install and configure a hosted cache server

1. On the computer that you want to configure as a hosted cache server, run the following command at a Windows PowerShell prompt to install the BranchCache feature.

    `Install-WindowsFeature BranchCache -IncludeManagementTools`
2. Configure the computer as a hosted cache server by using one of the following commands:

    - To configure a non-domain joined computer as a hosted cache server, type the following command at the Windows PowerShell prompt, and then press ENTER.

        `Enable-BCHostedServer`
    - To configure a domain joined computer as a hosted cache server, and to register a service connection point in Active Directory for automatic hosted cache server discovery by client computers, type the following command at the Windows PowerShell prompt, and then press ENTER.

        `Enable-BCHostedServer -RegisterSCP`
3. To verify the correct configuration of the hosted cache server, type the following command at the Windows PowerShell prompt, and then press ENTER.

    `Get-BCStatus`

    Note

    After you run this command, in the section **HostedCacheServerConfiguration**, the value for **HostedCacheServerIsEnabled** is **True**. If you configured a domain joined hosted cache server to register a service connection point (SCP) in Active Directory, the value for **HostedCacheScpRegistrationEnabled** is **True**.