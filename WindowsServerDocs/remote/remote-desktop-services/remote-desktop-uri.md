---
layout: Conceptual
title: Remote Desktop URI scheme | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/remote-desktop-uri
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn about the Uniform Resource Identifier scheme for Remote Desktop clients
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
locale: en-us
document_id: 52243ef6-6e78-3b42-a5d2-33b17c0401bd
document_version_independent_id: 52243ef6-6e78-3b42-a5d2-33b17c0401bd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/remote-desktop-uri.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/remote-desktop-uri
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/remote-desktop-uri.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: b4b1c635-aa81-b931-20cc-fb92e67f6765
---

# Remote Desktop URI scheme | Microsoft Learn

This document defines the format of Uniform Resource Identifiers (URIs) for Remote Desktop. These URI schemes allow for Remote Desktop clients to be invoked with various commands.

## ms-rd URI scheme

Note

The ms-rd URI scheme is currently only supported with the Windows Desktop client (MSRDC).

The ms-rd URI provides the option to specify a command for the client and a set of parameters specific to the command using the following format:

```
ms-rd:command?parameters
```

`Parameters` uses the query string format of key=value pair separated by & to provide additional information for the given command:

```
param1=value1&param2=value2&…
```

### Commands and parameters

Here's the list of currently supported commands and their corresponding parameters.

Using `ms-rd:` without any commands launches the client.

#### Subscribe

This command launches the client and starts the subscription process.

**Command name:** subscribe

**Command parameters:**

| Parameter | Description | Values |
| --- | --- | --- |
| url | Specifies the Workspace URL. | A valid URL, such as `https://contoso.com`&gt;`. |

**Example:**`ms-rd:subscribe?url=https://contoso.com`

## Legacy rdp URI scheme

Note

The following URI scheme is only supported with the clients for macOS, iOS, and Android devices.

Microsoft Remote Desktop uses the URI scheme rdp://query\_string to store preconfigured attribute settings that are used when launching the client. The query strings represent a single or set of RDP attributes provided in the URL.

The RDP attributes are separated by the ampersand symbol (&). For example, when connecting to a PC, the string is:

```
rdp://full%20address=s:mypc:3389&audiomode=i:2&disable%20themes=i:1
```

This table gives a complete list of supported attributes that can be used with the iOS, Mac, and Android Remote Desktop clients. (An "x" in the platform column indicates the attribute is supported. The values denoted by chevrons (&lt;&gt;) represent the values that the Remote Desktop client supports.)

| RDP attribute | Android | Mac | iOS |
| --- | --- | --- | --- |
| allow desktop composition=i:&lt;0 or 1&gt; | x | x | x |
| allow font smoothing=i:&lt;0 or 1&gt; | x | x | x |
| alternate shell=s:&lt;string&gt; | x | x | x |
| [audiomode=i:&lt;0, 1, or 2&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393707%28v=ws.10%29) | x | x | x |
| [authentication level=i:&lt;0 or 1&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393709%28v=ws.10%29) | x | x | x |
| connect to console=i:&lt;0 or 1&gt; | x | x | x |
| [desktopheight=i:&lt;value in pixels&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393702%28v=ws.10%29) |  | x |  |
| [desktopwidth=i:&lt;value in pixels&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393697%28v=ws.10%29) |  | x |  |
| disable cursor settings=i:&lt;0 or 1&gt; | x | x | x |
| disable full window drag=i:&lt;0 or 1&gt; | x | x | x |
| disable menu anims=i:&lt;0 or 1&gt; | x | x | x |
| disable themes=i:&lt;0 or 1&gt; | x | x | x |
| disable wallpaper=i:&lt;0 or 1&gt; | x | x | x |
| [domain=s:&lt;string&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393673%28v=ws.10%29) | x | x | x |
| [drivestoredirect=s:*](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393728%28v=ws.10%29) (this is the only supported value) | x | x |  |
| [full address=s:&lt;string&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393661%28v=ws.10%29) | x | x | x |
| gatewayhostname=s:&lt;string&gt; | x | x | x |
| [gatewayusagemethod=i:&lt;1 or 2&gt;](/en-us/windows/win32/termserv/imsrdpclienttransportsettings-gatewayusagemethod) | x | x | x |
| [loadbalanceinfo=s:&lt;string&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393684%28v=ws.10%29) | x | x | x |
| [prompt for credentials on client=i:&lt;0 or 1&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393660%28v=ws.10%29) |  | x |  |
| [redirectprinters=i:&lt;0 or 1&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393671%28v=ws.10%29) |  | x |  |
| remoteapplicationcmdline=s:&lt;string&gt; | x | x | x |
| remoteapplicationmode=i:&lt;0 or 1&gt; | x | x | x |
| remoteapplicationprogram=s:&lt;string&gt; | x | x | x |
| [screen mode id=i:&lt;1 or 2&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393692%28v=ws.10%29) |  | x |  |
| [session bpp=i:&lt;8, 15, 16, 24, or 32&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393680%28v=ws.10%29) |  | x |  |
| shell working directory=s:&lt;string&gt; | x | x | x |
| [use multimon=i:&lt;0 or 1&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393695%28v=ws.10%29) |  | x |  |
| use redirection server name=i:&lt;0 or 1&gt; | x | x | x |
| [username=s:&lt;string&gt;](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393678%28v=ws.10%29) | x | x | x |