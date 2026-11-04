---
layout: Conceptual
title: Performance Tuning for HTTP 1.1/2 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/role/web-server/http-performance
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Performance tuning recommendations for HTTP 1.1/2
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 5725d4c2-4f20-a017-61ab-32c231d1489f
document_version_independent_id: fad930f3-8391-7f0d-7349-7f758b61f2f9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/role/web-server/http-performance.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/role/web-server/http-performance
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/role/web-server/http-performance.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: 3541bb8e-edab-343b-7164-a056b35ffa8d
---

# Performance Tuning for HTTP 1.1/2 | Microsoft Learn

HTTP/2 is meant to improve performance on the client side (e.g., page load time on a browser). On the server, it may represent a slight increase in CPU cost. Whereas the server no longer requires a single TCP connection for every request, some of that state will now be kept in the HTTP layer. Furthermore, HTTP/2 has header compression, which represents additional CPU load.

Some situations require an HTTP/1.1 fallback (resetting the HTTP/2 connection and instead establishing a new connection to use HTTP/1.1). In particular, TLS renegotiation and HTTP authentication (other than Basic and Digest) require HTTP/1.1 fallback. Even though this adds overhead, these operations already imply some delay and so are not particularly performance-sensitive.

## Additional References

- [Web Server performance tuning](./)
- [IIS 10.0 performance tuning](tuning-iis-10)