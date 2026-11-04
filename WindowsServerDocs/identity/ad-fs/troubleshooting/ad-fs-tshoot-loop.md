---
layout: Conceptual
title: AD FS Troubleshooting - Loop Detection | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-loop
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: This article describes how to troubleshoot loop detection for Active Directory Federation Services (AD FS).
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: troubleshooting-general
locale: en-us
document_id: 2b97892a-9197-c162-f604-1db5c3417490
document_version_independent_id: 3793f572-edb0-94f6-d5ca-6f8a0191a3d5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-loop.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/troubleshooting/ad-fs-tshoot-loop
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-loop.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
platformId: 153a890c-72bd-92ef-10de-77bd8d89b93e
---

# AD FS Troubleshooting - Loop Detection | Microsoft Learn

Looping in Active Directory Federation Services (AD FS) occurs when a relying party continuously rejects a valid security token and redirects back to AD FS.

## Loop detection cookie

To prevent this problem from happening, AD FS implemented a loop detection cookie. By default, AD FS writes a cookie to web passive clients named `MSISLoopDetectionCookie`. This cookie holds a timestamp value and a value for the number of tokens issued. This information allows AD FS to keep track of how often and how many times a client visited the federation service within a specific timespan.

If a passive client visits the federation service for a token five times within 20 seconds, AD FS throws the following error:

`MSIS7042: The same client browser session has made '{0}' requests in the last '{1}' seconds. Contact your administrator for details.`

Entering into infinite loops is often caused by a misbehaving relying party application that isn't successfully consuming the token issued by AD FS. The application then sends the passive client back to AD FS, repeatedly, for a new token. AD FS issues the passive client a new token each time, with a limit of five requests within 20 seconds.

## Adjust the loop detection cookie

You can use PowerShell to change the value for the number of tokens issued and the timespan value.

```powershell
Set-AdfsProperties -LoopDetectionMaximumTokensIssuedInterval 5  -LoopDetectionTimeIntervalInSeconds 20
```

The minimum value for `LoopDetectionMaximumTokensIssuedInterval` is 1.

The minimum value for `LoopDetectionTimeIntervalInSeconds` is 5.

You can also disable loop detection when you're doing performance testing.

```powershell
Set-AdfsProperties -EnableLoopDetection $false
```

Important

Don't disable loop detection permanently because it prevents users from entering into infinite loop states.