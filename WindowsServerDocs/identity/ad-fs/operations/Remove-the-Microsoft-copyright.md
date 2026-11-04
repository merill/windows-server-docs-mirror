---
layout: Conceptual
title: Remove the Microsoft copyright | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/remove-the-microsoft-copyright
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Remove the Microsoft copyright'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 09157f4e-7eb7-ea80-7bdd-9b48cffef1a7
document_version_independent_id: 6fdf1ab5-ef30-2d25-a36b-61ca7319f2ab
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Remove-the-Microsoft-copyright.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/remove-the-microsoft-copyright
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Remove-the-Microsoft-copyright.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: c2551566-1b21-273b-be8e-0f2209dbf057
---

# Remove the Microsoft copyright | Microsoft Learn

By default, the AD FS pages contain the Microsoft copyright. To remove this copyright from your customized pages, you can use the following procedure.

![Screenshot that shows the login page for with the copyright at the bottom.](media/ad-fs-user-sign-in-customization/adfs_blue_custom1.png)

## To remove the Microsoft copyright

1. Create a custom theme that is based on the default.

    ```powershell
    New-AdfsWebTheme –Name custom –SourceName default
    ```
2. Export the theme by specifying the output folder.

    ```powershell
    Export-AdfsWebTheme -Name custom -DirectoryPath C:\CustomWebTheme
    ```
3. Locate the `Style.css` file that is located in the output folder. By using the previous example, the path would be `C:\CustomWebTheme\Css\Style.css.`
4. Open the `Style.css` file with an editor, such as Notepad.
5. Locate the `#copyright` portion, and then change it to the following:

    ```css
    #copyright {color:#696969; display:none;}
    ```
6. Create a custom theme that is based on the new `Style.css` file.

    ```powershell
    Set-AdfsWebTheme -TargetName custom -StyleSheet @{locale="";path="C:\customWebTheme\css\style.css"}
    ```
7. Activate the new theme.

    ```powershell
    Set-AdfsWebConfig -ActiveThemeName custom
    ```

Now, you should no longer see the copyright at the bottom of the sign-in page.

![remove copyright](media/ad-fs-user-sign-in-customization/adfs_blue_custom1a.png)

## Additional references

[AD FS User Sign-in Customization](ad-fs-user-sign-in-customization)