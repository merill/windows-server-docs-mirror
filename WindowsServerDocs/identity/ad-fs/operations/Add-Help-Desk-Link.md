---
layout: Conceptual
title: Add Help Desk Link | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/add-help-desk-link
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Add Help Desk Link'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 8e2aeafb-b8c6-a167-814c-daba44011abb
document_version_independent_id: 00ca6ed0-2ba9-8980-eff7-4c6ddd30efff
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Add-Help-Desk-Link.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/add-help-desk-link
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Add-Help-Desk-Link.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 63ad2e61-c3d8-4275-701a-5a50e169a0f2
---

# Add Help Desk Link | Microsoft Learn

## To Add a Help Desk Link

To add the help desk link that is displayed on the sign-in page, use the following Windows PowerShell cmdlet and syntax.

![add help desk](media/ad-fs-user-sign-in-customization/adfs_blue_custom2.png)

`Set-AdfsGlobalWebContent -HelpDeskLink https://fs1.contoso.com/help/ -HelpDeskLinkText Help`

Important

The `linkText` parameter in this cmdlet is not required unless you use another value than the default, which is *Help*. The advantage of using the default is that they are localized to all client locales. After the page is customized, the customization takes precedence; therefore, you should customize for all languages that you want to support.

## Additional references

[AD FS User Sign-in Customization](ad-fs-user-sign-in-customization)