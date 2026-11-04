---
layout: Conceptual
title: DNS for AD DS Owner Role | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/assigning-the-dns-for-ad-ds-owner-role
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Information about the DNS for AD DS Owner role.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 3b278b39-8437-1886-ab8e-264370673776
document_version_independent_id: 10a3d7bb-4673-c53d-1310-55204018af60
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/deploy/Assigning-the-DNS-for-AD-DS-Owner-Role.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/deploy/assigning-the-dns-for-ad-ds-owner-role
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/deploy/Assigning-the-DNS-for-AD-DS-Owner-Role.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: cc8ba3ed-f13a-b6fe-3e9a-0e2b2328bfb4
---

# DNS for AD DS Owner Role | Microsoft Learn

The DNS for AD DS owner of the forest is a person (or group of people) who is responsible for overseeing the deployment of the DNS for AD DS infrastructure and for making sure that (if necessary) domain names are registered with the proper Internet authorities. The forest owner assigns a Domain Name System (DNS) for Active Directory Domain Services (AD DS) owner for the forest.

The DNS for AD DS owner is responsible for the DNS for AD DS design for the forest. If your organization is currently operating a DNS Server service, the DNS designer for the existing DNS Server service works with the DNS for AD DS owner to delegate the forest root DNS name to DNS servers running on domain controllers.

The DNS for AD DS owner for the forest also maintains contact with the Dynamic Host Configuration Protocol (DHCP) group and the DNS group of the organization and coordinates the plans of the individual DNS owners of each domain in the forest (if any) with these groups. The DNS owner for the forest ensures that the DHCP and DNS groups are involved in the DNS for AD DS design process so that each group is aware of the DNS design plan and can provide input early.