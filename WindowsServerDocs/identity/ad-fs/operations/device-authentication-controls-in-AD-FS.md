---
layout: Conceptual
title: Device Authentication controls in AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/device-authentication-controls-in-ad-fs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: This document describes how to enable device authentication in AD FS for Windows Server 2016 and 2012 R2
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 5d4dff54-0199-2bc2-a8bd-5e807c6a784a
document_version_independent_id: f46f1bfa-afa4-83aa-2c69-12e910df2917
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/device-authentication-controls-in-AD-FS.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/device-authentication-controls-in-ad-fs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/device-authentication-controls-in-AD-FS.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7f6da2db-876a-b453-5c65-35cbc852e744
---

# Device Authentication controls in AD FS | Microsoft Learn

The following document shows how to enable device authentication controls in Windows Server 2016 and 2012 R2.

## Device Authentication controls in AD FS 2012 R2

Originally in AD FS 2012 R2 there was one global authentication property called `DeviceAuthenticationEnabled` that controlled device authentication.

To configure the setting, the `Set-AdfsGlobalAuthenticationPolicy` cmdlet was used as shown below:

```powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationEnabled $true
```

To disable device authentication, the same cmdlet was used to set the value to $false.

## Device Authentication controls in AD FS 2016

The only type of device authentication supported in 2012 R2 was clientTLS. In AD FS 2016, in addition to clientTLS there are two new types of device authentication for modern devices authentication. These are:

- PKeyAuth
- PRT

To control the new behavior, the `DeviceAuthenticationEnabled` property is used in combination with a new property called `DeviceAuthenticationMethod`.

The device authentication method determines the type of device authentication that will be done: PRT, PKeyAuth, clientTLS, or some combination. It has the following values:

- SignedToken: PRT only
- PKeyAuth: PRT + PKeyAuth
- ClientTLS: PRT + clientTLS
- All: All of the above

As you can see, PRT is part of all device authentication methods, making it in effect the default method that is always enabled when `DeviceAuthenticationEnabled` is set to `$true`.

Example: To configure the method(s), use the DeviceAuthenticationEnabled cmdlet as above, along with new property:

```powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationEnabled $true
```

Note

In AD FS 2019, `DeviceAuthenticationMethod` can be used with the `Set-AdfsRelyingPartyTrust` command.

```powershell
PS:\>Set-AdfsRelyingPartyTrust -DeviceAuthenticationMethod ClientTLS
```

Note

Enabling device authentication (setting `DeviceAuthenticationEnabled` to `$true`) means the `DeviceAuthenticationMethod` is implicitly set to `SignedToken`, which equates to **PRT**.

```powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationMethod All
```

Note

The default device authentication method is `SignedToken`. Other values are **PKeyAuth,** **ClientTLS,** and **All**.

The meanings of the `DeviceAuthenticationMethod` values have changed slightly since AD FS 2016 was released. See the table below for the meaning of each value, depending on the update level:

| AD FS version | DeviceAuthenticationMethod value | Means |
| --- | --- | --- |
| 2016 RTM | SignedToken | PRT + PkeyAuth |
|  | clientTLS | clientTLS |
|  | All | PRT + PkeyAuth + clientTLS |
| 2016 RTM + up to date with Windows Update | SignedToken (changed meaning) | PRT (only) |
|  | PkeyAuth (new) | PRT + PkeyAuth |
|  | clientTLS | PRT + clientTLS |
|  | All | PRT + PkeyAuth + clientTLS |