---
layout: Conceptual
title: Set up Windows LAPS in the LAPS properties dialog | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/laps/laps-management-user-interface
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to use the LAPS properties dialog to configure Windows Local Administrator Password Solution (Windows LAPS) for Windows Server Active Directory.
author: jay98014
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: e21d484a-dcbd-ad59-10f1-f74e7a7d97de
document_version_independent_id: e21d484a-dcbd-ad59-10f1-f74e7a7d97de
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/laps/laps-management-user-interface.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/laps/laps-management-user-interface
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/laps/laps-management-user-interface.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c915eb59-b9c5-db17-87bf-18d3463b64fa
---

# Set up Windows LAPS in the LAPS properties dialog | Microsoft Learn

Learn how to use the LAPS properties dialog in the Windows Server Active Directory Users and Computers management snap-in to configure Windows Local Administrator Password Solution (Windows LAPS) for Windows Server Active Directory.

## Windows LAPS snap-in availability

The Windows LAPS-enabled Active Directory Users and Computers management snap-in is available on Windows Server platforms that have been patched with the Windows LAPS feature. The Active Directory Users and Computers management snap-in must be installed, either as part of the larger `Active Directory Domain Services` role, or as part of the `AD DS Snap-in and Command-Line Tools` individual feature.

One way to install the `AD DS Snap-Ins and Command-Line Tools` feature is from the command line as follows:

```
dism.exe /online /enable-feature:DirectoryServices-DomainController-Tools /all
```

The Windows LAPS-enabled Active Directory Users and Computers management snap-in is available on supported Windows Client platforms that have been patched with the Windows LAPS feature, via Remote Server Administration Tools (RSAT). You may add RSAT on client platforms by going to Settings, then System (or Apps if on a version older than Windows 10 22H2), then Optional Features, and then add RSAT (specifically search for and add "RSAT: Active Directory Domain Services and Lightweight Directory Services Tools").

The Windows LAPS-enabled Active Directory Users and Computers management snap-in isn't available on older platforms that don't support Windows LAPS. The older Remote Server Administration tools package is not updated to support the new snap-in.

## LAPS properties dialog in the management snap-in

The Windows Server Active Directory Users and Computers management snap-in includes a LAPS properties dialog that's available for computer objects:

![Screenshot that shows the Windows LAPS properties dialog in the Windows Server Active Directory Users and Computers snap-in.](media/laps-management-user-interface/laps-management-user-interface-property-page.png)

You can use the properties dialog to complete the following actions:

- View the current password expiration time.
- Modify the password expiration time.
- Expire the password expiration time.
- View the current account name and password.

Important

The LAPS properties dialog doesn't support viewing legacy Microsoft LAPS passwords or password expiration times.

### View the current password expiration time

When you first go to the properties dialog for a Windows Server Active Directory computer, the date-time control displays the current password expiration time. For example:

![Screenshot that shows the current password expiration time in the Windows LAPS properties dialog in the Windows Server Active Directory Users and Computers snap-in.](media/laps-management-user-interface/laps-management-user-interface-view-password-expiration.png)

### Modify the password expiration time

You can use the date-time control to modify the password expiration time. For example:

![Screenshot that shows a modification of the password expiration time in the Windows LAPS properties dialog in the Windows Server Active Directory Users and Computers snap-in.](media/laps-management-user-interface/laps-management-user-interface-modify-password-expiration.png)

If you modify the date or time, select **Apply**, and then select **OK**.

### Manually expire the password

To immediately expire the password, select **Expire now**:

![Screenshot that shows the Expire now button in the Windows LAPS properties dialog in the Windows Server Active Directory Users and Computers snap-in.](media/laps-management-user-interface/laps-management-user-interface-expire-password-now.png)

Select **Apply**, and then select **OK**.

### View the current account name and password

If you have permissions to read and decrypt the computer's current Windows LAPS password attribute, **Account Name** and **Password** have your username and password. Select **Copy password** to copy the password to the clipboard. Select **Show password** to show the password.

![Screenshot that shows the copy and show password functionality in the Windows LAPS properties dialog in the Windows Server Active Directory Users and Computers snap-in.](media/laps-management-user-interface/laps-management-user-interface-copy-show-password.png)

If you don't have permissions to read or decrypt the current password information, a dialog displays a warning.

Important

The Active Directory Users and Computers management snap-in only supports viewing the most recently stored password. In order to query older passwords (assuming you enabled password history), you must use the `Get-LapsADPassword` PowerShell cmdlet.