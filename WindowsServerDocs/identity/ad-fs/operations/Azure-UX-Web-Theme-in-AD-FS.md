---
layout: Conceptual
title: Microsoft Entra UX Web Theme in AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/azure-ux-web-theme-in-ad-fs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: The following document describes how to change the AD FS forms sign-in so that it resembles the Microsoft Entra user experience.
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: 70c4d861-ff1f-b60d-adf5-b0ec787ff613
document_version_independent_id: aa1c46d6-eef6-c20a-13b7-10e7ffe8786d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Azure-UX-Web-Theme-in-AD-FS.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/azure-ux-web-theme-in-ad-fs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Azure-UX-Web-Theme-in-AD-FS.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: a1717a02-8cef-47e2-03f4-8ec0fee10c77
---

# Microsoft Entra UX Web Theme in AD FS | Microsoft Learn

The AD FS forms sign in currently does not mirror the Azure/O365 sign-in experience. To provide a more uniform and seamless experience for end-users, we have released the follow cascading style sheet web theme which can be applied to your AD FS servers. Currently, the forms sign-in for AD FS on Windows Server 2016 looks like following:

![Current sign-in](media/azure-ux-web-theme-in-ad-fs/one.png)

With the new style sheet, the user experience will look more like the Azure and Office 365 sign-in experiences.

## Download the CSS style sheet

You can download the web theme from the following Github [location](https://github.com/Microsoft/adfsWebCustomization/tree/master/centeredUi).

## Enabling the new web theme

To enable the new web theme use the following procedure:

### To enable the new Microsoft Entra UX web theme in AD FS

1. Start PowerShell as an Administrator
2. Create a new web theme using PowerShell: `New-AdfsWebTheme –Name custom –StyleSheet @{path="c:\NewTheme.css"}`
3. Set the new theme as the active theme using PowerShell: `Set-AdfsWebConfig -ActiveThemeName custom`![PowerShell](media/azure-ux-web-theme-in-ad-fs/two.png)
4. Test the sign-in by going to https://&lt;AD FS name.domain&gt;/adfs/ls/idpinitiatedsignon.htm ![Sign-on](media/azure-ux-web-theme-in-ad-fs/three.png)

> 
> ![NOTE] You need to ensure that idpinitiatedsignon has been enabled. It is not enabled by default. To enable idpinitiatedsignon use the following PowerShell command: `Set-AdfsProperties –EnableIdpInitiatedSignonPage $True`

## Image Recommendations

Enabling the centered UI enables you to use the same images for background and logo that you might already have for Microsoft Entra company branding. Generally, the same recommendations for size, ratio, and format do apply.

### Logo

| Description | Constraints | Recommendations |
| --- | --- | --- |
| The logo is displayed on top of the login panel. | Transparent JPG or PNGMax height: 36 pxMax width: 245 px | Use your organization's logo here.Use a transparent image. Don't assume that the background will be white.Do not add padding around your logo in the image or your logo will look disproportionately small. |

### Background

| Description | Constraints | Recommendations |
| --- | --- | --- |
| This option appears in the background of the sign-in page, is anchored to the center of the viewable space, and scales and crops to fill the browser window. On narrow screens such as mobile phones, this image is not shown.A black mask with 0.55 opacity is applied over this image when the page is loaded. | JPG or PNGImage dimensions: 1920x1080 pxFile size: &lt; 300 KB | Use images where there isn't a strong subject focus. The opaque sign-in form appears over the center of this image and can cover any part of the image, depending on the size of the browser window.Keep the file size small to ensure quick load times. |