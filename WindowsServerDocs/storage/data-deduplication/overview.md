---
layout: Conceptual
title: Data Deduplication Overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/data-deduplication/overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: 'Learn more about: Data Deduplication Overview'
ms.topic: overview
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-20T00:00:00.0000000Z
locale: en-us
document_id: a77853e9-1393-cf67-c5bc-ed3c4dd74980
document_version_independent_id: a7b0344a-5803-7dbf-1b8d-e096899d86e9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/data-deduplication/overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/data-deduplication/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/data-deduplication/overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://authoring-docs-microsoft.poolparty.biz/devrel/01a89bec-e73f-4ce0-a00a-ae34ad62e5fe
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://authoring-docs-microsoft.poolparty.biz/devrel/50038ab9-5431-4515-9dfc-c24291ef4fce
platformId: 4258227f-e1e0-5eee-4649-555e99095b2b
---

# Data Deduplication Overview | Microsoft Learn

## What is Data Deduplication?

Data Deduplication, often called "dedupe" for short, is a feature that can help reduce the impact of redundant data on storage costs. When enabled, Data Deduplication optimizes free space on a volume by examining the data on the volume by looking for duplicated portions on the volume. Duplicated portions of the volume's dataset are stored once and are (optionally) compressed for additional savings. Data Deduplication optimizes redundancies without compromising data fidelity or integrity. More information about how Data Deduplication works can be found in the '[How does Data Deduplication work?](understand#how-does-dedup-work)' section of the [Understanding Data Deduplication](understand) page.

Important

[KB4025334](https://support.microsoft.com/kb/4025334) contains a roll up of fixes for Data Deduplication, including important reliability fixes, and we strongly recommend installing it when using Data Deduplication with Windows Server 2016 and Windows Server 2019.

## Why is Data Deduplication useful?

Data Deduplication helps storage administrators reduce costs that are associated with duplicated data. Large datasets often have **a lot** of duplication, which increases the costs of storing the data. For example:

- User file shares may have many copies of the same or similar files.
- Virtualization guests might be almost identical from VM-to-VM.
- Backup snapshots might have minor differences from day to day.

The space savings that you can gain from Data Deduplication depend on the dataset or workload on the volume. Datasets that have high duplication could see optimization rates of up to 95%, or a 20x reduction in storage utilization. The following table highlights typical deduplication savings for various content types:

| Scenario | Content | Typical space savings |
| --- | --- | --- |
| User documents | Office documents, photos, music, videos, etc. | 30-50% |
| Deployment shares | Software binaries, cab files, symbols, etc. | 70-80% |
| Virtualization libraries | ISOs, virtual hard disk files, etc. | 80-95% |
| General file share | All the above | 50-60% |

Note

If you're just looking to free up space on a volume, consider using Azure File Sync with cloud tiering enabled. This allows you to cache your most frequently accessed files locally and tier your least frequently accessed files to the cloud, saving local storage space while maintaining performance. For details, see [Planning for an Azure File Sync deployment](/en-us/azure/storage/files/storage-sync-files-planning).

## When can Data Deduplication be used?

| Scenario illustration | Description |
| --- | --- |
| ![Illustration of file servers.](media/overview-clustered-gpfs.png) | **General purpose file servers**: General purpose file servers are general use file servers that might contain any of the following types of shares: <br>- Team shares<br>- User home folders<br>- [Work folders](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265974%28v=ws.11%29)<br>- Software development shares<br><br>General purpose file servers are a good candidate for Data Deduplication because multiple users tend to have many copies or versions of the same file. Software development shares benefit from Data Deduplication because many binaries remain essentially unchanged from build to build. |
| ![Illustration of VDI servers.](media/overview-vdi.png) | **Virtual Desktop Infrastructure (VDI) deployments**: VDI servers, such as [Remote Desktop Services](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725560%28v=ws.11%29), provide a lightweight option for organizations to provision desktops to users. There are many reasons for an organization to rely on such technology: <br>- **Application deployment**: You can quickly deploy applications across your enterprise. This is especially useful when you have applications that are frequently updated, infrequently used, or difficult to manage.<br>- **Application consolidation**: When you install and run applications from a set of centrally managed virtual machines, you eliminate the need to update applications on client computers. This option also reduces the amount of network bandwidth that is required to access applications.<br>- **Remote Access**: Users can access enterprise applications from devices such as home computers, kiosks, low-powered hardware, and operating systems other than Windows.<br>- **Branch office access**: VDI deployments can provide better application performance for branch office workers who need access to centralized data stores. Data-intensive applications sometimes do not have client/server protocols that are optimized for low-speed connections.<br><br> VDI deployments are great candidates for Data Deduplication because the virtual hard disks that drive the remote desktops for users are essentially identical. Additionally, Data Deduplication can help with the so-called *VDI boot storm*, which is the drop in storage performance when many users simultaneously sign in to their desktops to start the day. |
| ![Illustration of backup applications.](media/overview-backup.png) | **Backup targets, such as virtualized backup applications**: Backup applications, such as [Microsoft Data Protection Manager (DPM)](/en-us/previous-versions/system-center/system-center-2012-R2/hh758173%28v=sc.12%29), are excellent candidates for Data Deduplication because of the significant duplication between backup snapshots. |
| ![Illustration of other workloads.](media/overview-other.png) | **Other workloads**: [Other workloads may also be excellent candidates for Data Deduplication](install-enable#enable-dedup-candidate-workloads). |