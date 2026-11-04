---
layout: Conceptual
title: AD FS Customization in Windows Server 2016 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/ad-fs-customization-in-windows-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: AD FS Customization in Windows Server 2016'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 09f57cb3-3b20-d4e4-d757-f7fe08995122
document_version_independent_id: f8edbb70-12b7-e456-0b88-f069d1064f40
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/ad-fs-customization-in-windows-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/ad-fs-customization-in-windows-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/ad-fs-customization-in-windows-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: db51ac37-055e-43fb-d677-86dad946b6ca
---

# AD FS Customization in Windows Server 2016 | Microsoft Learn

In response to feedback from organizations using AD FS, we have added additional tools to customize the user sign in experience for individual applications protected by AD FS. In addition to specifying per-application web content such as description text and links, now you can specify entire web themes per application. This includes logo, illustration, style sheets, or an entire onload.js file.

## Global Settings

For general global settings you can refer to [Customizing the AD FS Sign-in Pages](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn280950%28v=ws.11%29) that shipped with AD FS in Windows Server 2012 R2.

## Pre-requisites

The following pre-requisites are required before attempting the procedures outlined in this document.

- AD FS in Windows Server 2016 TP4 or later

## Configure AD FS Relying parties

Per relying party sign-in web elements and themes can be configured using the PowerShell examples below:

### Customize messages

```
PS C:\>Set-AdfsRelyingPartyWebContent
    -TargetRelyingPartyName "<RP trust Name>"
    -CompanyName "This text appears in place of the federation service display name"
    -OrganizationalNameDescriptionText "This text appears right below the company name"
    -SignInPageDescription "This text appears below the credential prompt"
```

### Customize company name, logo, and image

```
PS C:\>Set-AdfsRelyingPartyWebTheme
    -TargetRelyingPartyName "<RP trust Name>"
    -Logo @{path="C:\Images\applogo.png"}
    -Illustration @{path="C:\Images\appillustration.jpg"}
```

### Customize entire page

```
PS C:\>Set-AdfsRelyingPartyWebTheme
    -TargetRelyingPartyName "<RP trust Name>"
    -OnLoadScriptPath @{path="c:\scripts\adfstheme\onload.js"}
```

## Custom themes and advanced custom themes

For custom themes refer to [Customizing the AD FS Sign-in Pages](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn280950%28v=ws.11%29) and [Advanced Customization of AD FS Sign-in Pages.](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn636121%28v=ws.11%29)

## Assigning custom web themes per RP

To assign a custom theme per RP use the following procedure:

1. Create a new theme as a copy for the default, global theme in AD FS `New-AdfsWebTheme -Name AppSpecificTheme -SourceName default`
2. Export the theme for customization `Export-AdfsWebTheme -Name AppSpecificTheme -DirectoryPath c:\appspecifictheme`
3. Customize theme files (images, css, onload.js) - in your favorite editor or replace the file
4. Import customized files from the file system to AD FS (targeting the new theme) `Set-AdfsWebTheme -TargetName AppSpecificTheme -AdditionalFileResource @{Uri='/adfs/portal/script/onload.js';Path="c:\appspecifictheme\script\onload.js"}`
5. Apply the new, customized theme to the specific RP (or RP's) `Set-AdfsRelyingPartyWebTheme -TargetRelyingPartyName urn:app1 -SourceWebThemeName AppSpecificTheme`

## Home Realm Discovery

For home realm discovery customization see [Customizing the AD FS Sign-in Pages](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn280950%28v=ws.11%29).

## Updated password page

For information on customizing the update password page see [Customizing the AD FS Sign-in Pages](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn280950%28v=ws.11%29).

## Customizing and Alternate IDs

Users can sign in to Active Directory Federation Services (AD FS)-enabled applications using any form of user identifier that is accepted by Active Directory Domain Services (AD DS). These include User Principal Names (UPNs) (johndoe@contoso.com) or domain qualified sam-account names (contoso\johndoe or contoso.com\johndoe). For more information on this see [Configuring Alternate Login ID.](configuring-alternate-login-id)

You may additionally want to customize the AD FS sign-in page to give end users some hint about the alternate login ID. You can do it by adding the customized sign-in page description for more information see [Customizing the AD FS Sign-in Pages.](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn280950%28v=ws.11%29)

You can also do this by customizing "Sign in with organizational account" string above username field. For information on this see [Advanced Customization of AD FS Sign-in Pages](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn636121%28v=ws.11%29).

## Additional references

[AD FS User Sign-in Customization](ad-fs-user-sign-in-customization)