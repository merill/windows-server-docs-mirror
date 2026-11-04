---
layout: Conceptual
title: Change the  company name on the AD FS sign-in page | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/change-the-company-name-on-the-ad-fs-sign-in-page
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Change the company name on the AD FS sign-in page'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 470b97b0-90cb-65dc-9780-4de2a1aabf8f
document_version_independent_id: 0bfa604a-30da-acb6-7fd7-a8d6f76eaf80
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Change-the-company-name-on-the-AD-FS-sign-in-page.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/change-the-company-name-on-the-ad-fs-sign-in-page
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Change-the-company-name-on-the-AD-FS-sign-in-page.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3fbcaec8-dbf7-0f79-7c05-4554709a0524
---

# Change the  company name on the AD FS sign-in page | Microsoft Learn

To change the name of the company that is displayed on the sign-in page, use the following Windows PowerShell cmdlet and syntax. This value is set by default by using the value from the Federation Service display name that you entered during setup.

![change name](media/ad-fs-user-sign-in-customization/adfs_blue_custom1.png)

```powershell
    Set-AdfsGlobalWebContent –CompanyName "Contoso Corp"
```

Note

You can also use the Windows PowerShell Integrated Scripting Environment (ISE) to change the company name. By using the Windows PowerShell ISE, you can display content in a Unicode-compliant environment. For additional information, see [Introducing the Windows PowerShell ISE](/en-us/previous-versions/mt707506%28v=msdn.10%29).

## Additional references

- [AD FS User Sign-in Customization](ad-fs-user-sign-in-customization)