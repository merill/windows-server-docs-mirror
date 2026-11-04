---
layout: Conceptual
title: Update password customization | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/update-password-customization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Update password customization'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: 1829a80f-b015-d8a8-c76a-7481e174bfff
document_version_independent_id: db62ce77-eba5-821d-099e-78b28619df6c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Update-password-customization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/update-password-customization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Update-password-customization.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: de4f298d-99ea-93e4-b31e-f1e83d73a489
---

# Update password customization | Microsoft Learn

In some instances, users might not be able to connect to the corporate network to change their account password. This factor can be problematic especially for remote employees who might live far from the nearest corporate office. For these specific cases, the update password page can be used by only connecting to the Internet.

You can customize the update password page by providing your own description for the page.

To enable the password update page, go to AD FS Management under Endpoints. The endpoint for update password is located at the bottom under Other - /adfs/portal/updatepassword/. Once you have enabled the endpoint, you must restart the AD FS service. This must be done manually. If you expect using update password webpage externally, and when using Web Application Proxy, under the same option you need to enable it on the proxy (Enable on proxy). You can then navigate to `https://<fqdn>/adfs/portal/updatepassword/` on a workplace joined device and you should see the update password page.

![update](media/ad-fs-user-sign-in-customization/adfs_blue_custom5.png)

## Customize the Update Password page description

To customize the update password page description, use the following Windows PowerShell cmdlet and syntax.

```powershell
Set-AdfsGlobalWebContent -UpdatePasswordPageDescriptionText "This is the Contoso Update Password page."
```

## Additional references

[AD FS User Sign-in Customization](ad-fs-user-sign-in-customization)