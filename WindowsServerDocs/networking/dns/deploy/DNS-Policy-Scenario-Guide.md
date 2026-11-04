---
layout: Conceptual
title: DNS Policy Scenario Guide | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/dns/deploy/dns-policy-scenario-guide
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to use DNS policy to control how a DNS server processes name resolution queries based on different parameters that you define in policies.
ms.topic: example-scenario
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 5b8df6bf-bf98-2b50-2e7d-5b1989538a8a
document_version_independent_id: bbff85f0-a45b-24f2-1dd4-ad0f21eea97f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/dns/deploy/DNS-Policy-Scenario-Guide.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/dns/deploy/dns-policy-scenario-guide
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/dns/deploy/DNS-Policy-Scenario-Guide.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 8d25c256-55fd-da34-0cde-1eac500c42a5
---

# DNS Policy Scenario Guide | Microsoft Learn

This guide is intended for use by DNS, network, and systems administrators.

DNS Policy is a new feature for DNS in Windows Server® 2016. You can use this guide to learn how to use DNS policy to control how a DNS server processes name resolution queries based on different parameters that you define in policies.

This guide contains DNS policy overview information, as well as specific DNS policy scenarios that provide you with instructions on how to configure DNS server behavior to accomplish your goals, including geo-location based traffic management for primary and secondary DNS servers, application high availability, split-brain DNS, and more.

This guide contains the following sections.

- [DNS Policies Overview](dns-policies-overview)
- [Use DNS Policy for Geo-Location Based Traffic Management with Primary Servers](primary-geo-location)
- [Use DNS Policy for Geo-Location Based Traffic Management with Primary-Secondary Deployments](primary-secondary-geo-location)
- [Use DNS Policy for Intelligent DNS Responses Based on the Time of Day](dns-tod-intelligent)
- [DNS Responses Based on Time of Day with an Azure Cloud App Server](dns-tod-azure-cloud-app-server)
- [Use DNS Policy for Split-Brain DNS Deployment](split-brain-dns-deployment)
- [Use DNS Policy for Split-Brain DNS in Active Directory](dns-sb-with-ad)
- [Use DNS Policy for Applying Filters on DNS Queries](apply-filters-on-dns-queries)
- [Use DNS Policy for Application Load Balancing](app-lb)
- [Use DNS Policy for Application Load Balancing With Geo-Location Awareness](app-lb-geo)