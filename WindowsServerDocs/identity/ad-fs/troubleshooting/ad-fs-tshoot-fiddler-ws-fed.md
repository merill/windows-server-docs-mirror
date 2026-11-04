---
layout: Conceptual
title: AD FS Troubleshooting - Fiddler - WS-Federation | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-fiddler-ws-fed
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: This document shows an in-depth trace of a WS-Federation exchange with AD FS
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: troubleshooting-general
ms.custom: sfi-image-nochange
locale: en-us
document_id: d7de439a-77b6-172c-99e8-bc83b4eea290
document_version_independent_id: 11df09e8-7b5d-b842-6d2f-2e21556b3afd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-fiddler-ws-fed.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/troubleshooting/ad-fs-tshoot-fiddler-ws-fed
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-fiddler-ws-fed.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 130ecb29-3c20-7318-5036-9aca2169da11
---

# AD FS Troubleshooting - Fiddler - WS-Federation | Microsoft Learn

![AD FS and Windows Server Federation diagram](media/ad-fs-tshoot-fiddler-ws-fed/fiddler9.png)

## Step 1 and 2

This is the beginning of our trace. In this frame we see the following:

![Start of Fiddler trace](media/ad-fs-tshoot-fiddler-ws-fed/fiddler1.png)

Request:

- HTTP GET to our relying party (`https://sql1.contoso.com/SampApp`)

Response:

- The Response is a HTTP 302 (Redirect). The Transport data in the Response header shows where to redirect to (`https://sts.contoso.com/adfs/ls`)
- The redirect URL contains wa=wsignin 1.0 which tells us that our RP application has built a WS-Federation sign-in request for us and sent this to the AD FS's /adfs/ls/ endpoint. This is known as Redirect binding.

![Transport data in the Response header](media/ad-fs-tshoot-fiddler-ws-fed/fiddler2.png)

## Step 3 and 4

![Continuation Fiddler trace](media/ad-fs-tshoot-fiddler-ws-fed/fiddler3.png)

Request:

- HTTP GET to our AD FS server(sts.contoso.com)

Response:

- The Response is a prompt for credentials. This indicates that we are using forms authentication
- By clicking on the WebView of the Response you can see the credentials prompt.

![Screenshot of the web view of the response showing the credentials prompt.](media/ad-fs-tshoot-fiddler-ws-fed/fiddler6.png)

## Step 5 and 6

![WebView tab of the prompt for credentials Prompt screen](media/ad-fs-tshoot-fiddler-ws-fed/fiddler4.png)

Request:

- HTTP POST with our username and password.
- We present our credentials. By looking at the Raw data in the request we can see the credentials

Response:

- The response is Found and the MSIAuth encrypted cookie is created and returned. This is used to validate the SAML assertion produced by our client. This is also known as the "authentication cookie" and will only be present when AD FS is the Idp.

## Step 7 and 8

![Screenshot of the of Fiddler trace showing the H T T P Get request and the response to that request.](media/ad-fs-tshoot-fiddler-ws-fed/fiddler5.png)

Request:

- Now that we have authenticated we do another HTTP GET to the AD FS server and present our authentication token

Response:

- The response is an HTTP OK which means that AD FS has authenticated the user based on the credentials provided
- Also, we set 3 cookies back to the client
    - MSISAuthenticated contains a base64-encoded timestamp value for when the client was authenticated.
    - MSISLoopDetectionCookie is used by the AD FS infinite loop detection mechanism to stop clients who have ended up in an infinite redirection loop to the Federation Server. The cookie data is a timestamp that is base64 encoded.
    - MSISSignout is used to keep track of the IdP and all RPs visited for the SSO session. This cookie is utilized when a WS-Federation sign-out is invoked. You can see the contents of this cookie using a base64 decoder.

## Step 9 and 10

![Screenshot of the of Fiddler trace showing the H T T P Post request and the response to that request.](media/ad-fs-tshoot-fiddler-ws-fed/fiddler7.png)

Request:

- HTTP POST

Response:

- The response is a Found

## Step 11 and 12

![Finalization of Fiddler trace](media/ad-fs-tshoot-fiddler-ws-fed/fiddler8.png)

Request:

- HTTP GET

Response:

- The response is OK