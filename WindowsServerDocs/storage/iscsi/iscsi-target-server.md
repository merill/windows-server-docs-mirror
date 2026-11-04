---
layout: Conceptual
title: iSCSI Target Server Overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/iscsi/iscsi-target-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: 'Learn more about: iSCSI Target Server overview'
TOCTitle: iSCSI Target Server
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2018-09-11T00:00:00.0000000Z
locale: en-us
document_id: 4521dea9-599e-ce9f-71d4-74bb3015c736
document_version_independent_id: e0eb1a5e-a76b-521a-d99c-8b12e8f77ef9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/iscsi/iscsi-target-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/iscsi/iscsi-target-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/iscsi/iscsi-target-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b5d88553-1a5f-73b4-3384-8dea904c4edb
---

# iSCSI Target Server Overview | Microsoft Learn

This topic provides a brief overview of iSCSI Target Server, a role service in Windows Server that enables you to make storage available via the iSCSI protocol. This is useful for providing access to storage on your Windows server for clients that can't communicate over the native Windows file sharing protocol, SMB.

iSCSI Target Server is ideal for the following:

- **Network and diskless boot** By using boot-capable network adapters or a software loader, you can deploy hundreds of diskless servers. With iSCSI Target Server, the deployment is fast. In Microsoft internal testing, 256 computers deployed in 34 minutes. By using differencing virtual hard disks, you can save up to 90% of the storage space that was used for operating system images. This is ideal for large deployments of identical operating system images, such as on virtual machines running Hyper-V or in high-performance computing (HPC) clusters.
- **Server application storage** Some applications require block storage. iSCSI Target Server can provide these applications with continuously available block storage. Because the storage is remotely accessible, it can also consolidate block storage for central or branch office locations.
- **Heterogeneous storage** iSCSI Target Server supports non-Microsoft iSCSI initiators, making it easy to share storage on servers in a mixed software environment.
- **Development, test, demonstration, and lab environments** When iSCSI Target Server is enabled, a computer running the Windows Server operating system becomes a network-accessible block storage device. This is useful for testing applications prior to deployment in a storage area network (SAN).

## Block storage requirements

Enabling iSCSI Target Server to provide block storage leverages your existing Ethernet network. No additional hardware is needed. If high availability is an important criterion, consider setting up a high-availability cluster. You need shared storage for a high-availability cluster—either hardware for Fibre Channel storage or a serial attached SCSI (SAS) storage array.

If you enable guest clustering, you need to provide block storage. Any servers running Windows Server software with iSCSI Target Server can provide block storage.