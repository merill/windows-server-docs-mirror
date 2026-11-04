---
layout: Conceptual
title: iSCSI target boot overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/iscsi/iscsi-boot-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: 'Learn more about: iSCSI target boot overview'
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2018-09-11T00:00:00.0000000Z
locale: en-us
document_id: 13dc5b01-2374-8f65-9825-64bc0c894854
document_version_independent_id: d0613293-3c71-2326-9b8b-dddcfb170ed9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/iscsi/iscsi-boot-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/iscsi/iscsi-boot-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/iscsi/iscsi-boot-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 27e5bdfe-cfcc-1b6c-23ef-13d6a9d36ee9
---

# iSCSI target boot overview | Microsoft Learn

> 
> \*\*

iSCSI Target Server in Windows Server can boot hundreds of computers from a single operating system image that is stored in a centralized location. This improves efficiency, manageability, availability, and security.

## Feature description

By using differencing virtual hard disks (VHDs), you can use a single operating system image (the "master image") to boot up to 256 computers. As an example, let's assume that you deployed Windows Server with an operating system image of approximately 20 GB, and you used two mirrored disk drives to act as the boot volume. You would have needed approximately 10 TB of storage for only the operating system image to boot 256 computers. With iSCSI Target Server, you will use 40 GB for the operating system base image, and 2 GB for differencing virtual hard disks per server instance, totaling 552 GB for the operating system images. This provides a savings of over 90% on storage for the operating system images alone.

## Practical applications

Using a controlled operating system image provides the following benefits:

**More secure and easier to manage.** Some enterprises require that data be secured by physically locking storage in a centralized location. In this scenario, servers access the data remotely, including the operating system image. With iSCSI Target Server, administrators can centrally manage the operating system boot images, and control which applications to use for the master image.

**Rapid deployment.** Because the master image is prepared by using Sysprep, when computers boot from the master image, they skip the file copying and installation phase that occurs during Windows Setup, and they go straight to the customization phase. In Microsoft internal testing, 256 computers were deployed in 34 minutes.

**Fast recovery.** Because the operating system images are hosted on the computer running iSCSI Target Server, if a disk-less client needs to be replaced, the new computer can point to the operating system image, and boot up immediately.

Note

Various vendors provide a storage area network (SAN) boot solution, which can be used by the iSCSI Target Server in Windows Server on commodity hardware.

## Hardware requirements

iSCSI Target Server does not require special hardware for functional verification. In data centers with large-scale deployments, the design should be validated against specific hardware. For reference, Microsoft internal testing indicated that a 256 computer deployment required 24x15k-RPM disks in a RAID 10 configuration for storage. A network bandwidth of 10 Gigabit is optimal. A general estimate is 60 iSCSI boot servers per 1 Gigabit network adapter.

A specialized network adapter is not required for this scenario, and a software boot loader can be used (such as iPXE open source boot firmware).

## Software requirements

iSCSI Target Server can be installed as part of the File and iSCSI Services role service in Server Manager.

Note

Booting Nano Server from iSCSI (either from the Windows iSCSI Target Server, or a 3rd party target implementation) is not supported.

## Additional References

- [iSCSI Target Server](iscsi-target-server)
- [iSCSI initiator cmdlets](/en-us/powershell/module/iscsi/)
- [iSCSI Target Server cmdlets](/en-us/powershell/module/iscsitarget/)