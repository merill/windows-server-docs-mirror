---
layout: Conceptual
title: Test Lab Guide - Demonstrate a DirectAccess Multisite Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-multisite/test-lab-guide-demonstrate-a-directaccess-multisite-deployment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn about extending the Test Lab Guide - Demonstrate DirectAccess Single Server Setup with Mixed IPv4 and IPv6 to demonstrate Remote Access in a multisite scenario.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 0b00c95e-24d8-de1e-c262-699f9d1bb178
document_version_independent_id: df4f2b62-2da5-21e4-9bfb-87a90adeba80
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/Test-Lab-Guide-Demonstrate-a-DirectAccess-Multisite-Deployment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-multisite/test-lab-guide-demonstrate-a-directaccess-multisite-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/Test-Lab-Guide-Demonstrate-a-DirectAccess-Multisite-Deployment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 3187b20e-3f0a-386f-1f59-f46a56829bd4
---

# Test Lab Guide - Demonstrate a DirectAccess Multisite Deployment | Microsoft Learn

Remote Access is a server role in the Windows Server 2016, Windows Server 2012 R2 and Windows Server 2012 operating systems that enables remote users to securely access internal network resources using DirectAccess or RRAS VPN. This guide contains step-by-step instructions for extending the [Test Lab Guide: Demonstrate DirectAccess Single Server Setup with Mixed IPv4 and IPv6](https://go.microsoft.com/fwlink/p/?LinkId=237004) to demonstrate Remote Access in a multisite scenario.

Deploying Remote Access in a multisite scenario enables you to configure Remote Access servers in geographically diverse locations. Previously, remote users were required to always connect to the corporate network through a particular DirectAccess server. With Windows Server 2016, Windows Server 2012 R2 or Windows Server 2012 and Windows 10 or Windows 8, you can configure entry points for each geographic location in your deployment. Each entry point can be a single Remote Access server or a cluster of Remote Access servers. Remote users have the option to connect to any of the organization's Remote Access entry points. For example, if a remote user usually connects to the Remote Access entry point located in Asia, but then goes on a business trip to Europe, the client computer automatically connects to the closest Remote Access entry point.

## About this guide

This guide contains instructions for configuring and demonstrating Remote Access using nine servers and three client computers. The completed Remote Access multisite test lab simulates an intranet, the Internet, and a home network and demonstrates Remote Access functionality in different Internet connection scenarios.

Important

This lab is a proof of concept using the minimum number of computers. The configuration detailed in this guide is for test lab purposes only, and is not to be used in a production environment.