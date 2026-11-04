---
layout: Conceptual
title: Changing the company logo on the AD FS sign-in page | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/change-the-company-logo-on-the-ad-fs-sign-in-page
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Changing the company logo on the AD FS sign-in page'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: cb606be2-82cd-d2f8-37b6-01d0f9ba039c
document_version_independent_id: b6eb4b5d-7188-cf4d-8c10-1fbc00ad09f2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Change-the-company-logo-on-the-AD-FS-sign-in-page.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/change-the-company-logo-on-the-ad-fs-sign-in-page
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Change-the-company-logo-on-the-AD-FS-sign-in-page.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 21b31de4-d548-847f-2449-7b811d69f08c
---

# Changing the company logo on the AD FS sign-in page | Microsoft Learn

## Change company logo

To change the logo of the company that is displayed on the sign-in page, use the following PowerShell Windows PowerShell cmdlet and syntax.

![change logo](media/ad-fs-user-sign-in-customization/adfs_blue_custom2.png)

Important

We recommend the dimensions for the logo to be 260x35 @ 96 dpi with a file size of no greater than 10 KB.

```powershell
Set-AdfsWebTheme -TargetName default -Logo @{path="c:\Contoso\logo.png"}
```

Note

The `TargetName` parameter is required. The default theme that is released with AD FS is named *default*.

## Additional references

[AD FS User Sign-in Customization](ad-fs-user-sign-in-customization)