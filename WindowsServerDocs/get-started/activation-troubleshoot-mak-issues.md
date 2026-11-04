---
layout: Conceptual
title: MAK activation known issues | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/activation-troubleshoot-mak-issues
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: Describes common issues that may occur during the MAK activation process, and provides resolutions and guidance
ms.topic: troubleshooting
ms.date: 2019-10-03T00:00:00.0000000Z
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 00a58e17-2218-f46c-218d-56be66a77d90
document_version_independent_id: 99a3b009-9c5f-1b8e-f367-02fa7f476bb3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/activation-troubleshoot-mak-issues.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/activation-troubleshoot-mak-issues
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/activation-troubleshoot-mak-issues.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 83f045c7-ad4e-b52a-b30a-8d4f656500cb
---

# MAK activation known issues | Microsoft Learn

[**Try our Virtual Agent**](https://vsa.services.microsoft.com/v1.0/?partnerId=7d74cf73-5217-4008-833f-87a1a278f2cb&amp;flowId=DMC&amp;initialQuery=31806237) - It can help you quickly identify and fix common issues related to KMS and MAK activation

This article describes common issues that can occur during Multiple Activation Key (MAK) activations, and provides guidance for addressing those issues.

## How can I tell whether my computer is activated?

On the computer, open the **System** control panel and look for **Windows is activated**. Alternatively, run Slmgr.vbs and use the **/dli** command-line option.

## The computer does not activate over the internet

Make sure that the required ports are open in the firewall. For a list of ports, see the [Volume Activation Deployment Guide](/en-us/previous-versions/tn-archive/dd772269%28v=technet.10%29).

## Internet and telephone activation fail

Contact a local Microsoft Activation Center. For the telephone numbers of Microsoft Activation Centers worldwide, go to [Microsoft Licensing Activation Centers worldwide telephone numbers](https://www.microsoft.com/Licensing/existing-customer/activation-centers). Make sure to provide the Volume License agreement information and proof of purchase when you call.

## Slmgr.vbs /ato returns an error code

If Slmgr.vbs returns a hexadecimal error code, determine the corresponding error message by running the following script:

```cmd
slui.exe 0x2a 0x <ErrorCode>
```

For more information about specific error codes and how to address them, see [Resolving common activation error codes](activation-error-codes).