---
layout: Conceptual
title: Troubleshooting Domain Name System (DNS) issues | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/dns/troubleshoot/troubleshoot-dns-data-collection
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This article introduces how to collect data when DNS issues occur.
ms.topic: troubleshooting-general
ms.author: roharwoo
ms.date: 2019-08-08T00:00:00.0000000Z
author: robinharwood
locale: en-us
document_id: 82d79b72-a842-d8ee-f4fd-d4c63d721b11
document_version_independent_id: 70d52a80-ad89-1c4f-07ec-a8caced2815e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/dns/troubleshoot/troubleshoot-dns-data-collection.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/dns/troubleshoot/troubleshoot-dns-data-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/dns/troubleshoot/troubleshoot-dns-data-collection.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: 7d936194-3a4a-5be2-e0b2-6f638691b876
---

# Troubleshooting Domain Name System (DNS) issues | Microsoft Learn

Domain Name resolution issues can be broken down into client-side and server-side issues. In general, you should start with client-side troubleshooting unless you determine during the scoping phase that the issue is definitely occurring on the server side.

- [Troubleshooting DNS clients](troubleshoot-dns-client)
- [Troubleshooting DNS Servers](troubleshoot-dns-server)

## Data Collection

We recommend that you simultaneously collect data on both the client and server sides when the issue occurs. However, depending on the actual issue, you can start your collection at a single data set on either the DNS client or DNS server.

To collect a Windows Networking Diagnostic from an affected client and its configured DNS server, follow these steps:

1. Start network captures on the client and server:

    ```cmd
    netsh trace start capture=yes tracefile=c:\%computername%_nettrace.etl
    ```
2. Clear the DNS cache on the DNS client by running the following command:

    ```cmd
    ipconfig /flushdns
    ```
3. Reproduce the issue.
4. Stop and save traces:

    ```cmd
    netsh trace stop
    ```
5. Save the Nettrace.cab files from each computer. This information will be helpful when you contact Microsoft Support.