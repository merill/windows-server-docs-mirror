---
layout: Conceptual
title: Connect to Remote Desktop Services in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/connect-remote-desktop-services
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how you can connect to a remote session from Remote Desktop Services in Windows Server using Windows App or the Remote Desktop client.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-19T00:00:00.0000000Z
locale: en-us
document_id: 66e76859-a8f5-ffeb-98a6-8ae3325f4951
document_version_independent_id: 66e76859-a8f5-ffeb-98a6-8ae3325f4951
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/connect-remote-desktop-services.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/connect-remote-desktop-services
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/connect-remote-desktop-services.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/cd440f3c-1b78-40a7-97ba-aa00a1d79df7
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c828f7e0-89b4-459c-9bae-d7ab1c4bd9ad
platformId: b4655f59-6684-350d-9a98-124a3e056294
---

# Connect to Remote Desktop Services in Windows Server | Microsoft Learn

You can connect to remote desktops and apps running in Remote Desktop Services using Windows App or the Remote Desktop client.

Windows App and the Remote Desktop client are available on many different types of devices on different platforms and form factors, such as desktops and laptops, tablets, smartphones, through a web browser, and virtual reality headsets. This choice provides flexibility and convenience to access desktops and apps from anywhere.

Here's an introductory video for Windows App showing connecting to remote desktops and apps. It combines resources from Remote Desktop Services, remote PC connections, Azure Virtual Desktop, Windows 365, and Microsoft Dev Box.

There are many features you can use to enhance your remote experience, such as:

- Multiple monitor support, with custom and dynamic display resolutions and scaling.
- Microsoft Teams optimizations.
- Device redirection, such as webcams, audio, storage devices, and printers.
- Single sign-on to eliminate the need to enter credentials multiple times.
- Sign in with multiple accounts and easily switch between them.

## How can I connect to Remote Desktop Services?

First, you need to decide whether to use Windows App or the Remote Desktop client to connect to Remote Desktop Services. Windows App replaces the Remote Desktop client and it's available for all platforms, but you can't currently connect to Remote Desktop Services using Windows App from all platforms, so you might still need to use the Remote Desktop client.

Here's what platforms you can use to connect to Remote Desktop Services from Windows App and the Remote Desktop client:

| Platform | Windows App | Remote Desktop client |
| --- | --- | --- |
| Windows | ❌ | ✅ |
| macOS | ✅ | ✅ |
| iOS/iPadOS | ✅ | ✅ |
| Android | ✅ | ✅ |
| Web browser | ❌ | ✅ |

Once you choose which app to use, download an install it on your device. If you want to connect from a web browser, contact your administrator for their specific link to the Remote Desktop Web client.

In the following articles, you can find download links for Windows App and the Remote Desktop client, and detailed guidance on how to connect to Remote Desktop Services for each supported platform. You need your user account for Remote Desktop Services to sign in, which is provided by your administrator.

- **Windows App**:

    - [macOS](/en-us/windows-app/get-started-connect-devices-desktops-apps?pivots=remote-desktop-services&amp;tabs=macos-rds)
    - [iOS/iPadOS](/en-us/windows-app/get-started-connect-devices-desktops-apps?pivots=remote-desktop-services&amp;tabs=ios-ipados-rds)
    - [Android](/en-us/windows-app/get-started-connect-devices-desktops-apps?pivots=remote-desktop-services&amp;tabs=android-rds)
- **Remote Desktop client**:

    - [Windows](/en-us/previous-versions/remote-desktop-client/remote-desktop-windows-urdc)
    - [macOS](/en-us/previous-versions/remote-desktop-client/remote-desktop-macos)
    - [iOS/iPadOS](/en-us/previous-versions/remote-desktop-client/remote-desktop-ios-ipados)
    - [Android](/en-us/previous-versions/remote-desktop-client/remote-desktop-android)
    - [Web browser](remote-desktop-web-client)

Tip

You should use Windows App to connect to Remote Desktop Services where possible as it replaces the Remote Desktop client.