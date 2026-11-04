---
layout: Conceptual
title: Test Lab Guide - Demonstrate DirectAccess with OTP Authentication and RSA SecurID | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-otp-securid/test-lab-guide-demonstrate-directaccess-with-otp-authentication-and-rsa-securid
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to extend the Demonstrate DirectAccess Single Server Setup with Mixed IPv4 and IPv6 test lab guide to demonstrate a Remote Access one-time password (OTP) configuration.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: d9cbfddb-b011-918b-a4a8-f54f3dcc994b
document_version_independent_id: d10f429b-22b3-9803-12c1-0bea076322b0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-otp-securid/Test-Lab-Guide-Demonstrate-DirectAccess-with-OTP-Authentication-and-RSA-SecurID.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-otp-securid/test-lab-guide-demonstrate-directaccess-with-otp-authentication-and-rsa-securid
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-otp-securid/Test-Lab-Guide-Demonstrate-DirectAccess-with-OTP-Authentication-and-RSA-SecurID.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ac617758-3020-8a91-3720-b0fea690fdbb
---

# Test Lab Guide - Demonstrate DirectAccess with OTP Authentication and RSA SecurID | Microsoft Learn

Remote Access is a server role in the Windows Server 2016, Windows Server 2012 R2 and Windows Server 2012 operating system that enables remote users to securely access internal network resources using DirectAccess or virtual private networks (VPNs) with the Routing and Remote Access Service (RRAS). This guide contains step-by-step instructions for extending the [Test Lab Guide: Demonstrate DirectAccess Single Server Setup with Mixed IPv4 and IPv6](https://go.microsoft.com/fwlink/p/?LinkId=237004) to demonstrate a Remote Access one-time password (OTP) configuration.

Warning

The design of this test lab guide includes infrastructure servers, such as a domain controller and a certification authority (CA) that are running either Windows Server 2012 R2 or Windows Server 2012. Using this test lab guide to configure infrastructure servers that are running other operating systems has not been tested, and instructions for configuring other operating systems are not included in this guide.

## About this guide

Remote Access in Windows Server 2016, Windows Server 2012 R2 and Windows Server 2012 adds support for client authentication with OTP. For the purposes of this test lab only RSA SecurID is used to demonstrate OTP functionality with Remote Access. Other RADIUS based OTP solutions are supported as well, but are outside the scope of this test lab. This guide contains instructions for configuring and demonstrating Remote Access using six servers and two client computers. The completed Remote Access with OTP test lab simulates an intranet, the Internet, and a home network, and demonstrates Remote Access functionality in different Internet connection scenarios.

Important

This lab is a proof of concept using the minimum number of computers. The configuration detailed in this guide is for test lab purposes only, and is not to be used in a production environment.