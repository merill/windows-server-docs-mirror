---
layout: Conceptual
title: Custom error messages for AD FS sign-in page | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/custom-error-messages-for-ad-fs-sign-in-page
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Custom error messages for AD FS sign-in page'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 56e5724f-81e4-2707-c287-371cf103c7c1
document_version_independent_id: 0c5fcd5c-74d9-aee7-593b-8465252f54c9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Custom-error-messages-for-AD-FS-sign-in-page.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/custom-error-messages-for-ad-fs-sign-in-page
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Custom-error-messages-for-AD-FS-sign-in-page.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: c514ca21-e7ee-95f5-e466-f8770255b66f
---

# Custom error messages for AD FS sign-in page | Microsoft Learn

You can configure custom error messages that can be tailored to your organization. The following illustration shows a customized error page description and a generic error message. Use the following Windows PowerShell cmdlets to customize your error messages.

![custom error](media/ad-fs-user-sign-in-customization/adfs_blue_custom3.png)

## Customize the error page description

To customize the error page description, use the following Windows PowerShell cmdlet and syntax.

```powershell
Set-AdfsGlobalWebContent -ErrorPageDescriptionText "This is Contoso's error page description"
```

## Customize a generic error message

To customize the generic error message, use the following Windows PowerShell cmdlet and syntax.

```powershell
Set-AdfsGlobalWebContent -ErrorPageGenericErrorMessage "This is a generic error message.  Contact Contoso IT for assistance."
```

## Customize an authorization error message

To customize the authorization error message, use the following Windows PowerShell cmdlet and syntax.

```powershell
Set-AdfsGlobalWebContent -ErrorPageAuthorizationErrorMessage "You have received an Authorization error.  Contact Contoso IT for assistance."
```

## Customize a device authentication error message

To customize the device authentication error message, use the following Windows PowerShell cmdlet and syntax.

```powershell
Set-AdfsGlobalWebContent -ErrorPageDeviceAuthenticationErrorMessage "Your device is not authorized.  Contact Contoso IT for assistance."
```

## Customize a support email error message

You can configure a support email address in AD FS. If configured, AD FS automatically shows a link for end users to email the error details.

To customize the support email error message, use the following Windows PowerShell cmdlet and syntax.

```powershell
Set-AdfsGlobalWebContent -ErrorPageSupportEmail  "admin@contoso.com"
```

## Customize a relying party authorization message

You can configure a relying party authorization error message in AD FS.

To customize the relying party error message, use the following Windows PowerShell cmdlet and syntax.

```powershell
Set-AdfsRelyingPartyWebContent -Name fedpassive -ErrorPageAuthorizationErrorMessage "<p> You need to be a member of Security Auditors to access this site. Click <A href='http://accessrequest/'>here</A> for more information.</p>"
```

## Additional references

[AD FS User Sign-in Customization](ad-fs-user-sign-in-customization)