---
layout: Conceptual
title: Custom Web Themes in AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/custom-web-themes-in-ad-fs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Custom Web Themes in AD FS'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: ee84f4dc-1312-ae51-e1db-4575bb2b80e9
document_version_independent_id: f726ca8b-bbc3-47ab-54d9-94a298efe616
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Custom-Web-Themes-in-AD-FS.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/custom-web-themes-in-ad-fs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Custom-Web-Themes-in-AD-FS.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: df17fe37-6176-cad5-ca62-563e929d3521
---

# Custom Web Themes in AD FS | Microsoft Learn

The theme that is shipped out-of-the-box is called Default. You can export the default theme and use it so that you can start quickly. You can customize the appearance and behavior, which includes the layout by modifying the .css file, import and apply this new theme, and then you can use the customized appearance and behavior. Using the .css file also makes it easier to work with your web designers.

The following cmdlet creates a custom web theme, which duplicates the default web theme.

```powershell
New-AdfsWebTheme –Name custom –SourceName default
```

You can modify the .css file and configure the new web theme by using the new .css file. To export a web theme, use the following cmdlet.

```powershell
Export-AdfsWebTheme –Name default –DirectoryPath c:\theme
```

To apply the .css file to the new theme, use the following cmdlet.

```powershell
Set-AdfsWebTheme –TargetName custom –StyleSheet @{path="c:\NewTheme.css"}
```

The following cmdlet creates a custom web theme from a new style sheet.

```powershell
New-AdfsWebTheme –Name custom –StyleSheet @{path="c:\NewTheme.css"} –RTLStyleSheetPath c:\NewRtlTheme.css
```

To apply the custom web theme to AD FS, use the following cmdlet.

```powershell
Set-AdfsWebConfig -ActiveThemeName custom
```

To add JavaScript to AD FS, use the following cmdlet.

```powershell
Set-AdfsWebTheme -TargetName custom -AdditionalFileResource @{Uri=' /adfs/portal/script/onload.js';path="D:\inetpub\adfsassets\script\onload.js"}
```

## Additional references

[AD FS User Sign-in Customization](ad-fs-user-sign-in-customization)