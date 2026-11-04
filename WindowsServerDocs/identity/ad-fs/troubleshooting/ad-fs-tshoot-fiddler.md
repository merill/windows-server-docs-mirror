---
layout: Conceptual
title: AD FS Troubleshooting - Fiddler | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-fiddler
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: This document introduces the Fiddler tool, including guidance on installing and configuring Fiddler to troubleshoot AD FS claims issues
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: troubleshooting-general
ms.custom: sfi-image-nochange
locale: en-us
document_id: 5df85f2e-0c9f-91d3-0e29-b9465ad91448
document_version_independent_id: 9531dfcd-61b8-3601-4d5d-e26813f0eeaa
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-fiddler.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/troubleshooting/ad-fs-tshoot-fiddler
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-fiddler.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 2a5d4553-3a06-2688-a8d2-e3505398db50
---

# AD FS Troubleshooting - Fiddler | Microsoft Learn

Fiddler is a tool that can be used to capture HTTP/HTTPS web traffic. Fiddler can be used to assist in troubleshooting the claim issuance process. Capturing and examining HTTP/HTTPS web traffic can help you get a better understanding of where an interaction is breaking down. This article describes how to install and set up Fiddler to capture AD FS traffic. For an example Fiddler trace using WS-Federation, see [AD FS Troubleshooting - Fiddler - WS-Federation](ad-fs-tshoot-fiddler-ws-fed)

## Download and install Fiddler

See [Fiddler download](https://www.telerik.com/download/fiddler) to download the Fiddler tool. After you have downloaded Fiddler, proceed with installing it.

## Configure Fiddler to capture AD FS traffic

In order to capture AD FS traffic, you need to configure Fiddler to decrypt SSL traffic.

### Configure the Fiddler SSL certificate

Use the following procedure to setup Fiddler to decrypt SSL traffic.

1. Open Fiddler
2. At the top, under **Tools**, select **Fiddler Options**.
3. Select the HTTPS tab.
4. Place a check in **Decrypt HTTPS traffic** and select **from browsers only** from the drop-down.
5. Place a check in **Ignore server certificate errors**.
6. Select **OK**.

![Fiddler](media/ad-fs-tshoot-fiddler/fiddler1.png)

## Related links

- [AD FS Troubleshooting](ad-fs-tshoot-overview)