---
layout: Conceptual
title: How to configure intranet forms-based authentication for devices that do not support Windows Integrated Authentication (WIA) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/configure-intranet-forms-based-authentication-for-devices-that-do-not-support-wia
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configuring intranet forms-based authentication for devices that do not support Windows Integrated Authentication (WIA)'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: abf9cb6e-38be-d28e-6ad3-1151b7e1a379
document_version_independent_id: 3eed2746-fc1e-b7c3-ea04-203291aec098
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Configure-intranet-forms-based-authentication-for-devices-that-do-not-support-WIA.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/configure-intranet-forms-based-authentication-for-devices-that-do-not-support-wia
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Configure-intranet-forms-based-authentication-for-devices-that-do-not-support-WIA.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c4d81a2c-1e44-aaf8-5bb9-d1ac64d10a98
---

# How to configure intranet forms-based authentication for devices that do not support Windows Integrated Authentication (WIA) | Microsoft Learn

By default, Windows Integrated Authentication (WIA) is enabled in Active Directory Federation Services (AD FS) in Windows Server for authentication requests that occur within the organization's internal network (intranet) for any application that uses a browser for its authentication. For example, applications can be browser-based that use WS-Federation or SAML protocols and rich applications that use the OAuth protocol. WIA provides end users with seamless logon to the applications without having to manually entering their credentials. However, some devices and browsers are not capable of supporting WIA and as a result authentication requests from these devices fail. Also, the experience on certain browsers that negotiate to NTLM is not desirable. The recommended approach is to fall back to forms-based authentication for such devices and browsers.

AD FS in Windows Server 2016 and Windows Server 2012 R2 provides the administrators with the ability to configure the list of user agents that support the fallback to forms-based authentication. The fallback is made possible by two configurations:

- The **WIASupportedUserAgentStrings** property of the `Set-ADFSProperties` commandlet
- The **WindowsIntegratedFallbackEnabled** property of the `Set-AdfsGlobalAuthenticationPolicy` commandlet

The **WIASupportedUserAgentStrings** defines the user agents that support WIA. AD FS analyzes the user agent string when performing logins in a browser or browser control. If the component of the user agent string does not match any of the components of the user agent strings that are configured in **WIASupportedUserAgentStrings** property, AD FS will fall back to providing forms-based authentication, provided that the **WindowsIntegratedFallbackEnabled** flag is set to True.

By default, a new AD FS installation has a set of user agent string matches created. However, these may be out of date based on changes to browsers and devices. Particularly, Windows devices have similar user agent strings with minor variations in the tokens. The following Windows PowerShell example provides the best guidance for the current set of devices that are on the market today that support seamless WIA:

```powershell
Set-AdfsProperties -WIASupportedUserAgents @("MSIE 6.0", "MSIE 7.0; Windows NT", "MSIE 8.0", "MSIE 9.0", "MSIE 10.0; Windows NT 6", "Windows NT 6.3; Trident/7.0", "Windows NT 6.3; Win64; x64; Trident/7.0", "Windows NT 6.3; WOW64; Trident/7.0", "Windows NT 6.2; Trident/7.0", "Windows NT 6.2; Win64; x64; Trident/7.0", "Windows NT 6.2; WOW64; Trident/7.0", "Windows NT 6.1; Trident/7.0", "Windows NT 6.1; Win64; x64; Trident/7.0", "Windows NT 6.1; WOW64; Trident/7.0", "MSIPC", "Windows Rights Management Client")
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
| MSIPC | Microsoft Information Protection and Control Client |
| Windows Rights Management Client | Windows Rights Management Client |

In order to enable fall back to form based authentication for user agents other than those mentioned in the WIASupportedUserAgents string, set the WindowsIntegratedFallbackEnabled flag to true

```powershell
Set-AdfsGlobalAuthenticationPolicy -WindowsIntegratedFallbackEnabled $true
```

Also ensure that the forms-based authentication is enabled for intranet.

## Configuring WIA for Chrome

You can add Chrome or other user agents to the AD FS configuration that supports WIA. This enables seamless logon to applications without having to manually enter credentials when you access resources protected by AD FS. Follow the steps below to enable WIA on Chrome:

In AD FS configuration, add a user agent string for Chrome on Windows-based platforms:

```powershell
Set-AdfsProperties -WIASupportedUserAgents (Get-ADFSProperties | Select -ExpandProperty WIASupportedUserAgents) + "Mozilla/5.0 (Windows NT)"
```

And similarly for Chrome on Apple macOS, add the following user agent string to the AD FS configuration:

```powershell
Set-AdfsProperties -WIASupportedUserAgents (Get-ADFSProperties | Select -ExpandProperty WIASupportedUserAgents) + "Mozilla/5.0 (Macintosh; Intel Mac OS X)"
```

Confirm that the user agent string for Chrome is now set in the AD FS properties:

```powershell
Get-AdfsProperties | Select -ExpandProperty WIASupportedUserAgents
```

![configure auth](media/configure-intranet-forms-based-authentication-for-devices-that-do-not-support-wia/chrome1.png)

Note

As new browsers and devices are released, it is recommended that you reconcile the capabilities of those user agents and update the AD FS configuration accordingly to optimize the user's authentication experience when using said browser and devices. More specifically, it is recommended that you re-evaluate the **WIASupportedUserAgents** setting in AD FS when adding a new device or browser type to your support matrix for WIA.