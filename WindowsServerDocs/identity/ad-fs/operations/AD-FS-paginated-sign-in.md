---
layout: Conceptual
title: AD FS paginated sign-in | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/ad-fs-paginated-sign-in
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: This article describes new sign-in experience for AD FS.
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: 67760ed4-7079-db76-cff3-5ed316737822
document_version_independent_id: 3d901879-aefb-34a2-d107-0df42ed698ad
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/AD-FS-paginated-sign-in.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/ad-fs-paginated-sign-in
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/AD-FS-paginated-sign-in.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
platformId: e50911c8-8914-7e4b-a11b-5b88178a2b77
---

# AD FS paginated sign-in | Microsoft Learn

The user interface for sign-in is updated in Windows Server 2019 to feature a look and feel identical to Microsoft Entra ID. This update provides users with a more consistent sign-in experience that incorporates a centered and paginated user flow.

## What's new

In AD FS in Windows Server 2012 R2 and 2016, your sign-in screen looked something like this:

![Screenshot of the old Sign in screen.](media/ad-fs-paginated-sign-in/signin1.png)

Instead of displaying a single form located on the right side of the screen, Windows Server 2019 sign-in features several design updates, including:

- **Centered UI**. In earlier versions, the sign-in UI displays on the right side of the screen, as shown in the previous screenshot. The UI is now positioned front and center to modernize the experience.
- **Pagination**. Instead of a long form to fill out, a new flow takes you through the sign-in experience step-by-step. Our research shows that with this approach, our customers have more successful sign-ins. It also enables more flexibility for incorporating various authentication methods, such us phone factor authentication.

![Screenshot of the new Sign in screen.](media/ad-fs-paginated-sign-in/signin2.png)

On the first page, you're asked to enter your username. You can also select the option to “Keep me signed in” to reduce the frequency of sign-in prompts and remain signed in when it's safe to do so. (This option is disabled by default.)

![Screenshot of the first page of the new Sign in screen.](media/ad-fs-paginated-sign-in/signin3.png)

On the second page, you're presented with authentication options, configured by your administrator. If allowing external authentication as primary is enabled, that is also included.

![Screenshot of the second page of the new Sign in screen.](media/ad-fs-paginated-sign-in/signin4.png)

On the third page, you're asked to enter your password (assuming you selected “Password” as your authentication option).

### Upgrading to paginated sign-in

New installations of AD FS receive the new sign-in UI by default.

If you're an existing customer using AD FS 2012 R2 or 2016, there are two ways to receive the new UI design after upgrading servers to AD FS 2019 and enabling the FBL to 2019.

- Allow the new sign-in via PowerShell. Run the following command to enable pagination:

`Set-AdfsGlobalAuthenticationPolicy -EnablePaginatedAuthenticationPages $true`

- Enable external authentication as primary, either via PowerShell or through the AD FS Server Manager. The new paginated sign-in pages are enabled when this feature is enabled.

If you're a new customer to AD FS, you receive the new design by default. However, if you're using AD FS 2012 R2 or 2016, there are several steps you need to take to receive the new design:

`Set-AdfsGlobalAuthenticationPolicy -AllowAdditionalAuthenticationAsPrimary $true`

## Customization

Options for customization still work in AD FS 2019.

## Related links

- If you don't plan to upgrade your servers to AD FS 2019, but still want to enjoy the new sign-in design: [Using a Microsoft Entra UX Web Theme in Active Directory Federation Services](azure-ux-web-theme-in-ad-fs)
- Customization guidance: [AD FS user sign-in customization](ad-fs-user-sign-in-customization)