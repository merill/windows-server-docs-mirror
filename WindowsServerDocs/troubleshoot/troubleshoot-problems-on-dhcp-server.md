---
layout: Conceptual
title: Troubleshoot problems on the DHCP server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/troubleshoot/troubleshoot-problems-on-dhcp-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: troubleshoot
ms.update-cycle: 1095-days
description: Find out how to troubleshoot problems on the DHCP server and collect data.
ms.date: 2023-09-27T00:00:00.0000000Z
ms.topic: troubleshooting
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 70ed7e4c-0e62-887f-e3aa-db50bcb9d2b9
document_version_independent_id: 4d40f939-2773-a34b-ff7b-4f9d8e29878b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/troubleshoot/troubleshoot-problems-on-dhcp-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../networking/toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: troubleshoot/troubleshoot-problems-on-dhcp-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/troubleshoot/troubleshoot-problems-on-dhcp-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6bbf1dbc-14ef-289b-0bfb-eb2f0d29ba9b
---

# Troubleshoot problems on the DHCP server | Microsoft Learn

This article discusses how to troubleshoot problems that occur on the DHCP server.

## Troubleshooting checklist

Check the following settings:

- The DHCP server service is started and running. To check this setting, run the `net start` command, and look for **DHCP Server**.
- The DHCP server is authorized. See [Windows DHCP Server Authorization in Domain Joined Scenario](/en-us/openspecs/windows_protocols/ms-dhcpe/56f8870b-a7c1-4db1-8a86-f69079fe5077).
- Verify that IP address leases are available in the DHCP server scope for the subnet the DHCP client is on. To verify availability, see the statistic for the appropriate scope in the DHCP server management console.
- Check whether any BAD\_ADDRESS listings can be found in Address Leases.
- Check whether any devices on the network have static IP addresses that haven't been excluded from the DHCP scope.
- Verify that the DHCP server binds to at least one IP address, and that this IP address is within the subnet of the scopes from which IP addresses must be leased out, unless using DHCP relay. To do this verification, run the `Get-DhcpServerv4Binding` or `Get-DhcpServerv6Binding` cmdlet. Server connection bindings are configured in the DHCP server management console under **IPv4 / IPv6 Advanced Properties**.
- Verify that only the DHCP server is listening on UDP port 67 and 68 by running the `netstat -anb` command. No other process or other services, such as WDS or PXE, should occupy these ports.
- Verify that the DHCP server IPsec exemption is added if you're dealing with an IPsec-deployed environment.
- Verify that the relay agent IP address can be pinged from the DHCP server.
- Enumerate and check configured DHCP policies and filters.

## Data collection

### DHCP Server log

The DHCP Server debug logs provide more information about the IP address lease assignment and the DNS dynamic updates that are done by the DHCP server. These logs by default are located in %windir%\System32\Dhcp. For more information, see [Analyze DHCP Server Log Files](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd183591%28v=ws.10%29).

### Network trace

A correlating network trace may indicate what the DHCP server was doing at the time that the event was logged. To create such a trace by using the [Windows Troubleshooting Tools (TSS)](https://aka.ms/getTSS), follow the instructions at [DHCP troubleshooting guidance - Data collection](/en-us/troubleshoot/windows-server/networking/troubleshoot-dhcp-guidance#data-collection).