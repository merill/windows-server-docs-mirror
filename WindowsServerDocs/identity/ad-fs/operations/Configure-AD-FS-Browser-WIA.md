---
layout: Conceptual
title: Configure browsers to use Windows Integrated Authentication (WIA) with AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/configure-ad-fs-browser-wia
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: This document describes how to configure browsers to use WIA with AD FS
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: cd7eb3f6-c00a-453f-a596-6f8bde452cb7
document_version_independent_id: 3250a24b-8e71-a36c-a9a0-7c46bc36acd4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Configure-AD-FS-Browser-WIA.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/configure-ad-fs-browser-wia
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Configure-AD-FS-Browser-WIA.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
platformId: 35b1577d-d7b1-1ff0-98b2-7f0dcb8238f6
---

# Configure browsers to use Windows Integrated Authentication (WIA) with AD FS | Microsoft Learn

By default, Windows Integrated Authentication (WIA) is enabled in Active Directory Federation Services (AD FS) in Windows Server 2012 R2 for authentication requests that occur within the organization's internal network (intranet) for any application that uses a browser for its authentication.

AD FS 2016 now has an improved default setting that enables the Edge browser to do WIA while not also (incorrectly) catching Windows Phone as well:

```
=~Windows\s*NT.*Edg.*
```

The above means you no longer have to configure individual user agent strings to support common Edge scenarios, even though they are updated quite often.

For other browsers, configure the AD FS property **WiaSupportedUserAgents** to add the required values based on the browsers you are using. You can use the procedures below.

### View WIASupportedUserAgent settings

The **WIASupportedUserAgents** defines the user agents that support WIA. AD FS analyzes the user agent string when performing logins in a browser or browser control.

You can view the current settings using the following PowerShell example:

```powershell
Get-AdfsProperties | select -ExpandProperty WiaSupportedUserAgents
```

![WIA Support](media/configure-ad-fs-browser-wia/wiasupport.png)

### Change WIASupportedUserAgent settings

By default, a new AD FS installation has a set of user agent string matches created. However, these may be out of date based on changes to browsers and devices. Particularly, Windows devices have similar user agent strings with minor variations in the tokens. The following Windows PowerShell example provides the best guidance for the current set of devices that are on the market today that support seamless WIA:

If you have AD FS on Windows Server 2012 R2 or earlier:

```powershell
Set-AdfsProperties -WIASupportedUserAgents @("MSIE 6.0", "MSIE 7.0; Windows NT", "MSIE 8.0", "MSIE 9.0", "MSIE 10.0; Windows NT 6", "Windows NT 6.3; Trident/7.0", "Windows NT 6.3; Win64; x64; Trident/7.0", "Windows NT 6.3; WOW64; Trident/7.0", "Windows NT 6.2; Trident/7.0", "Windows NT 6.2; Win64; x64; Trident/7.0", "Windows NT 6.2; WOW64; Trident/7.0", "Windows NT 6.1; Trident/7.0", "Windows NT 6.1; Win64; x64; Trident/7.0", "Windows NT 6.1; WOW64; Trident/7.0","Windows NT 10.0; WOW64; Trident/7.0","MSIPC", "Windows Rights Management Client", "Edg/","Edge/")
```

If you have AD FS on Windows Server 2016 or later:

```powershell
Set-AdfsProperties -WIASupportedUserAgents @("MSIE 6.0", "MSIE 7.0; Windows NT", "MSIE 8.0", "MSIE 9.0", "MSIE 10.0; Windows NT 6", "Windows NT 6.3; Trident/7.0", "Windows NT 6.3; Win64; x64; Trident/7.0", "Windows NT 6.3; WOW64; Trident/7.0", "Windows NT 6.2; Trident/7.0", "Windows NT 6.2; Win64; x64; Trident/7.0", "Windows NT 6.2; WOW64; Trident/7.0", "Windows NT 6.1; Trident/7.0", "Windows NT 6.1; Win64; x64; Trident/7.0", "Windows NT 6.1; WOW64; Trident/7.0","Windows NT 10.0; WOW64; Trident/7.0", "MSIPC", "Windows Rights Management Client", "=~Windows\s*NT.*Edg.*")
```

The command above will ensure that AD FS only covers the following use cases for WIA:

| User Agents | Use cases |
| --- | --- |
| MSIE 6.0 | IE 6.0 |
| MSIE 7.0; Windows NT | IE 7, IE in intranet zone. The "Windows NT" fragment is sent by desktop operation system. |
| MSIE 8.0 | IE 8.0 (no devices send this, so need to make more specific) |
| MSIE 9.0 | IE 9.0 (no devices send this, so no need to make this more specific) |
| MSIE 10.0; Windows NT 6 | IE 10.0 for Windows XP and newer versions of desktop operating systemWindows Phone 8.0 devices (with preference set to mobile) are excluded because they sendUser-Agent: Mozilla/5.0 (compatible; MSIE 10.0; Windows Phone 8.0; Trident/6.0; IEMobile/10.0; ARM; Touch; NOKIA; Lumia 920) |
| Windows NT 6.3; Trident/7.0Windows NT 6.3; Win64; x64; Trident/7.0Windows NT 6.3; WOW64; Trident/7.0 | Windows 8.1 desktop operating system, different platforms |
| Windows NT 6.2; Trident/7.0Windows NT 6.2; Win64; x64; Trident/7.0Windows NT 6.2; WOW64; Trident/7.0 | Windows 8 desktop operating system, different platforms |
| Windows NT 6.1; Trident/7.0Windows NT 6.1; Win64; x64; Trident/7.0Windows NT 6.1; WOW64; Trident/7.0 | Windows 7 desktop operating system, different platforms |
| Edg/ and Edge/ | Microsoft Edge (Chromium) for Windows Server 2012 R2 or earlier |
| =~Windows\s\*NT.\*Edg.\* | Microsoft Edge (Chromium) for Windows Server 2016 or later |
| MSIPC | Microsoft Information Protection and Control Client |
| Windows Rights Management Client | Windows Rights Management Client |

### Additional links

[Microsoft Edge documentation](/en-us/microsoft-edge/web-platform/user-agent-string)