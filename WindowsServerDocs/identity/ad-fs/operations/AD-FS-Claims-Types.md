---
layout: Conceptual
title: Client access claim types in AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/ad-fs-claims-types
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Client access policy claim Types in AD FS'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: ecd05228-38b5-0e37-8eef-b2f2d801f0f3
document_version_independent_id: 94163f6d-4010-e679-81ef-a33a8397348a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/AD-FS-Claims-Types.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/ad-fs-claims-types
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/AD-FS-Claims-Types.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cf9b82c5-b6dc-45f3-b005-b1bc5fc03bea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/0c85d34e-bfd2-4466-957c-f0b61e9692df
platformId: c5e41e4a-c8c0-0caf-1634-fcdbd4068b49
---

# Client access claim types in AD FS | Microsoft Learn

To provide more request context information, Client Access Policies use the following claim types, which AD FS generates from request header information for processing. For more information, see [The role of the claims engine](../technical-reference/the-role-of-the-claims-engine).

## X-MS-Forwarded-Client-IP

Claim type: `http://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-forwarded-client-ip`

This AD FS claim represents a "best attempt" at ascertaining the IP address of the user (for example, the Outlook client) making the request. This claim can contain multiple IP addresses, including the address of every proxy that forwarded the request. This claim is populated from an HTTP header that is currently only set by Exchange Online, which populates the header when passing the authentication request to AD FS. The value of the claim can be one of the following:

- A single IP address - The IP address of the client that is directly connected to Exchange Online

    Note

    The IP address of a client on the corporate network will appear as the external interface IP address of the organization's outbound proxy or gateway.
- One or more IP addresses

    - If Exchange Online can't determine the IP address of the connecting client, it will set the value based on the value of the x-forwarded-for header, a non-standard header that can be included in HTTP-based requests and is supported by many clients, load balancers, and proxies on the market.
    - Multiple IP addresses indicating the client IP address and the address of each proxy that passed the request will be separated by a comma.

        Note

        IP addresses related to Exchange Online infrastructure will not be present in the list.

Warning

Exchange Online currently supports only IPv4 addresses; it does not support IPv6 addresses.

## X-MS-Client-Application

Claim type: `http://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-client-application`

This AD FS claim represents the protocol used by the end client, which corresponds loosely to the application being used. This claim is populated from an HTTP header that is currently only set by Exchange Online, which populates the header when passing the authentication request to AD FS. Depending on the application, the value of this claim will be one of the following:

- In the case of devices that use Exchange Active Sync, the value is Microsoft.Exchange.ActiveSync.
- Use of the Microsoft Outlook client may result in any of the following values:
    - Microsoft.Exchange.Autodiscover
    - Microsoft.Exchange.OfflineAddressBook
    - Microsoft.Exchange.RPC
    - Microsoft.Exchange.WebServices
    - Microsoft.Exchange.Mapi
- Other possible values for this header include the following:
    - Microsoft.Exchange.Powershell
    - Microsoft.Exchange.SMTP
    - Microsoft.Exchange.PopImap
    - Microsoft.Exchange.Pop
    - Microsoft.Exchange.Imap

## X-MS-Client-User-Agent

Claim type: `http://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-client-user-agent`

This AD FS claim provides a string to represent the device type that the client is using to access the service. This can be used when customers would like to prevent access for certain devices (such as particular types of smart phones). This claim is populated from an HTTP header that is currently only set by Exchange Online, which populates the header when passing the authentication request to AD FS. Example values for this claim include (but aren't limited to) the values below.

Note

The below are examples of what the x-ms-user-agent value might contain for a client whose x-ms-client-application is "Microsoft.Exchange.ActiveSync"

- Vortex/1.0
- Apple-iPad1C1/812.1
- Apple-iPhone3C1/811.2
- Apple-iPhone/704.11
- Moto-DROID2/4.5.1
- SAMSUNGSPHD700/100.202
- Android/0.3

Note

It is also possible that this value is empty.

## X-MS-Proxy

Claim type: `http://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-proxy`

This AD FS claim indicates that the request has passed through the federation server proxy. This claim is populated by the federation server proxy, which populates the header when passing the authentication request to the back-end Federation Service. AD FS then converts it to a claim.

The value of the claim is the DNS name of the federation server proxy that passed the request.

## X-MS-Endpoint-Absolute-Path (Active vs Passive)

Claim type: `http://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-endpoint-absolute-path`

This claim type can be used for determining requests originating from "active" (rich) clients versus "passive" (web-browser-based) clients. This enables external requests from browser-based applications such as the Outlook Web Access, SharePoint Online, or the Office 365 portal to be allowed while requests originating from rich clients such as Microsoft Outlook are blocked.

The value of the claim is the name of the AD FS service that received the request.