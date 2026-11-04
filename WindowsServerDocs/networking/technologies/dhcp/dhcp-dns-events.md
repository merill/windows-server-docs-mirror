---
layout: Conceptual
title: DHCP Logging Events for DNS Record Registrations | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/dhcp/dhcp-dns-events
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides information about DHCP server logging events in Windows Server 2016.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 1346caa3-4785-27e2-e1ca-986f57a4c663
document_version_independent_id: 7c9329a2-d778-9b3d-0e4a-4210eaaeae7e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/dhcp/dhcp-dns-events.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/dhcp/dhcp-dns-events
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/dhcp/dhcp-dns-events.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 19ae76f9-9b85-51a9-47f8-e1aa31e0eb19
---

# DHCP Logging Events for DNS Record Registrations | Microsoft Learn

DHCP server event logs now provide detailed information about DNS registration failures.

Note

In many cases, the reason for DNS record registration failures by DHCP servers is that a DNS Reverse-Lookup Zone is either configured incorrectly or not configured at all.

The following new DHCP events assist you to easily identify when DNS registrations are failing because of a misconfigured or missing DNS Reverse-Lookup Zone.

| ID | Event | Value |
| --- | --- | --- |
| 20317 | DHCPv4.ForwardRecordDNSFailure | Forward record registration for IPv4 address %1 and FQDN %2 failed with error %3. This is likely to be because the forward lookup zone for this record does not exist on the DNS server. |
| 20318 | DHCPv4.ForwardRecordDNSTimeout | Forward record registration for IPv4 address %1 and FQDN %2 failed with error %3. |
| 20319 | DHCPv4.PTRRecordDNSFailure | PTR record registration for IPv4 address %1 and FQDN %2 failed with error %3. This is likely to be because the reverse lookup zone for this record does not exist on the DNS server. |
| 20320 | DHCPv4.PTRRecordDNSTimeout | PTR record registration for IPv4 address %1 and FQDN %2 failed with error %3. |
| 20321 | DHCPv6.ForwardRecordDNSFailure | Forward record registration for IPv6 address %1 and FQDN %2 failed with error %3. This is likely to be because the forward lookup zone for this record does not exist on the DNS server. |
| 20322 | DHCPv6.ForwardRecordDNSTimeout | Forward record registration for IPv6 address %1 and FQDN %2 failed with error %3. |
| 20323 | DHCPv6.PTRRecordDNSFailure | PTR record registration for IPv6 address %1 and FQDN %2 failed with error %3. This is likely to be because the reverse lookup zone for this record does not exist on the DNS server. |
| 20324 | DHCPv6.PTRRecordDNSTimeout | PTR record registration for IPv6 address %1 and FQDN %2 failed with error %3. |
| 20325 | DHCPv4.ForwardRecordDNSError | PTR record registration for IPv4 address %1 and FQDN %2 failed with error %3 (%4). |
| 20326 | DHCPv6.ForwardRecordDNSError | Forward record registration for IPv6 address %1 and FQDN %2 failed with error %3 (%4) |
| 20327 | DHCPv6.PTRRecordDNSError | PTR record registration for IPv6 address %1 and FQDN %2 failed with error %3 (%4). |