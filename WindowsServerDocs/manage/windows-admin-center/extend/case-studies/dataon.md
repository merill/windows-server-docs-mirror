---
layout: Conceptual
title: Windows Admin Center SDK Case Study - DataON | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/case-studies/dataon
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Windows Admin Center SDK Case Study - DataON
ms.topic: partner-tools
author: robinharwood
ms.author: roharwoo
ms.date: 2019-01-11T00:00:00.0000000Z
locale: en-us
document_id: a558d858-5d5d-3dce-0a88-35ca57f31787
document_version_independent_id: 86330d35-d7f6-4293-b055-f34782523048
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/case-studies/dataon.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/case-studies/dataon
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/case-studies/dataon.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 51d26725-169d-2250-4206-f75e88c0b14e
---

# Windows Admin Center SDK Case Study - DataON | Microsoft Learn

## Integrated monitoring and management for Microsoft hyper-converged infrastructure

[DataON](http://www.dataonstorage.com/) is the industry-leading provider of hyper-converged infrastructure and storage systems optimized for Microsoft Windows Server environments. Exclusively focused on delivering Microsoft applications, virtualization, data protection, and hybrid cloud services, it has over 650 enterprise deployments and over 120PB of Storage Spaces Direct deployments.

[DataON's MUST](http://www.dataonstorage.com/must) extension for Windows Admin Center is a prime example of the value that integrating two complementary products can deliver to customers, bringing monitoring and management and end-to-end insight into hardware and software together across an entire cluster in a unified experience.

> 
> “We've taken our standalone MUST visibility, monitoring, and management tool and enabled it to work within Windows Admin Center. Customers will benefit from the expanded capabilities that MUST provides, and the combination of MUST and Windows Admin Center from a single console will provide the ultimate management experience for Windows Server-based infrastructure.”
> 
> -- Howard Lo, Vice President of Sales and Marketing, DataON

The MUST extension extends the functionality of Windows Admin Center by providing features such as:

- **Historic Data Reporting** – Provides real-time and monthly dashboards of your system performance data including IOPS, latency, throughput on your cluster, storage pool, volume, and nodes.
- **Disk Mapping** – MUST displays the device types and components in each of the nodes, providing a clear disk map of your entire node. It shows the number of disks, disk type, location and slot of each drive, and disk health status.
- **System Alerts** – Leverages Windows Health Service faults to identify hardware failures, configuration issues, and resource saturation. It also provides a multi-level assessment of specific locations, fault descriptions, and recovery actions. You can also leverage third-party SNMP monitoring traps to alert you when you need disk or hardware replacements.
- **SAN-like Call Home Service** – Prompted by system alerts, administrators can have automated email alerts sent to key contacts.

![Screenshot of the Windows Admin Center showing the disk mapping in the DataON MUST extension.](../../media/extend-case-study-dataon/dataon-1.png)*Disk mapping in the DataON MUST extension for Windows Admin Center*

> 
> “It's great that Windows Admin Center allows for extensions such as DataON MUST so I can use both tools within the same console, and I like how seamless that integration is. Windows Admin Center and DataON MUST together really does allow us to be more efficient and saves our team a ton of time. It allows us to achieve our administrator tasks a lot quicker than what we had before."
> 
> -- Matt Roper, Facilitator of Technology Support Services, Cherokee County (GA) School District

![Screenshot of the Windows Admin Center showing the Alert Services in the DataON MUST extension.](../../media/extend-case-study-dataon/dataon-2.png)*Alert Services in the DataON MUST extension for Windows Admin Center*

> 
> “MUST has been very valuable and was a big selling point. To us, it demonstrated a commitment from DataON to support Microsoft hyper-converged infrastructure. The inclusion of MUST with their S2D appliance is what completes the solution with Storage Spaces Direct as a viable SAN replacement.” 
> 
> -- Benjamin Clements, President, Strategic Online Systems, Inc.