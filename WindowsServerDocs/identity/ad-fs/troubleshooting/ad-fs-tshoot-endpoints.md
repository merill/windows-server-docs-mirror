---
layout: Conceptual
title: AD FS Troubleshooting - AD FS Endpoints | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-endpoints
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: This article describes how to troubleshoot Active Directory Federation Services (AD FS) endpoints.
ms.date: 2024-10-14T00:00:00.0000000Z
ms.topic: troubleshooting-general
ms.custom: sfi-image-nochange
locale: en-us
document_id: 3fe35141-ee0d-2d3b-b805-939299ce3f4b
document_version_independent_id: 485e45ed-a5db-2a5b-f643-c7a20897a98c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-endpoints.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/troubleshooting/ad-fs-tshoot-endpoints
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-endpoints.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 27ca05b2-b168-82ae-56f3-7bbe4eb0f299
---

# AD FS Troubleshooting - AD FS Endpoints | Microsoft Learn

Endpoints provide access to the federation server functionality of Active Directory Federation Services (AD FS), such as publishing federation metadata. To verify that the AD FS server is responding to web requests, you can check the various endpoints.

## Federation metadata test

Passive federation refers to scenarios where your browser is redirected to the AD FS sign-in page. By testing the metadata endpoint, you can determine if the AD FS server is responding to web requests in these passive scenarios. Use the following procedure to test the endpoint.

1. Use a web browser to go to your AD FS federation metadata endpoint. An example is `https://sts.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`. The .xml file downloads locally to your machine.
2. Open the .xml file and verify that it contains information similar to the following image.

    ![Screenshot that shows a passive scenario.](media/ad-fs-tshoot-endpoints/meta2.png)

## WS-MEX test (active test)

WS-MetaDataExchange is a web services protocol and is part of the WS-Federation roadmap. It uses a SOAP message to request metadata. By testing the endpoint, you can determine if the AD FS server is responding to web requests for WS-MetaDataExchange.

To test the endpoint, use a web browser to go to your AD FS federation metadata endpoint. An example is `https://sts.contoso.com/adfs/services/trust/mex`. The .xml file automatically appears in the browser and should look like the following image.

![Screenshot that shows the AD FS federation metadata endpoint .xml file.](media/ad-fs-tshoot-endpoints/security-trust-file.png)