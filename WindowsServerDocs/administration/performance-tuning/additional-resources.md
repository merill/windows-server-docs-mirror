---
layout: Conceptual
title: Additional server performance tuning resources | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/additional-resources
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Additional server performance tuning resources
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b0e3081b-aa7b-004b-04ab-8f20b0ce34c7
document_version_independent_id: 7637c84d-8513-a518-a029-e8e12816ba78
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/additional-resources.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/additional-resources
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/additional-resources.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: e0ffe420-7f2d-6af5-7152-5491e72722c0
---

# Additional server performance tuning resources | Microsoft Learn

Use the links in this topic to learn more about the concepts that were discussed in this tuning guide.

## Microsoft Windows Server Websites

- [Windows Server Catalog](https://www.windowsservercatalog.com/)
- [Windows Sysinternals](/en-us/sysinternals/)
- [Transaction Processing Performance Council](http://www.tpc.org/)
- [Windows Assessment and Deployment Kit](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit)

## Power Management Tuning Resources

- [Power Policy Configuration and Deployment in Windows](/en-us/windows-hardware/customize/power-settings/configure-processor-power-management-options)
- [Using PowerCfg to Evaluate System Energy Efficiency](/en-us/previous-versions/windows/it-pro/windows-vista/cc748940%28v=ws.10%29)
- [Interrupt-Affinity](/en-us/windows-hardware/drivers/kernel/interrupt-affinity-and-priority)

## Networking Subsystem Tuning Resources

- [Scalable Networking: Eliminating the Receive Processing Bottleneck—Introducing RSS](https://download.microsoft.com/download/5/D/6/5D6EAF2B-7DDF-476B-93DC-7CF0072878E6/NDIS_RSS.doc)
- [Windows Filtering Platform](/en-us/windows-hardware/drivers/network/porting-packet-processing-drivers-and-apps-to-wfp)
- [Networking Deployment Guide: Deploying High-Speed Networking Features](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg162681%28v=ws.10%29)

## Storage Subsystem Tuning Resources

- [Disk Subsystem Performance Analysis for Windows](https://download.microsoft.com/download/e/b/a/eba1050f-a31d-436b-9281-92cdfeae4b45/subsys_perf.doc) (Parts of this document are out of date, but many of the general observations and guidelines captured are still accurate and relevant.)

## File Server Tuning Resources

- [Performance Tuning Guidelines for Microsoft Services for Network File System](/en-us/previous-versions/tn-archive/bb463205%28v=technet.10%29)
- [\[MS-FSSO\]: File Access Services System Overview](https://download.microsoft.com/download/5/0/1/501ED102-E53F-4CE0-AA6B-B0F93629DDC6/Windows/%5bMS-FSSO%5d.pdf)
- [How to disable the TCP autotuning diagnostic tool](https://support.microsoft.com/kb/967475)

## Active Directory Server Tuning Resources

- [Active Directory Performance](/en-us/previous-versions/dn567654%28v=vs.85%29)
- [How to configure Active Directory diagnostic event logging in Windows Server 2003 and in Windows 2000 Server](https://support.microsoft.com/kb/314980)

## Virtualization Server Tuning Resources

- [What's New in Hyper-V in Windows Server 2016](../../virtualization/hyper-v/what-s-new-in-hyper-v-on-windows)
- [Hyper-V Dynamic Memory Configuration Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff817651%28v=ws.10%29)
- [NUMA Node Balancing](/en-us/archive/blogs/winserverperformance/numa-node-balancing)
- [Hyper-V WMI Provider](/en-us/previous-versions/windows/desktop/virtual/windows-virtualization-portal)
- [Hyper-V WMI Classes](/en-us/previous-versions/windows/desktop/virtual/virtualization-wmi-classes)
- [About Virtual Machines and Guest Operating Systems](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794868%28v=ws.10%29)
- [Optimizing and Troubleshooting Hyper-V Storage](/en-us/archive/blogs/microsoft_press/new-book-optimizing-and-troubleshooting-hyper-v-storage)
- [Optimizing and Troubleshooting Hyper-V Networking](https://blogs.msdn.com/b/microsoft_press/archive/2013/07/12/rtm-d-today-optimizing-and-troubleshooting-hyper-v-networking.aspx)

## Print Server Tuning Resources

- [Print Server Scalability and Capacity Planning](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn554243%28v=ws.11%29)

## Server Workload Tuning Resources

Note

Microsoft Server Performance Advisor is no longer available. Please use the resources in this section instead.

- [Performance Tuning for NTttcp](/en-us/previous-versions/dn567663%28v=vs.85%29)
- [Ttcp](http://en.wikipedia.org/wiki/Ttcp)
- [How to use NTttcp to Test Network Performance](/en-us/samples/browse/?redirectedfrom=TechNet-Gallery)
- [Using the File Server Capacity Tool](/en-us/previous-versions/dn567658%28v=vs.85%29)
- [Using the SPECsfs2008 File Server](/en-us/previous-versions/dn567653%28v=vs.85%29)
- [Performance Tuning for the Sales and Distribution Workload](/en-us/previous-versions/dn567646%28v=vs.85%29)
- [Performance Tuning for Online Transaction Processing (OLTP)](/en-us/previous-versions/dn567642%28v=vs.85%29)
- [How to: Configure SQL Server to Use Soft-NUMA](/en-us/sql/database-engine/configure-windows/soft-numa-sql-server)
- [How to: Map TCP/IP Ports to NUMA Nodes](/en-us/sql/database-engine/configure-windows/map-tcp-ip-ports-to-numa-nodes-sql-server)
- [ALTER SERVER CONFIGURATION (Transact-SQL)](/en-us/sql/t-sql/statements/alter-server-configuration-transact-sql)

## Performance Tuning Guidelines for previous versions of Windows Server

Use the performance tuning guidelines to improve performance for older versions of Windows Server.

Here's a list of performance tuning guidelines for previous versions of Windows Server:

- [Performance Tuning Guidelines for Windows Server 2012 R2](https://www.microsoft.com/download/details.aspx?id=51960)
- [Performance Tuning Guidelines for Windows Server 2012](https://download.microsoft.com/download/0/0/B/00BE76AF-D340-4759-8ECD-C80BC53B6231/performance-tuning-guidelines-windows-server-2012.docx)
- [Performance Tuning Guidelines for Windows Server 2008 R2](https://download.microsoft.com/download/6/B/2/6B2EBD3A-302E-4553-AC00-9885BBF31E21/Perf-tun-srv-R2.docx)