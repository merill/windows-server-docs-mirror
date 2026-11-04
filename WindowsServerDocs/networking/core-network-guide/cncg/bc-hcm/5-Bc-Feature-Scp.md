---
layout: Conceptual
title: Install the BranchCache Feature and Configure the Hosted Cache Server by Service Connection Point | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/bc-hcm/5-bc-feature-scp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to install the BranchCache feature on your hosted cache server, HCS1, and to configure the server to register an SCP in AD DS.
ms.topic: install-set-up-deploy
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 7fe6b080-fc56-e2a6-eb13-9661f26ba97e
document_version_independent_id: 74eb6cae-94fc-1f2e-5556-bb58d5a65597
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/5-Bc-Feature-Scp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/bc-hcm/5-bc-feature-scp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/5-Bc-Feature-Scp.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b4891645-060e-2741-47e3-ddbdcf57d976
---

# Install the BranchCache Feature and Configure the Hosted Cache Server by Service Connection Point | Microsoft Learn

You can use this procedure to install the BranchCache feature on your hosted cache server, HCS1, and to configure the server to register a Service Connection Point (SCP) in Active Directory Domain Services (AD DS).

When you register hosted cache servers with an SCP in AD DS, the SCP allows client computers that are configured correctly to automatically discover hosted cache servers by querying AD DS for the SCP. Instructions on how to configure client computers to perform this action are provided later in this guide.

Important

Before you perform this procedure, you must join the computer to the domain and configure the computer with a static IP address.

To perform this procedure, you must be a member of the Administrators group.

## To install the BranchCache feature and configure the hosted cache server

1. On the server computer, run Windows PowerShell as an Administrator. Type the following command, and then press ENTER.

    ```
    Install-WindowsFeature BranchCache
    ```
2. To configure the computer as a hosted cache server after the BranchCache feature is installed, and to register a Service Connection Point in AD DS, type the following command in Windows PowerShell, and then press ENTER.

    ```
    Enable-BCHostedServer -RegisterSCP
    ```
3. To verify the hosted cache server configuration, type the following command and press ENTER.

    ```
    Get-BCStatus
    ```

    The results of the command display status for all aspects of your BranchCache installation. Following are a few of the BranchCache settings and the correct value for each item:

    - BranchCacheIsEnabled: True
    - HostedCacheServerIsEnabled: True
    - HostedCacheScpRegistrationEnabled: True
4. To prepare for the step of copying your data packages from your content servers to your hosted cache servers, either identify an existing share on the hosted cache server or create a new folder and share the folder so that it is accessible from your content servers. After you create your data packages on your content servers, you will copy the data packages to this shared folder on the hosted cache server.
5. If you are deploying more than one hosted cache server, repeat this procedure on each server.

To continue with this guide, see [Move and Resize the Hosted Cache (Optional)](6-bc-move-resize-cache).