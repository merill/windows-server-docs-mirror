---
layout: Conceptual
title: BranchCache Hosted Cache Mode Deployment Planning | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/bc-hcm/3-bc-hcm-plan
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to plan your deployment of BranchCache in Hosted Cache mode.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 5ae68b99-74f7-e163-c505-d5bc5f95af65
document_version_independent_id: 8bf9e47d-7064-e88c-3db9-4603f20f383c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/3-Bc-Hcm-Plan.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/bc-hcm/3-bc-hcm-plan
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/3-Bc-Hcm-Plan.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: ee7ca7ab-c5b3-edc7-e628-41901e59a5e2
---

# BranchCache Hosted Cache Mode Deployment Planning | Microsoft Learn

You can use this topic to plan your deployment of BranchCache in Hosted Cache mode.

Important

Your hosted cache server must be running Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012.

Before you deploy your hosted cache server, you must plan the following items:

- Plan basic server configuration
- Plan domain access
- Plan the location and size of the hosted cache
- Plan the share to which the content server packages are to be copied
- Plan prehashing and data package creation on content servers

## Plan basic server configuration

If you are planning on using an existing server in your branch office as your hosted cache server, you do not need to perform this planning step, because the computer is already named and has an IP address configuration.

After you install Windows Server 2016 on your hosted cache server, you must rename the computer and assign and configure a static IP address for the local computer.

Note

In this guide, the hosted cache server is named HCS1, however you should use a server name that is appropriate for your deployment.

## Plan domain access

If you are planning on using an existing server in your branch office as your hosted cache server, you do not need to perform this planning step, unless the computer is not currently joined to the domain.

To log on to the domain, the computer must be a domain member computer and the user account must be created in AD DS before the logon attempt. In addition, you must join the computer to the domain with an account that has the appropriate group membership.

## Plan the location and size of the hosted cache

On HCS1, determine where on your hosted cache server you want to locate the hosted cache. For example, decide the hard disk, volume, and folder location where you plan to store the cache.

In addition, decide what percentage of disk space you want to allocate for the hosted cache.

## Plan the share to which the content server packages are to be copied

After you create data packages on your content servers, you must copy them over the network to a share on your hosted cache server.

Plan the folder location and sharing permissions for the shared folder. In addition, if your content servers host a large amount of data and the packages that you create will be large files, plan to perform the copy operation during off\–peak hours so that WAN bandwidth is not consumed by the copy operation during a time when others need to use the bandwidth for normal business operations.

## Plan prehashing and data package creation on content servers

Before you prehash content on your content servers, you must identify the folders and files that contain content that you want to add to the data package.

In addition, you must plan on the local folder location where you can store the data packages before copying them to the hosted cache server.

To continue with this guide, see [BranchCache Hosted Cache Mode Deployment](4-bc-hcm-deployment).