---
layout: Conceptual
title: Get Started with Software Inventory Logging | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/software-inventory-logging/get-started-with-software-inventory-logging
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Describes how to install and start using Software Inventory Logging
ms.topic: get-started
author: robinharwood
ms.author: roharwoo
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a66f1e60-ad90-aff4-62b1-f66bbe73f19c
document_version_independent_id: 9f2ae9a2-0487-31ba-7ae3-68270023e6d1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/software-inventory-logging/get-started-with-software-inventory-logging.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/software-inventory-logging/get-started-with-software-inventory-logging
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/software-inventory-logging/get-started-with-software-inventory-logging.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f913e0df-c1a0-2268-4dc2-09d9527f1513
---

# Get Started with Software Inventory Logging | Microsoft Learn

Software Inventory Logging collects Microsoft software inventory data on a per server basis. Before using Software Inventory Logging with Windows Server 2012 R2, make sure that Windows Update [KB 3000850](https://support.microsoft.com/kb/3000850) and [KB 3060681](https://support.microsoft.com/kb/3060681) are installed on each system that will be inventoried. No Windows Update is required for Windows Server 2016. Also, if you want to use SIL's capability to forward data to an aggregation server, be sure you have SSL certificates valid for your network.

## Feature description

Software Inventory Logging in Windows Server is a feature with a simple set of PowerShell cmdlets that help server administrators retrieve a list of the Microsoft software that is installed on their servers. It also provides the capability to collect and forward this data periodically over the network to a target web server, using the HTTPS protocol, for aggregation. Managing the feature, primarily for hourly collection and forwarding, is also done with PowerShell commands.

Note

An aggregation server running a web service can be separately configured. Learn more about [Software Inventory Logging Aggregator](software-inventory-logging-aggregator).

Important

None of the data collected by Software Inventory Logging is sent to Microsoft as part of the feature's functionality.

## Practical applications

Software Inventory Logging is intended to reduce the operational costs of retrieving accurate information regarding the Microsoft software deployed locally on a server, but especially across many servers in an IT environment (assuming it is deployed and enabled across the IT environment). The ability to forward this data to an aggregation server (if set up separately by an IT administrator), allows the data to be collected in one place by a uniform, automatic process. While this can also be achieved by querying the interfaces directly, Software Inventory Logging, by employing a forwarding (over the network) architecture initiated by each server, can overcome machine discovery challenges typical for many software inventory and asset management scenarios. SSL is used to secure data forwarded over HTTPS to an administrator's aggregation server. Having the data in one place (on one server) makes the data easier to analyze, manipulate and report on. It is important to note that none of this data is sent to Microsoft as part of the feature functionality. Software Inventory Logging data and functionality is meant for the sole use of the server software's licensed owner and administrators.

Software Inventory Logging can assist server administrators in performing the following tasks:

- Retrieving software and server inventory information from Windows Servers, remotely and on-demand.
- Aggregating software and server inventory information for a wide variety of software asset management scenarios by enabling each server's Software Inventory Logging feature and choosing a web server target URI, and certificate thumbprint for authentication.