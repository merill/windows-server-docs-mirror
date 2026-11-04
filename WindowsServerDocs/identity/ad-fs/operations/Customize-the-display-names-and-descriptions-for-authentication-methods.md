---
layout: Conceptual
title: Customize the display names and descriptions for authentication methods | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/customize-the-display-names-and-descriptions-for-authentication-methods
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Customize the display names and descriptions for authentication methods'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: 369d09c6-f1fb-89bf-4b08-37874a66b5dc
document_version_independent_id: b5328555-17c9-2196-03db-85593d0ffd5c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Customize-the-display-names-and-descriptions-for-authentication-methods.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/customize-the-display-names-and-descriptions-for-authentication-methods
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Customize-the-display-names-and-descriptions-for-authentication-methods.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f925701f-3e80-cb6d-8310-9ad7adc2b3c6
---

# Customize the display names and descriptions for authentication methods | Microsoft Learn

To customize the display names and descriptions for authentication methods you can use the `Set-AdfsAuthenticationProviderWebContent` PowerShell cmdlet. In order to use this cmdlet, you must first obtain the name of the authentication method you wish to customize. This can be done using `Get-AdfsGlobalAuthenticationPolicy`. In the example below we see that, on our sign-in page, the following is displayed: "Sign in using an X.509 certificate". We want to simplify this for our users.

![customize displayname](media/ad-fs-user-sign-in-customization/adfs_customize_update1.png)

So first we get the name of the authentication method and then we edit the displayed text.

```powershell
Get-AdfsGlobalAuthenticationPolicy

AdditionalAuthenticationProvider  : {}
DeviceAuthenticationEnabled   : False
PrimaryIntranetAuthenticationProvider : {FormsAuthentication, CertificateAuthentication}
PrimaryExtranetAuthenticationProvider : {FormsAuthentication, CertificateAuthentication}
WindowsIntegratedFallbackEnabled  : True

Set-AdfsAuthenticationProviderWebContent -Name CertificateAuthentication -DisplayName "Sign in with a certificate"
```

![Screenshot that shows how to get the name of the authentication method and edit the displayed text.](media/ad-fs-user-sign-in-customization/adfs_customize_update2.png)

Now we see that our display message has changed.

![Screenshot that shows that the display message has changed.](media/ad-fs-user-sign-in-customization/adfs_customize_update3.png)

## Additional references

[AD FS User Sign-in Customization](ad-fs-user-sign-in-customization)