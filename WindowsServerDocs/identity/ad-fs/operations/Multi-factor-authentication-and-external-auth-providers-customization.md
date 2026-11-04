---
layout: Conceptual
title: Multi-factor authentication and external authentication providers customization | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/multi-factor-authentication-and-external-auth-providers-customization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: Learn more about multi-factor authentication and external authentication providers customization.
ms.topic: how-to
ms.date: 2025-04-08T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: 710ec0bf-834b-5dbf-3205-e2ca4e43d7d0
document_version_independent_id: 88d05134-e8e6-1c43-277f-110d478d5d40
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Multi-factor-authentication-and-external-auth-providers-customization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/multi-factor-authentication-and-external-auth-providers-customization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Multi-factor-authentication-and-external-auth-providers-customization.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: c1ba9e0b-cd99-8efb-9a78-3a518ec2d47a
---

# Multi-factor authentication and external authentication providers customization | Microsoft Learn

In AD FS, support for multi-factor authentication is included out of the box. For example, you can configure AD FS to use built in Certificate Authentication as the second factor authentication. You can also use external authentication providers. This approach can enable AD FS to integrate with other services, such as Azure Multi-factor Authentication, or you can develop your own provider. See [Solution Guide: Manage Risk with Multi-factor Access Control](manage-risk-with-conditional-access-control) for more information about how to register external authentication provider by using AD FS.

An external authentication provider should use the classes that are defined in the .css file that AD FS provides to author the authentication UI. You can use the following cmdlet to export the default web theme and inspect the user interface classes and elements that are defined in the .css file. The .css file can be used in the development of the sign-in user interface of an external authentication provider.

```powershell
Export-AdfsWebTheme -Name default -DirectoryPath C:\theme
```

The following example shows a sign-in user interface, which is highlighted in RED, by an external authentication provider. The user interface uses the UI classes in the AD FS .css file.

![Screenshot that shows an example of the sign-in user interface.](media/ad-fs-user-sign-in-customization/adfs_blue_custom8.png)

Before you write a new custom authentication method, study the AD FS theme and style definitions to understand the content authoring requirements.

- A custom authentication method only authors an HTML segment on the AD FS sign-in page and not the full page. Use the AD FS style definition to get the consistent appearance and behavior.

![AD FS and MFA](media/ad-fs-user-sign-in-customization/adfs_blue_custom9.png)

- AD FS administrators can customize the AD FS styles. Don't hardcode your own styles. Instead, try using AD FS styles whenever possible.
- Out of the box, AD FS styles are authored with one left-to-right (LTR) style and one right-to-left (RTL). Administrators can customize both and can provide language-specific styles through the web theme definition. Each stylesheet has three sections with respective comments:
- **theme styles** - These styles shouldn't and can't be used. These styles are meant to define the theme across all pages. They're defined with an element ID purposely so that they aren't reused.
- **common styles** - These styles are the styles that should be used for your content.
- **form factor styles** - These styles for different form factors. You should understand this section to ensure that your content works with different form factors, for example, phones and tablets.

For more information, see [Solution Guide: Manage Risk with Multi-factor Access Control](manage-risk-with-conditional-access-control) and [Walkthrough Guide: Manage Risk with Additional Multi-Factor Authentication for Sensitive Applications](/en-us/windows-server/identity/ad-fs/operations/walkthrough-guide--manage-risk-with-additional-multi-factor-authentication-for-sensitive-applications)).

## Related links

[AD FS User Sign-in Customization](ad-fs-user-sign-in-customization)