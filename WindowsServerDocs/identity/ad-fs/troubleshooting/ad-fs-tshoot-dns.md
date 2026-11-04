---
layout: Conceptual
title: AD FS Troubleshooting - DNS Resolution | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-dns
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: This article describes how to troubleshoot Domain Name System aspects of Active Directory Federation Services.
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: troubleshooting-general
locale: en-us
document_id: 218f0e70-9934-3b99-d7b4-d266e4db3bac
document_version_independent_id: 318d4e01-0696-fb50-b34b-4859dc89670d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-dns.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/troubleshooting/ad-fs-tshoot-dns
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-dns.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 8f8f4403-e5d6-624e-2edb-2bfac5812721
---

# AD FS Troubleshooting - DNS Resolution | Microsoft Learn

If Active Directory Federation Services (AD FS) isn't working or responding, one of the first things to check is Domain Name System (DNS) name resolution. Basic tests determine if the AD FS or Web Application Proxy (WAP) servers are found on your network. For internal users, these tests should resolve to the AD FS servers security token service (STS). For external users, these tests should resolve to the WAP servers.

The remainder of this article shows how to use command-line tools to do some quick name resolution checks.

## Ping test

A ping test verifies IP-level connectivity to another TCP/IP computer by sending Internet Control Message Protocol (ICMP) Echo Request messages. The receipt of corresponding Echo Reply messages appears, along with round-trip times. For more information, see [Ping](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff961503%28v=ws.11%29).

Note

Some organizations block this port on their servers. You might get a **Request timed out** response.

To use a ping test:

1. Open a command prompt.
2. Enter `ping <name of AD FS server>`.

    Example: `ping sts.contoso.com`

A reply from the server appears.

![Screenshot that shows a ping sample.](media/ad-fs-tshoot-dns/dns1.png)

## NSLookup

NSLookup shows information that you can use to diagnose DNS infrastructure. For more information, see [NSLookup](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc725991%28v=ws.11%29).

To use NSLookup:

1. Open a command prompt.
2. Enter `nslookup <name of AD FS server>`.

    Example: `nslookup sts.contoso.com`

The DNS information for the server appears.

![Screenshot that shows NSLookup.](media/ad-fs-tshoot-dns/dns2.png)

## Tracert

Tracert determines the path taken to a destination by sending an ICMP Echo Request or ICMPv6 messages to the destination with incrementally increasing Time to Live (TTL) field values. For more information, see [Tracert](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff961507%28v=ws.11%29).

To use tracert:

1. Open a command prompt.
2. Enter `tracert <name of AD FS server>`.

    Example: `tracert sts.contoso.com`

The destination path used to reach the server appears.

![Screenshot that shows tracert.](media/ad-fs-tshoot-dns/dns3.png)