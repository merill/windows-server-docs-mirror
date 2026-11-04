---
layout: Conceptual
title: Change the illustration on the AD FS sign-in page | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/change-the-illustration-on-the-ad-fs-sign-in-page
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Change the illustration on the AD FS sign-in page'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 879cdd90-da4c-fa30-49e0-2ddfccf74e03
document_version_independent_id: e2ac76f5-2ee5-147d-79b0-0834ee8076fd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Change-the-illustration-on-the-AD-FS-sign-in-page.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/change-the-illustration-on-the-ad-fs-sign-in-page
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Change-the-illustration-on-the-AD-FS-sign-in-page.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 86e8f0cf-4346-01ad-f2bf-5b816ff980d9
---

# Change the illustration on the AD FS sign-in page | Microsoft Learn

To change the illustration, the graphic on the left, which is displayed on the sign-in page, use the following Windows PowerShell cmdlet and syntax.

![change illustration](media/ad-fs-user-sign-in-customization/adfs_blue_custom2.png)

Important

We recommend the dimensions for the illustration to be 1420x1080 pixels @ 96 DPI for displays with 1080p resolution in **jpg** or **png** format. A file size of no greater than 200 KB to 500 KB to improve load times.

```powershell
Set-AdfsWebTheme -TargetName default -Illustration @{path="c:\Contoso\illustration.png"}
```

## Additional references

[AD FS User Sign-in Customization](ad-fs-user-sign-in-customization)